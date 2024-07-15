# C# Coding Conventions

## Table of Contents
1. [`var` Preferences](#var-preferences)
2. [Expression-bodied Members](#expression-bodied-members)
3. [Null-checking Preferences](#null-checking-preferences)
4. [Modifier Preferences](#modifier-preferences)
5. [Code block Preferences](#code-block-preferences) 


## var Preferences

### `csharp_style_var_for_built_in_types = true`

**Explanation:**

This setting specifies that the var keyword should be used for declaring variables of built-in types (e.g., int, string, bool). 
Using var can make the code more concise and easier to read by reducing redundancy.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        var number = 10;  // var keyword used instead of explicit type
        var text = "Hello, World!";  // var keyword used instead of explicit type
        var isTrue = true;  // var keyword used instead of explicit type
    }
}
```

### `csharp_style_var_elsewhere = true`

**Explanation:**

This setting specifies that the `var` keyword should be used for variable declarations elsewhere in the code. 
Using `var` can simplify the code and make it more concise, especially in contexts where the type is obvious from the context.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        var number = 10;  // var keyword used instead of explicit type
        var text = "Hello, World!";  // var keyword used instead of explicit type
    }
}
```

### `csharp_style_var_when_type_is_apparent = true`

**Explanation:**

This setting specifies that the var keyword should be used even when the type is apparent from the right-hand side of the assignment. 
This helps in maintaining consistency and reduces redundancy in the code.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        var names = new List<string>();  // var keyword used instead of explicit type
        var keyValuePairs = new Dictionary<int, string>();  // var keyword used instead of explicit type
    }
}
```

## Expression bodied Members

### Preferences
#### `csharp_style_expression_bodied_accessors = true`
#### `csharp_style_expression_bodied_constructors = false`
#### `csharp_style_expression_bodied_indexers = true`
#### `csharp_style_expression_bodied_lambdas = true`
#### `csharp_style_expression_bodied_local_functions = false`
#### `csharp_style_expression_bodied_methods = false`
#### `csharp_style_expression_bodied_operators = false`
#### `csharp_style_expression_bodied_properties = true`

**Explanation:**

- `csharp_style_expression_bodied_accessors = true` allows for expression-bodied accessors for the Number property.
- `csharp_style_expression_bodied_constructors = false` keeps the constructor in a regular block form.
- `csharp_style_expression_bodied_indexers = true` allows for an expression-bodied indexer.
- `csharp_style_expression_bodied_lambdas = true` allows for an expression-bodied lambda expression.
- `csharp_style_expression_bodied_local_functions = false` keeps the local function in a regular block form.
- `csharp_style_expression_bodied_methods = false` keeps the method in a regular block form.
- `csharp_style_expression_bodied_operators = false` keeps the operator in a regular block form.
- `csharp_style_expression_bodied_properties = true` allows for an expression-bodied property initializer.


**C# Code Example:**
```csharp
using System;
using System.Collections.Generic;

public class Example
{
    // Expression-bodied property
    public string Name { get; set; } = "Default Name";

    // Expression-bodied accessor
    private int _number;
    public int Number
    {
        get => _number;
        set => _number = value;
    }

    // Constructor (not expression-bodied)
    public Example(int number)
    {
        _number = number;
    }

    // Expression-bodied indexer
    private List<string> _items = new List<string>();
    public string this[int index] => _items[index];

    // Expression-bodied lambda
    Func<int, int> square = x => x * x;

    // Local function (not expression-bodied)
    public void PrintItems()
    {
        void PrintItem(string item)
        {
            Console.WriteLine(item);
        }

        foreach (var item in _items)
        {
            PrintItem(item);
        }
    }

    // Method (not expression-bodied)
    public void AddItem(string item)
    {
        _items.Add(item);
    }

    // Operator (not expression-bodied)
    public static Example operator +(Example a, Example b)
    {
        return new Example(a._number + b._number);
    }
}
```

## Pattern Matching Preferences

### Preferences
#### `csharp_style_pattern_matching_over_as_with_null_check = true`
#### `csharp_style_pattern_matching_over_is_with_cast_check = true`
#### `csharp_style_prefer_extended_property_pattern = true`
#### `csharp_style_prefer_not_pattern = true`
#### `csharp_style_prefer_pattern_matching = true`
#### `csharp_style_prefer_switch_expression = true`

**Explanation:**

Pattern matching in C# allows for concise and readable code when checking types and conditions. These preferences define the preferred ways to use pattern matching constructs.

**C# Code Example:**
```csharp
using System;

public class Example
{
    public static void Main()
    {
        object obj = "Hello";

        // Pattern matching with 'is' and 'as' expressions
        if (obj is string str)
        {
            Console.WriteLine($"Length of the string is {str.Length}");
        }

        // Pattern matching with 'switch' expression
        string result = obj switch
        {
            string s => $"String value: {s}",
            int i => $"Integer value: {i}",
            _ => "Unknown value"
        };

        Console.WriteLine(result);

        // Pattern matching with 'not' pattern
        if (!(obj is null))
        {
            Console.WriteLine($"Object is not null: {obj}");
        }

        // Pattern matching with extended property pattern
        if (obj is string { Length: > 5 } longString)
        {
            Console.WriteLine($"Long string with more than 5 characters: {longString}");
        }
    }
}
```

## Pattern Matching Preferences

### Preferences
- `csharp_style_pattern_matching_over_as_with_null_check = true`
- `csharp_style_pattern_matching_over_is_with_cast_check = true`
- `csharp_style_prefer_extended_property_pattern = true`
- `csharp_style_prefer_not_pattern = true`
- `csharp_style_prefer_pattern_matching = true`
- `csharp_style_prefer_switch_expression = true`

**Explanation:**

Pattern matching in C# allows for concise and readable code when checking types and conditions. 

**C# Code Example:**
```csharp
using System;

public class Example
{
    public static void Main()
    {
        object obj = "Hello";

        // Pattern matching with 'is' and 'as' expressions
        if (obj is string str)
        {
            Console.WriteLine($"Length of the string is {str.Length}");
        }

        // Pattern matching with 'switch' expression
        string result = obj switch
        {
            string s => $"String value: {s}",
            int i => $"Integer value: {i}",
            _ => "Unknown value"
        };

        Console.WriteLine(result);

        // Pattern matching with 'not' pattern
        if (!(obj is null))
        {
            Console.WriteLine($"Object is not null: {obj}");
        }

        // Pattern matching with extended property pattern
        if (obj is string { Length: > 5 } longString)
        {
            Console.WriteLine($"Long string with more than 5 characters: {longString}");
        }
    }
}
```

In the example above:

- `csharp_style_pattern_matching_over_as_with_null_check = true` promotes pattern matching over `as` with null check (`obj is string str` instead `of obj as string`)
- `csharp_style_pattern_matching_over_is_with_cast_check = true` promotes pattern matching over `is` with cast check (`obj is string { Length: > 5 } longString`).
- `csharp_style_prefer_extended_property_pattern = true` prefers the use of extended property patterns (string { Length: > 5 } longString).
- `csharp_style_prefer_not_pattern = true` prefers the use of the not pattern (`!(obj is null)`).
- `csharp_style_prefer_pattern_matching = true` promotes the use of pattern matching constructs in general.
- `csharp_style_prefer_switch_expression = true` prefers the use of switch expressions for pattern matching.

These settings ensure that pattern matching is used effectively and consistently throughout the codebase, improving readability and maintainability where type checks and conditionals are necessary.

## Null checking Preferences

### `csharp_style_conditional_delegate_call = true`

**Explanation:**

This setting promotes the use of conditional delegate invocation to safely invoke delegates that might be null. It ensures that delegate calls are only made when the delegate instance is not null, thereby avoiding potential `NullReferenceException` errors.

**C# Code Example:**
```csharp
using System;

public class Example
{
    public Action<int> Callback { get; set; }

    public void InvokeCallback(int value)
    {
        // Conditional delegate invocation
        Callback?.Invoke(value);
    }
}
```

## Modifier Preferences

### `csharp_prefer_static_local_function = true`

**Explanation:**

This preference encourages the use of static local functions where possible. Static local functions improve performance by avoiding unnecessary allocations and can enhance readability by making the intention of the function clear.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        // Static local function
        static void LocalFunction()
        {
            Console.WriteLine("Static local function");
        }

        LocalFunction(); // Call the static local function
    }
}
```

## Modifier Preferences

### `csharp_preferred_modifier_order = public,private,protected,internal,file,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,required,volatile,async`

**Explanation:**

This preference defines the preferred order of modifiers for members in C# code. 
Following a consistent order improves code readability and maintainability by making it easier to locate and understand member accessibility, behavior, and other characteristics.

**C# Code Example:**
```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,file,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,required,volatile,async
public class Example
{
    private static readonly int _daysInYear = 365;
}
```

## Modifier Preferences

### `csharp_style_prefer_readonly_struct = true`

**Explanation:**

This preference promotes the use of readonly for structs where appropriate. 
Using readonly structs ensures that their state cannot be modified after initialization, enhancing code safety and immutability.

**C# Code Example:**
```csharp
public readonly struct Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
}
```

### `csharp_style_prefer_readonly_struct_member = true`

**Explanation:**

This preference encourages using readonly for struct members where possible. 
Marking struct members as readonly ensures they cannot be modified after the struct is initialized, promoting immutability and preventing unintentional changes.

**C# Code Example:**
```csharp
public struct Vector
{
    public readonly int X;
    public readonly int Y;

    public Vector(int x, int y)
    {
        X = x;
        Y = y;
    }
}
```

## Code block Preferences

### `csharp_prefer_braces = true`

**Explanation:**

This preference enforces the use of braces `{}` for all control blocks, even if they contain only a single statement. 
Using braces improves readability and reduces the likelihood of errors during code modification.

**C# Code Example:**
```csharp
public class Example
{
    public void Method(bool condition)
    {
        // Using braces even for single statements
        if (condition)
        {
            Console.WriteLine("Condition is true");
        }
        else
        {
            Console.WriteLine("Condition is false");
        }
    }
}
```

### `csharp_prefer_simple_using_statement = true`

**Explanation:**

This preference encourages the use of the simplified using statement introduced in C# 8.0. 
The simplified using statement reduces indentation and improves code readability.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        using var resource = new Resource(); // Simplified using statement
        resource.DoWork();
    }
}

public class Resource : IDisposable
{
    public void DoWork() => Console.WriteLine("Working...");
    public void Dispose() => Console.WriteLine("Disposed");
}
```

### `csharp_style_namespace_declarations = file_scoped`

**Explanation**:

This preference encourages the use of file-scoped namespace declarations introduced in C# 10.0. 
File-scoped namespaces reduce indentation and make the overall structure of the file cleaner.

**C# Code Example:**
```csharp
namespace ExampleNamespace;

public class Example
{
    public void Method()
    {
        Console.WriteLine("File-scoped namespace declaration");
    }
}
```

### `csharp_style_prefer_method_group_conversion = true`

**Explanation**:

This preference promotes the use of method group conversions instead of lambda expressions where applicable. 
Method group conversions are more concise and can improve readability.

**C# Code Example:**
```csharp
bool IsEven(int x) => x % 2 == 0;

// Code with violations.
_ = new[] { 1, 2, 3 }.Where(n => IsEven(n));

// Fixed code.
_ = new[] { 1, 2, 3 }.Where(IsEven);
```

### `csharp_style_prefer_primary_constructors = true`

**Explanation**:

This preference encourages the use of primary constructors introduced in C# 12.0. 
Primary constructors simplify class definitions by combining constructor parameters with property declarations.

**C# Code Example:**
```csharp
public class Person(string name, int age)
{
    public string Name { get; } = name;
    public int Age { get; } = age;

    public void Print() => Console.WriteLine($"{Name}, {Age}");
}

// Usage
var person = new Person("Alice", 30);
```

### `csharp_style_prefer_top_level_statements = true`

**Explanation**:

This preference promotes the use of top-level statements, simplifying the entry point for applications. 
Top-level statements reduce boilerplate code and make the Main method more concise.

**C# Code Example:**
```csharp
// Code with violations.
internal class Program
{
    private static void Main(string[] args)
    {
        Console.WriteLine("Hello world.");
    }
}

// Fixed code.
Console.WriteLine("Hello world.");
```