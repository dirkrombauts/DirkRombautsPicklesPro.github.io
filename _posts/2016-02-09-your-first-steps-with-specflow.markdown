---
published: true
title: Your First Steps with SpecFlow
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, FirstSteps]
---
In this post, I will walk you through the steps you need to take to get your first [SpecFlow](http://www.specflow.org/) scenario up and running.

## Visual Studio

You will need a version of Visual Studio that can load plug-ins. Most versions can, it is mainly the Express editions of older Visual Studio versions that are unable to do that. If you do not have Visual Studio yet, then your best bet is the free [Community Edition of Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx).

## SpecFlow

Next you need to install the SpecFlow plug-in in Visual Studio.

1. Start Visual Studio if it is not already running.
2. In the `Tools` menu, click on `Extensions and Updates ...`.  
   ![Start Extensions Manager](/img/2016-02-09_StartExtentionsManager.png)
3. Expand the `Online` node on the left hand side, and click on the `Visual Studio Gallery` node.  
   ![Open the Visual Studio Gallery]("/img/2016-02-09_OpenTheVisualStudioGallery.png")
4. Search for `SpecFlow` in the search box in the top right corner, then click on the `Download` button for SpecFlow's entry in the search results.  
   ![Search for the SpecFlow Plug-in]("/img/2016-02-09_SearchForTheSpecFlowPlugin.png")
5. When the installer has finished downloading, click on the `Install` button in the `Download and Install` window. A web page will open with some advice on how to get started with SpecFlow. Feel free to read it or close it.
6. Click on the `Restart Now` button to finish the installation. Visual Studio will restart.

## Set up a Project

Now we will set up a Visual Studio solution and project, and add references to SpecFlow and to a unit-testing framework.

1. Start a new project by expanding the `File` menu, navigating to `New` and clicking on `Project ...`. Alternatively you can simply press `Ctrl+Shift+N`.
2. In the `New Project` window
    1. Expand the `Installed` node in the tree on the left hand side, then `Visual C#`, then `Windows`, then `Classic Desktop`.
    2. Click on the entry for `Class Library` in the list in the middle pane.
    3. Provide a name in the `Name` textbox near the bottom, for example `FirstStepsWithSpecFlow`.
    4. Click on the `OK` button in the bottom right corner.      
    ![Create New Project]("/img/2016-02-09_CreateNewProject.png")
3. Visual Studio provides a class named `Class1`. Delete it by right-clicking its file in the Solution Explorer and clicking `Delete`. Click on the `OK` button to confirm.
4. Add a reference to SpecFlow and [nUnit](http://www.nunit.org/), a unit-testing framework:
    1. Right-click on the project (named `FirstStepsWithSpecFlow`) in Solution Explorer and click on `Manage NuGet Packages ...`.
    2. In the `NuGet Package Manager` window, click on `Browse` and search for `SpecFlow.NUnit`.
    3. Click on the entry for `SpecFlow.NUnit` in the result list
    4. Click on the `Install` button on the right hand side.  
    ![Add NuGet Packages]("/img/2016-02-09_AddNuGetPackages.png")
    5. Close the `NuGet Package Manager` window.

## Add a Feature File

We will now add the first `.feature` file: that is the kind of file that contains the scenarios that describe the expected behavior of your software.

1. Right-click on the project (named `FirstStepsWithSpecFlow`) in Solution Explorer and click on `Add`, then on `New Item...`.
2. In the `Add New Item` window
    1. Expand the `Installed` node in the tree on the left hand side, then `Visual C#`.
    2. In the list in the middle pane, scroll until `SpecFlow Feature File` is visible. It should be near the top.
    3. Provide a name for the feature file near the bottom.
    4. Click on the `Add` button near the bottom right corner.     

![Add Feature File]("/img/2016-02-AddFeatureFile.png")

The `.feature` opens, and you will see a sample scenario (`Add Two Numbers`). 

We can now execute the specification for the first time. In the `Test` menu, point to `Run` and then click on `All Tests`. Alternatively, you can press `Ctrl+R,A`. Open the `Test Explorer` tool window by opening the `Test` menu, pointing to `Windows` and clicking on `Test Explorer`. You will see a list with a node for the sample scenario.

![Test Explorer: First Run]("/img/2016-02-09_TestExplorerFirstRun.png")

Note: if the `Test Explorer` is empty, you need to install the `NUnit3 Test Adapter 3.0` plug-in in the same way you installed the `SpecFlow` plug-in earlier.

Select the `Add Two Numbers` scenario. You will see that the test was not run because no matching step definition was found for one or more steps. We will now provide those step definitions. 

## Add a Step Definition File

Add a step definition file in much the same way as you added a `.feature` file, except that you select the `SpecFlow Step Definition` entry.

![Add Step Definitions]("/img/2016-02-09_AddStepDefinitions.png")

Execute the specification again. The Test Explorer tool window now has a different message: one or more step definitions are not implemented yet. SpecFlow found our step definitions and used them, but of course there is nothing meaningful inside them yet.

![Test Explorer: Second Run]("/img/2016-02-09_TestExplorerSecondRun.png")

Replace the code for the `StepDefinition1` class with this version:


```
    [Binding]
    public sealed class StepDefinition1
    {
        private readonly Calculator calculator;

        public StepDefinition1(Calculator calculator)
        {
            this.calculator = calculator;
        }

        [Given("I have entered (.*) into the calculator")]
        public void GivenIHaveEnteredSomethingIntoTheCalculator(int number)
        {
            this.calculator.Enter(number);
        }

        [When("I press add")]
        public void WhenIPressAdd()
        {
            this.calculator.Add();
        }

        [Then("the result should be (.*) on the screen")]
        public void ThenTheResultShouldBe(int expectedResult)
        {
            int actualResult = this.calculator.Display;

            Assert.That(actualResult, Is.EqualTo(expectedResult));
        }
    }
```

This will

- Give SpecFlow a calculator object to use.
- Tell SpecFlow to call the `Enter` method on the calculator whenever the scenario says to enter a value.
- Tell SpecFlow to call the `Add` method on the calculator whenever the scenario says to press add.
- Tell SpecFlow to take the value from the `Display` property and compare it against the expected value whenever the scenario says the display should have a certain value.

## Implement the Business Logic

After setting up the project, adding references, writing a scenario and preparing binding methods, it is now time to implement the business logic.

First create a new class called `Calculator` and replace it with this code:

```
    public class Calculator
    {
        public int Display { get; set; }

        private List<int> Values { get; } = new List<int>();

        public void Add()
        {
            throw new NotImplementedException();
        }

        public void Enter(int number)
        {
            this.Values.Add(number);
        }
    }
```

Execute the specification again. The Test Explorer tool window now has yet another different message: the method or operation is not implemented. SpecFlow found our step definitions and our calculator object, but the `Add` method is not implemented yet.

![Test Explorer: Third Run]("/img/2016-02-09_TestExplorerThirdRun.png")


Now replace the `Add` method in `Calculator` with this version:

```
        public void Add()
        {
            this.Display = this.Values[0] + this.Values[1];
        }
```

Execute the specification one more time. Now all is green.

![Test Explorer: Fourth Run]("/img/2016-02-09_TestExplorerFourthRun.png")

## Summary and Next Steps

Congratulations! You worked your way through this post and have implemented the business logic for the `Add Two Numbers` scenario. Your SpecFlow workflow should always follow this pattern:

1. Define a scenario.
2. Provide step definitions that call the business logic
3. Implement the business logic.

In this post I showed you how to get started with SpecFlow from scratch. We discussed the Visual Studio version you need, how to install the SpecFlow plug-in, how to create a new project and how to add references to SpecFlow and nUnit. I then showed how to add a `.feature` file, how to set up step bindings, and provided a very basic implementation of a calculator.

The next steps are two-fold: first, the calculator is very limited in its functionality. We can add more scenarios to describe subtraction, multiplication, division and other mathematical operations. Secondly, the implementation of the calculator is rather shaky: it assumes there are always at least two values in the `Values` list. So both the spectrum of functionality and the implementation of the existing functionality need to be improved.

You now have the necessary knowledge for the first of those steps, and your C# software development knowledge will help you with the second step.
