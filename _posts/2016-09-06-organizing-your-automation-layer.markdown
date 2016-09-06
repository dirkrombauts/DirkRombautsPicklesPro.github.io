---
published: true
title: Organizing Your Automation Layer
layout: post
tags: [SpecFlow, Tips, AutomationLayer]
---
When you start to use SpecFlow on your project, it's easy to extend the automation layer. It is easy to add binding methods to your binding classes, and SpecFlow offers some support for quickly creating skeletons of needed binding methods. This can quickly lead to a big pile of binding methods, which leads to duplication which leads to suffering. In this article, I give you some tips on how to organize your automation layer so that you avoid that pitfall.

<!--more-->

## The Big Pile

So you are using SpecFlow on your project. During the Three Amigos sessions you come up with new scenarios, and sometimes you need a new sentence. "No problem, I'll just add another binding method to my StepDefinitions class" you think. After a while you notice that the StepDefinitions.cs class is getting large. You notice some other problems as well.

Many of those methods have nothing to do with each others. Some of them deal with domain entities and their repositories, but some deal with external services and their gateways. Well-designed classes are [cohesive](https://www.wikiwand.com/en/Cohesion_(computer_science)): they contain methods and properties that are related to each other. So our step definitions class is not cohesive.

The methods in our step definition class that do deal with related entities, tend to contain a lot of similar code: they access a repository, they query, they create, and they compare. The code should not [repeat itself](https://www.wikiwand.com/en/Don't_repeat_yourself), should express one thing exactly once. Our step definition methods likely contain a lot of similar code, so they are not "dry".

The step definitions class is a small example of what I'm talking about. There are methods about books, and about payment. The methods about payment are similar but subtly different.

```c#
[Binding]
public class StepDefinitions
{
  [Given]
  public void GivenTheShopCarriesTheseBooks(IEnumerable<Book> books)
  {
	foreach(Book book in books)
    {
      BookDatabaseConnection connection = new BookDatabaseConnection();
      connection.Books.Insert(book.Title, book.Author, book.Isbn);
      connection.Books.Commit();
    }
  }

  [When]
  public void WhenIPayAOneTimeAmount(decimal amount)
  {
    PaymentProxy proxy = new PaymentProxy();
    SendMoneyMessage message = new SendMoneyMessage(amount, false);
    proxy.Send(message);

  }
  
  [When]
  public void WhenIPayARecurringTimeAmount(decimal amount)
  {
    PaymentProxy proxy = new PaymentProxy();
    SendMoneyMessage message = new SendMoneyMessage(amount, true);
    proxy.Send(message);
  }
}
```

## Some Solutions

Let's tackle the second problem first, since the knowledge needed for that is not specific to SpecFlow. By refactoring your code, and by generally applying good software developing practices, you can lift the code of the automation layer to the same level of quality as your production code. In doing so, you will probably arrive at some driver classes: a driver for database operations, a driver for repositories, a driver for external dependencies.

```c#
[Binding]
public class StepDefinitions
{
  private readonly PaymentProvider paymentProvider;
  private readonly BookRepository bookRepository;

  public StepDefinitions(PaymentProvider paymentProvider, BookRepository bookRepository)
  {
    this.paymentProvider = paymentProvider;
    this.bookRepository = bookRepository;
  }
  
  [Given]
  public void GivenTheShopCarriesTheseBooks(IEnumerable<Book> books)
  {
	foreach(Book book in books)
    {
      this.bookRepository.Create(book);
    }
  }
  
  [When]
  public void WhenIPayAOneTimeAmount(decimal amount)
  {
    this.paymentProvider.Pay(amount, false);
  }
  
  [When]
  public void WhenIPayARecurringTimeAmount(decimal amount)
  {
    this.paymentProvider.Pay(amount, true);
  }
}

public class PaymentProvider
{
  public void Pay(decimal amount, bool isRecurring)
  {
    PaymentProxy proxy = new PaymentProxy();
    SendMoneyMessage message = new SendMoneyMessage(amount, isRecurring);
    proxy.Send(message);
  }
}

public class BookRepository
{
  public void Create(Book book)
  {
    BookDatabaseConnection connection = new BookDatabaseConnection();
    connection.Books.Insert(book.Title, book.Author, book.Isbn);
    connection.Books.Commit();
  }
}
```

However, we now created another problem: now that we have driver objects, we have to manage the instances. We can do it ourself by creating instances of the driver objects in the constructor of the StepDefinitions class. Or we can use SpecFlow's built-in dependency management for this purpose (Gáspár Nagy recently wrote about [dependency injection in SpecFlow](http://gasparnagy.com/2016/08/specflow-tips-customizing-dependency-injection-with-autofac/)). But now we have driver objects that are used for some methods, but not for others. So we solved the second problem but we made our first problem worse.

We can solve the first problem by splitting the StepDefinition class in multiple classes. Each of those step definition classes is centered on one (or more) driver objects, and contains only methods that use all of the driver objects. That way, we arrive at a number of classes that are highly cohesive.

```c#
[Binding]
public class PaymentBindings
{
  private readonly PaymentProvider paymentProvider;
  
  public PaymentBindings(PaymentProvider paymentProvider)
  {
    this.paymentProvider = paymentProvider;
  }
  
  [When]
  public void WhenIPayAOneTimeAmount(decimal amount)
  {
    this.paymentProvider.Pay(amount, false);
  }
  
  [When]
  public void WhenIPayARecurringTimeAmount(decimal amount)
  {
    this.paymentProvider.Pay(amount, true);
  }

}

public class PaymentProvider
{
  public void Pay(decimal amount, bool isRecurring)
  {
    PaymentProxy proxy = new PaymentProxy();
    SendMoneyMessage message = new SendMoneyMessage(amount, isRecurring);
    proxy.Send(message);
  }
}

[Binding]
public void BookBindings
{
  private readonly BookRepository bookRepository;
  
  public BookBindings(BookRepository bookRepository)
  {
    this.bookRepository = bookRepository;
  }
  
  [Given]
  public void GivenTheShopCarriesTheseBooks(IEnumerable<Book> books)
  {
	foreach(Book book in books)
    {
      this.bookRepository.Create(book);
    }
  }
}

public class BookRepository
{
  public void Create(Book book)
  {
    BookDatabaseConnection connection = new BookDatabaseConnection();
    connection.Books.Insert(book.Title, book.Author, book.Isbn);
    connection.Books.Commit();
  }
}
```

## Conclusion

The important mindset is that automation layer code is just as important as production code. Automation layer code deserves just as much tender love and care as production code. This is especially important if you apply outside-in development, because then your automation layer code will help you define the production code's API. If your automation layer code is badly factored, then likely your production code will be as well.

Using well-known good software development practices, we ensure that the code doesn't repeat itself. We will likely use driver objects. We can then make the step definition classes more cohesive by organizing them around those driver objects.