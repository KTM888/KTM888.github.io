---
title: Learning C# Scripting for Unity
date: 2019-07-18T10:51:56.024Z
featured: true
link: miguel-lopez.me
image: img/csharp_unity.png
description: This is a collection of tutorials which are now all populated into
  a nicely formatted web page.
tags:
  - C#
  - Unity
  - Programming
  - Tutorials
fact: ""
weight: 10
sitemap:
  weight: 0.5
---


# Learning C# scripting for Unity

[[Behavior Components]]
[[Variables and Functions]]
[[Conventions and Syntax]]
[[IF Statements|C#IFStatements]]
[[Loops]]
[[Scope and Access Modifiers]]
[[Awake and Start Functions]]

## Behaviour Components

### Changing Colors by pressing Keys

```cs
using UnityEngine;
using System.Collections;

public class ExampleBehaviourScript : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.R))
        {
            GetComponent<Renderer> ().material.color = Color.red;
        }
        if (Input.GetKeyDown(KeyCode.G))
        {
            GetComponent<Renderer>().material.color = Color.green;
        }
        if (Input.GetKeyDown(KeyCode.B))
        {
            GetComponent<Renderer>().material.color = Color.blue;
        }
    }
}
```

- In example the `public class` defines a component that can be use globally throughout the code.
- `input.GetKeyDown(KeyCide.R)` defines that when a user press the R key an action will be triggered.
- `GetComponenet<Renderer>().material.color = Color.red;` is the action that will be triggered when the user presses the R key, c# knows this because its inside the double brackets "{}" meaning that is part of the statement above.

## Variables and Functions

```cs
using UnityEngine;
using System.Collections;

public class VariablesAndFunctions : MonoBehaviour
{
    int myInt = 5;


    void Start ()
    {
        myInt = MultiplyByTwo(myInt);
        Debug.Log (myInt);
    }


    int MultiplyByTwo (int number)
    {
        int result;
        result = number * 2;
        return result;
    }
}
```

- In c# we first declare the type of a variable an then we assign the name to it and then the value, e.g `int myInt = 5`.
- In c# you will also have to end each statement with a semi-colon ';'.
- The `void Start ()` means that when the program runs (object enters the scene) do this.
- In this case we do some calculation can `Debug.Log(myInt)` which means it will log "print" the calculation into the console.
- A function in c# is similar to a python `def` function. The differences are that the actions are inside the double brackets '{}'. In c# you will first have to declare what you are going to store in the function in this case will be an `int` integer. Then we need to name the function which will be `MultiplyByTwo`.
- In c# a function can have parameters just like in python, however you will have to specify the parameter's value first and then name it like so `int number`, the `int` is the parameter's value type and the `number` is the parameter's name.
- In the example above, the function will create a variable called `result` which will store an `int` integer, which will be the parameter which is named `number` and multiply that by 2.
- In c# the `return` command is equal to `print` function in python in which will print the output of the statement to the console which in this case will be the result of the actual result.

## Conventions and Syntax

```cs
using UnityEngine;
using System.Collections;

public class BasicSyntax : MonoBehaviour
{
    void Start ()
    {
        Debug.Log(transform.position.x);

        if(transform.position.y <= 5f)
        {
            Debug.Log ("I'm about to hit the ground!");
        }
    }
}
```

## If Statements

```cs
using UnityEngine;
using System.Collections;

public class IfStatements : MonoBehaviour
{
    float coffeeTemperature = 85.0f;
    float hotLimitTemperature = 70.0f;
    float coldLimitTemperature = 40.0f;


    void Update ()
    {
        if(Input.GetKeyDown(KeyCode.Space))
            TemperatureTest();

        coffeeTemperature -= Time.deltaTime * 5f;
    }


    void TemperatureTest ()
    {
        // If the coffee's temperature is greater than the hottest drinking temperature...
        if(coffeeTemperature > hotLimitTemperature)
        {
            // ... do this.
            print("Coffee is too hot.");
        }
        // If it isn't, but the coffee temperature is less than the coldest drinking temperature...
        else if(coffeeTemperature < coldLimitTemperature)
        {
            // ... do this.
            print("Coffee is too cold.");
        }
        // If it is neither of those then...
        else
        {
            // ... do this.
            print("Coffee is just right.");
        }
    }
}
```

- In c#, you can use if statements similar to python, the only difference is that instead of `elif` you use else if as the equivalent.
- Then all of the c# syntax is applied the same.

- In c# we use the dot operators (full stop) to drill down into elements inside compound item (something that contains many elements), e.g `Debug.log()`.
- The transform contains position, rotation and scale (x, y, z).
- The semi-colon ';' is use to terminate statements, however not all statements will end with a semi-colon, such as classes, if statements or functions because they will be followed by double brackets '{}', but any statements inside those brackets will end with a semi-colon.
- Indentation unlike python does not have a meaning, but is essential practice for readability and stop mistakes, you should indent every time you start or end an statement.
- Single line comments are done by using the double slash '//',
- Double line comments start with a '/\*' and finish using the opposite '\*/'

![[Pasted image 20210127195748.png]]

## Loops

### For Loops

```cs
using UnityEngine;
using System.Collections;

public class ForLoop : MonoBehaviour
{
    int numEnemies = 3;


    void Start ()
    {
        for(int i = 0; i < numEnemies; i++)
        {
            Debug.Log("Creating enemy number: " + i);
        }
    }
}
```

- In c# the for loop works by controlling a number of iterations.
- Meaning, it will start by checking conditions in the loop, and continue by executing the instructions that are in within the body '{}'.
- In this example the for loop has three arguments.
- The first part of the loop is called the iteration (count through the iterations of the loop) meaning the introduction of a variable.
- The second argument is the condition, which will tell the loop to run if that condition is met (True)
- the `i++` means that the variable `i` will be incremented by one each time the loops runs.

### Do While Loops

```cs
using UnityEngine;
using System.Collections;

public class DoWhileLoop : MonoBehaviour
{
    void Start()
    {
        bool shouldContinue = false;

        do
        {
            print ("Hello World");

        }while(shouldContinue == true);
    }
}
```

- The difference between `while` and `DoWhile` loops is that in a while loop the condition is checked before the loop body, whereas the `DoWhile` test the condition at the end of the body, this means that the body of the `DoWhile` is guaranteed to run at least once.
- In this example, we have a boolean variable which is set to `false`.
- The Syntax of the `do while` loop starts with a `do` followed by double braces `{}` (body), and ends with the keyword `while` which inside contains the condition.
- Finally at the end of the condition you should end the `while` with a semi-colon `;`

### While Loops

```cs
using UnityEngine;
using System.Collections;

public class WhileLoop : MonoBehaviour
{
    int cupsInTheSink = 4;


    void Start ()
    {
        while(cupsInTheSink > 0)
        {
            Debug.Log ("I've washed a cup!");
            cupsInTheSink--;
        }
    }
}
```

- While loops check the condition before running the body of the loop.
- we start by declaring the keyword `while`, followed by the condition inside the double parenthesis `()`.
- Then we write the actions that we want the loop o perform by using double braces `{}`.
- the `while` loop does not need the semi-colon `;` at the end of the loop.

### ForEach loop

```cs
using UnityEngine;
using System.Collections;

public class ForeachLoop : MonoBehaviour
{
    void Start ()
    {
        string[] strings = new string[3];

        strings[0] = "First string";
        strings[1] = "Second string";
        strings[2] = "Third string";

        foreach(string item in strings)
        {
            print (item);
        }
    }
}
```

re a datatype when declaring a variable, its purpose is to determine where that variable or function can be seen from.

- Common practice will be to declare `public` variables or function when there is a specif need for it (e.g using it on another script), otherwise it should be `private`.
- If you do not define the type of scope before the datatype C# will automatically define that as a `private` variable or function.
- By declaring a variable as public means that the variable will be shown and editable on the component in the inspector.
  ![[Pasted image 20210204181603.png]]
- You can add a default value to that variable in the script, but if changed in the inspector that will overwrite the default value, the only way we can overwrite the inspector's value is by placing that variable inside a function.
  - ![[Pasted image 20210204182005.png]]

#### Another Class

```cs
using UnityEngine;
using System.Collections;

public class AnotherClass
{
    public int apples;
    public int bananas;


    private int stapler;
    private int sellotape;


    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }


    private void OfficeSort (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Office Supplies total: " + answer);
    }
}
```

- In this script, because we previously set the variable as public we can access them.
- The `private` and `public` determination is also applied to functions, for example, in this script we have two functions and we can only access the `public` function from another script.

  - ![[Pasted image 20210204182538.png]]

- This is a new type of loop similar to the for loop, but its more simplistic.
- It is design to help you with collections of data (e.g array).
- In this example, we start by declaring the loop `foreach`, followed by the variable stored in the collection, in this case will be `item`, notice we can use the `string` keyword to inform the compiler what is stored on the variable, however we can also use `var` which the compiler will automatically define it.
- then we use the `in` keyword followed by the collection name `string` to create the condition, in this case the loop will check the items inside the string collection, and then print it as declared in the body section of the loop.
- The `foreach` loop does not require a semi-colon at the end.

## Scope and Access Modifiers

```cs
using UnityEngine;
using System.Collections;

public class ScopeAndAccessModifiers : MonoBehaviour
{
    public int alpha = 5;


    private int beta = 0;
    private int gamma = 5;


    private AnotherClass myOtherClass;


    void Start ()
    {
        alpha = 29;

        myOtherClass = new AnotherClass();
        myOtherClass.FruitMachine(alpha, myOtherClass.apples);
    }
```

- The scope of a variable is the area in code in which the variable can be use in.
- The access modifier is a keyword that is place before a datatype when declaring a variable, its purpose is to determine where that variable or function can be seen from.
- Common practice will be to declare `public` variables or function when there is a specif need for it (e.g using it on another script), otherwise it should be `private`.
- If you do not define the type of scope before the datatype C# will automatically define that as a `private` variable or function.
- By declaring a variable as public means that the variable will be shown and editable on the component in the inspector.
  ![[Pasted image 20210204181603.png]]
- You can add a default value to that variable in the script, but if changed in the inspector that will overwrite the default value, the only way we can overwrite the inspector's value is by placing that variable inside a function.
  - ![[Pasted image 20210204182005.png]]

#### Another Class

```cs
using UnityEngine;
using System.Collections;

public class AnotherClass
{
    public int apples;
    public int bananas;


    private int stapler;
    private int sellotape;


    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }


    private void OfficeSort (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Office Supplies total: " + answer);
    }
}
```

- In this script, because we previously set the variable as public we can access them.
- The `private` and `public` determination is also applied to functions, for example, in this script we have two functions and we can only access the `public` function from another script.
  - ![[Pasted image 20210204182538.png]]

## Awake and Start

```cs
using UnityEngine;
using System.Collections;

public class AwakeAndStart : MonoBehaviour
{
    void Awake ()
    {
        Debug.Log("Awake called.");
    }


    void Start ()
    {
        Debug.Log("Start called.");
    }
}
```

- The `awake` and `start` are two functions that are called automatically when a script is loaded.
- The `awake` function is called first, even if the script component is not enabled. It is used to set references between scripts and initialization.
- The `start` function is called only if the script component is enabled, this means that you can use the `start` function for anything you want to occur when the script component is enabled.
- The start can be useful to delay the initialization of the script or `awake` function.
- In this example, we can use the `awake` function to assign the `enemy` ammo and by using the `start` we can give the `enemy` the ability to shoot at a defined time when the script component is enabled.
- NOTE: the `awake` and `start` can only be called one in the lifetime of the script attached to an object.

# Learning C# scripting for Unity

[[Behavior Components]]
[[Variables and Functions]]
[[Conventions and Syntax]]
[[IF Statements|C#IFStatements]]
[[Loops]]
[[Scope and Access Modifiers]]
[[Awake and Start Functions]]

## Behaviour Components

### Changing Colors by pressing Keys

```cs
using UnityEngine;
using System.Collections;

public class ExampleBehaviourScript : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.R))
        {
            GetComponent<Renderer> ().material.color = Color.red;
        }
        if (Input.GetKeyDown(KeyCode.G))
        {
            GetComponent<Renderer>().material.color = Color.green;
        }
        if (Input.GetKeyDown(KeyCode.B))
        {
            GetComponent<Renderer>().material.color = Color.blue;
        }
    }
}
```

- In example the `public class` defines a component that can be use globally throughout the code.
- `input.GetKeyDown(KeyCide.R)` defines that when a user press the R key an action will be triggered.
- `GetComponenet<Renderer>().material.color = Color.red;` is the action that will be triggered when the user presses the R key, c# knows this because its inside the double brackets "{}" meaning that is part of the statement above.

## Variables and Functions

```cs
using UnityEngine;
using System.Collections;

public class VariablesAndFunctions : MonoBehaviour
{
    int myInt = 5;


    void Start ()
    {
        myInt = MultiplyByTwo(myInt);
        Debug.Log (myInt);
    }


    int MultiplyByTwo (int number)
    {
        int result;
        result = number * 2;
        return result;
    }
}
```

- In c# we first declare the type of a variable an then we assign the name to it and then the value, e.g `int myInt = 5`.
- In c# you will also have to end each statement with a semi-colon ';'.
- The `void Start ()` means that when the program runs (object enters the scene) do this.
- In this case we do some calculation can `Debug.Log(myInt)` which means it will log "print" the calculation into the console.
- A function in c# is similar to a python `def` function. The differences are that the actions are inside the double brackets '{}'. In c# you will first have to declare what you are going to store in the function in this case will be an `int` integer. Then we need to name the function which will be `MultiplyByTwo`.
- In c# a function can have parameters just like in python, however you will have to specify the parameter's value first and then name it like so `int number`, the `int` is the parameter's value type and the `number` is the parameter's name.
- In the example above, the function will create a variable called `result` which will store an `int` integer, which will be the parameter which is named `number` and multiply that by 2.
- In c# the `return` command is equal to `print` function in python in which will print the output of the statement to the console which in this case will be the result of the actual result.

## Conventions and Syntax

```cs
using UnityEngine;
using System.Collections;

public class BasicSyntax : MonoBehaviour
{
    void Start ()
    {
        Debug.Log(transform.position.x);

        if(transform.position.y <= 5f)
        {
            Debug.Log ("I'm about to hit the ground!");
        }
    }
}
```

## If Statements

```cs
using UnityEngine;
using System.Collections;

public class IfStatements : MonoBehaviour
{
    float coffeeTemperature = 85.0f;
    float hotLimitTemperature = 70.0f;
    float coldLimitTemperature = 40.0f;


    void Update ()
    {
        if(Input.GetKeyDown(KeyCode.Space))
            TemperatureTest();

        coffeeTemperature -= Time.deltaTime * 5f;
    }


    void TemperatureTest ()
    {
        // If the coffee's temperature is greater than the hottest drinking temperature...
        if(coffeeTemperature > hotLimitTemperature)
        {
            // ... do this.
            print("Coffee is too hot.");
        }
        // If it isn't, but the coffee temperature is less than the coldest drinking temperature...
        else if(coffeeTemperature < coldLimitTemperature)
        {
            // ... do this.
            print("Coffee is too cold.");
        }
        // If it is neither of those then...
        else
        {
            // ... do this.
            print("Coffee is just right.");
        }
    }
}
```

- In c#, you can use if statements similar to python, the only difference is that instead of `elif` you use else if as the equivalent.
- Then all of the c# syntax is applied the same.

- In c# we use the dot operators (full stop) to drill down into elements inside compound item (something that contains many elements), e.g `Debug.log()`.
- The transform contains position, rotation and scale (x, y, z).
- The semi-colon ';' is use to terminate statements, however not all statements will end with a semi-colon, such as classes, if statements or functions because they will be followed by double brackets '{}', but any statements inside those brackets will end with a semi-colon.
- Indentation unlike python does not have a meaning, but is essential practice for readability and stop mistakes, you should indent every time you start or end an statement.
- Single line comments are done by using the double slash '//',
- Double line comments start with a '/\*' and finish using the opposite '\*/'

![[Pasted image 20210127195748.png]]

## Loops

### For Loops

```cs
using UnityEngine;
using System.Collections;

public class ForLoop : MonoBehaviour
{
    int numEnemies = 3;


    void Start ()
    {
        for(int i = 0; i < numEnemies; i++)
        {
            Debug.Log("Creating enemy number: " + i);
        }
    }
}
```

- In c# the for loop works by controlling a number of iterations.
- Meaning, it will start by checking conditions in the loop, and continue by executing the instructions that are in within the body '{}'.
- In this example the for loop has three arguments.
- The first part of the loop is called the iteration (count through the iterations of the loop) meaning the introduction of a variable.
- The second argument is the condition, which will tell the loop to run if that condition is met (True)
- the `i++` means that the variable `i` will be incremented by one each time the loops runs.

### Do While Loops

```cs
using UnityEngine;
using System.Collections;

public class DoWhileLoop : MonoBehaviour
{
    void Start()
    {
        bool shouldContinue = false;

        do
        {
            print ("Hello World");

        }while(shouldContinue == true);
    }
}
```

- The difference between `while` and `DoWhile` loops is that in a while loop the condition is checked before the loop body, whereas the `DoWhile` test the condition at the end of the body, this means that the body of the `DoWhile` is guaranteed to run at least once.
- In this example, we have a boolean variable which is set to `false`.
- The Syntax of the `do while` loop starts with a `do` followed by double braces `{}` (body), and ends with the keyword `while` which inside contains the condition.
- Finally at the end of the condition you should end the `while` with a semi-colon `;`

### While Loops

```cs
using UnityEngine;
using System.Collections;

public class WhileLoop : MonoBehaviour
{
    int cupsInTheSink = 4;


    void Start ()
    {
        while(cupsInTheSink > 0)
        {
            Debug.Log ("I've washed a cup!");
            cupsInTheSink--;
        }
    }
}
```

- While loops check the condition before running the body of the loop.
- we start by declaring the keyword `while`, followed by the condition inside the double parenthesis `()`.
- Then we write the actions that we want the loop o perform by using double braces `{}`.
- the `while` loop does not need the semi-colon `;` at the end of the loop.

### ForEach loop

```cs
using UnityEngine;
using System.Collections;

public class ForeachLoop : MonoBehaviour
{
    void Start ()
    {
        string[] strings = new string[3];

        strings[0] = "First string";
        strings[1] = "Second string";
        strings[2] = "Third string";

        foreach(string item in strings)
        {
            print (item);
        }
    }
}
```

re a datatype when declaring a variable, its purpose is to determine where that variable or function can be seen from.

- Common practice will be to declare `public` variables or function when there is a specif need for it (e.g using it on another script), otherwise it should be `private`.
- If you do not define the type of scope before the datatype C# will automatically define that as a `private` variable or function.
- By declaring a variable as public means that the variable will be shown and editable on the component in the inspector.
  ![[Pasted image 20210204181603.png]]
- You can add a default value to that variable in the script, but if changed in the inspector that will overwrite the default value, the only way we can overwrite the inspector's value is by placing that variable inside a function.
  - ![[Pasted image 20210204182005.png]]

#### Another Class

```cs
using UnityEngine;
using System.Collections;

public class AnotherClass
{
    public int apples;
    public int bananas;


    private int stapler;
    private int sellotape;


    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }


    private void OfficeSort (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Office Supplies total: " + answer);
    }
}
```

- In this script, because we previously set the variable as public we can access them.
- The `private` and `public` determination is also applied to functions, for example, in this script we have two functions and we can only access the `public` function from another script.

  - ![[Pasted image 20210204182538.png]]

- This is a new type of loop similar to the for loop, but its more simplistic.
- It is design to help you with collections of data (e.g array).
- In this example, we start by declaring the loop `foreach`, followed by the variable stored in the collection, in this case will be `item`, notice we can use the `string` keyword to inform the compiler what is stored on the variable, however we can also use `var` which the compiler will automatically define it.
- then we use the `in` keyword followed by the collection name `string` to create the condition, in this case the loop will check the items inside the string collection, and then print it as declared in the body section of the loop.
- The `foreach` loop does not require a semi-colon at the end.

## Scope and Access Modifiers

```cs
using UnityEngine;
using System.Collections;

public class ScopeAndAccessModifiers : MonoBehaviour
{
    public int alpha = 5;


    private int beta = 0;
    private int gamma = 5;


    private AnotherClass myOtherClass;


    void Start ()
    {
        alpha = 29;

        myOtherClass = new AnotherClass();
        myOtherClass.FruitMachine(alpha, myOtherClass.apples);
    }
```

- The scope of a variable is the area in code in which the variable can be use in.
- The access modifier is a keyword that is place before a datatype when declaring a variable, its purpose is to determine where that variable or function can be seen from.
- Common practice will be to declare `public` variables or function when there is a specif need for it (e.g using it on another script), otherwise it should be `private`.
- If you do not define the type of scope before the datatype C# will automatically define that as a `private` variable or function.
- By declaring a variable as public means that the variable will be shown and editable on the component in the inspector.
  ![[Pasted image 20210204181603.png]]
- You can add a default value to that variable in the script, but if changed in the inspector that will overwrite the default value, the only way we can overwrite the inspector's value is by placing that variable inside a function.
  - ![[Pasted image 20210204182005.png]]

#### Another Class

```cs
using UnityEngine;
using System.Collections;

public class AnotherClass
{
    public int apples;
    public int bananas;


    private int stapler;
    private int sellotape;


    public void FruitMachine (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Fruit total: " + answer);
    }


    private void OfficeSort (int a, int b)
    {
        int answer;
        answer = a + b;
        Debug.Log("Office Supplies total: " + answer);
    }
}
```

- In this script, because we previously set the variable as public we can access them.
- The `private` and `public` determination is also applied to functions, for example, in this script we have two functions and we can only access the `public` function from another script.
  - ![[Pasted image 20210204182538.png]]

## Awake and Start

```cs
using UnityEngine;
using System.Collections;

public class AwakeAndStart : MonoBehaviour
{
    void Awake ()
    {
        Debug.Log("Awake called.");
    }


    void Start ()
    {
        Debug.Log("Start called.");
    }
}
```

- The `awake` and `start` are two functions that are called automatically when a script is loaded.
- The `awake` function is called first, even if the script component is not enabled. It is used to set references between scripts and initialization.
- The `start` function is called only if the script component is enabled, this means that you can use the `start` function for anything you want to occur when the script component is enabled.
- The start can be useful to delay the initialization of the script or `awake` function.
- In this example, we can use the `awake` function to assign the `enemy` ammo and by using the `start` we can give the `enemy` the ability to shoot at a defined time when the script component is enabled.
- NOTE: the `awake` and `start` can only be called one in the lifetime of the script attached to an object.

