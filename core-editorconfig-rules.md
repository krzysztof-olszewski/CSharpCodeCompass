# Core .editorconfig rules

## Table of Contents
1. [Indentation and Spacing](#indentation-and-spacing)
2. [New Line Preferences](#new-line-preferences)
3. [Organize Usings](#organize-usings)
4. [`this.` Preferences](#this-preferences)
5. [Language Keywords vs BCL Types Preferences](#language-keywords-vs-bcl-types-preferences)
6. [Parentheses Preferences](#parentheses-preferences)
7. [Modifier Preferences](#modifier-preferences)
8. [Field Preferences](#field-preferences)
9. [Expression level preferences](#expression-level-preferences)
10. [Parameter Preferences](#parameter-preferences)
11. [Suppression Preferences](#suppression-preferences)
12. [New Line Preferences](#new-line-preferences)

## Indentation and Spacing

### `indent_size = 4`

**Explanation:**
This setting specifies that each indentation level should be equivalent to 4 spaces. 
This helps maintain consistent indentation across the codebase.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        if (true)
        {
            Console.WriteLine("Hello, world!");
        }
    }
}
```

### `tab_width = 4`

**Explanation:**

This setting specifies the width of a tab character. 
Although we are using spaces for indentation, 
this setting ensures that if tabs are used, they will be equivalent to 4 spaces.

## New Line Preferences

### `end_of_line = crlf (Windows-style)`

**Explanation:**

This setting enforces the use of CRLF (Carriage Return + Line Feed) for line endings. 
This is commonly used in Windows environments.

### `insert_final_newline = false`

**Explanation:**

This setting specifies that a newline character should not be inserted at the end of the file. 
This helps avoid unnecessary diffs when files are edited.

**C# Code Example:**
```csharp
public class Example
{
    public void Method()
    {
        Console.WriteLine("Hello, world!");
    }
}
// No newline at the end of this file.
```

## Organize Usings

### `dotnet_separate_import_directive_groups = false`

**Explanation:**
This setting specifies that using directives should not be separated into groups.

**C# Code Example:**
```csharp
using System; // No blank lines between using directives.
using System.Collections.Generic;

public class Example
{
    // some code
}
```

### `dotnet_sort_system_directives_first = true`

**Explanation:**
This setting enforces that System using directives are placed at the top of the list of using directives.

**C# Code Example:**
```csharp
// 'System' directives are placed first, followed by non-'System' directives.
using System;
using System.Collections.Generic;
using System.Linq; 
using MyNamespace;

public class Example
{
    // some code
}
```

### `file_header_template = unset`

**Explanation:**
This setting specifies that no specific file header template is required.

## this Preferences 

### `dotnet_style_qualification_for_event = false`
### `dotnet_style_qualification_for_field = false`
### `dotnet_style_qualification_for_method = false`
### `dotnet_style_qualification_for_property = false`

**Explanation:**
These settings specify that using `this.` qualification for events, fields, methods, and properties is not enforced. 
This allows for a cleaner and less cluttered codebase.

**C# Code Example:**
```csharp
public class Example
{
    public event EventHandler MyEvent;
    private int myField;

    public int MyProperty { get; set; }

    public void MyMethod()
    {
        Console.WriteLine("Hello, world!");
    }

    public void AnotherMethod()
    {
        MyEvent?.Invoke(this, EventArgs.Empty);  // No 'this.' required for events.
        myField = 10;  // No 'this.' required for fields.
        MyMethod();  // No 'this.' required for methods.
        MyProperty = 20;  // No 'this.' required for properties.
    }
}
```

## Language Keywords vs BCL Types Preferences

### `dotnet_style_predefined_type_for_locals_parameters_members = true`
### `dotnet_style_predefined_type_for_member_access = true`

**Explanation:**
This setting specifies a preference for using predefined language keywords (e.g., `int`, `string`) over BCL types (e.g., `Int32`, `String`) for locals, parameters, and members. 
This can make the code more readable and consistent.

**C# Code Example:**
```csharp
public class Example
{
    private int myField;  // Prefer 'int' over 'Int32'.

    public void MyMethod(string message)  // Prefer 'string' over 'String'.
    {
        int localVariable = 69;  // Prefer 'int' over 'Int32'.
        int maxValue = int.MaxValue;  // Prefer 'int' over 'Int32'.
        string otherMessage = "Hello, world!";  // Prefer 'string' over 'String'.
    }
}
```

## Parentheses Preferences

### `dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity`

**Explanation:**
This setting specifies that parentheses should always be used around arithmetic binary operators (e.g., `+`, `-`, `*`, `/`) to enhance code clarity.

**C# Code Example:**
```csharp
public class Example
{
    public void MyMethod()
    {
        int result = (1 + 2) * (3 - 4);  // Parentheses used for clarity.
        Console.WriteLine(result);
    }
}
```

### `dotnet_style_parentheses_in_other_operators = never_if_unnecessary`

**Explanation:**
This setting specifies that parentheses should not be used around other operators if they are unnecessary. 
This helps reduce clutter in the code.

**C# Code Example:**
```csharp
public class Example
{
    public void MyMethod()
    {
        int a = 5;
        int b = 10;
        bool result = a < b;  // No unnecessary parentheses.
        Console.WriteLine(result);
    }
}
```

### `dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity`

**Explanation:**
This setting specifies that parentheses should always be used around relational binary operators (e.g., ==, !=, <, >) to enhance code clarity.

**C# Code Example:**
```csharp
public class Example
{
    public void MyMethod()
    {
        bool result = (5 > 3) && (2 < 4);  // Parentheses used for clarity.
        Console.WriteLine(result);
    }
}
```

## Modifier Preferences

### `dotnet_style_require_accessibility_modifiers = for_non_interface_members`

**Explanation:**
This setting specifies that accessibility modifiers (e.g., `public`, `private`, `protected`) should be required for non-interface members. 
This helps make the code's accessibility clear and explicit.

**C# Code Example:**
```csharp
public class Example
{
    private int myField;  // Accessibility modifier specified.

    public int MyProperty { get; set; }  // Accessibility modifier specified.

    public void MyMethod()  // Accessibility modifier specified.
    {
        Console.WriteLine("Hello, world!");
    }
}

public interface IExample
{
    // Accessibility modifiers are not required for interface members.
    int MyProperty { get; set; }
    void MyMethod();
}
```

## Field Preferences

### `dotnet_style_readonly_field = true`

**Explanation:**
This setting specifies a preference for using `readonly` fields where possible.
Readonly fields are useful when the value assigned to the field will not change after initialization, providing clarity and preventing accidental modification.

**C# Code Example:**
```csharp
public class Example
{
    private readonly int initialValue = 10;  // Readonly field initialized with a value.

    public Example()
    {
        Console.WriteLine(initialValue);
    }
}
```

## Expression level preferences

### `dotnet_style_coalesce_expression = true`

**Explanation:**
This setting specifies a preference for using the null-coalescing operator (`??`) over conditional expressions for null check and assignment. It provides a more concise and readable way to handle null values.

**C# Code Example:**
```csharp
public class Example
{
    public string GetName(string name)
    {
        string result = name ?? "DefaultName";  // Null-coalescing operator used.
        return result;
    }
}
```

### `dotnet_style_collection_initializer = true`

**Explanation:**

This setting specifies a preference for using collection initializer syntax over explicit constructor syntax when initializing collections. 
It improves code readability and conciseness.

```csharp
public class Example
{
    public List<int> GetNumbers()
    {
        List<int> numbers = new() { 1, 2, 3 };  // Collection initializer syntax used.
        return numbers;
    }
}
```

### `dotnet_style_explicit_tuple_names = true`

**Explanation:**

This setting specifies that explicit tuple element names should be required when deconstructing tuples or assigning to tuple variables. 
Explicit names enhance code readability and maintainability.

```csharp
public class Example
{
    public (int id, string name) GetPerson()
    {
        return (1, "John");  // Tuple with explicit names.
    }

    public void ProcessPerson()
    {
        var person = GetPerson();
        var (id, name) = person;  // Deconstruction with explicit names.
        Console.WriteLine($"{id}: {name}");
    }
}
```

### `dotnet_style_namespace_match_folder = true`

**Explanation:**

This setting specifies that the namespace declaration should match the folder structure where the file resides. 
This convention helps organize and locate files within the project structure.

```csharp
// File: /Project/Utilities/Helper.cs
namespace Project.Utilities;

public class Helper
{
    // Class implementation
}
```

### `dotnet_style_null_propagation = true`

**Explanation:**
This setting specifies a preference for using null propagation operators (?. and ?[]) over explicit null checks. 
It improves code readability and reduces verbosity when accessing members of potentially null objects or collections.

**C# Code Example:**
```csharp
public class Example
{
    public int GetStringLength(string? text)
    {
        int length = text?.Length ?? 0;  // Null propagation operator used.
        return length;
    }
}
```

### `dotnet_style_object_initializer = true`

**Explanation:**
This setting specifies a preference for using object initializer syntax (e.g., new MyClass { Prop1 = value1, Prop2 = value2 }) over explicit constructor syntax when initializing objects. 
It provides a more concise and readable way to set object properties.

**C# Code Example:**
```csharp
public class Example
{
    public void CreatePerson()
    {
        var person = new Person
        {
            FirstName = "John",
            LastName = "Doe"
        };  // Object initializer syntax used.
    }
}
```

### `dotnet_style_operator_placement_when_wrapping = beginning_of_line`

**Explanation:**
This setting specifies that operators should be placed at the beginning of lines when wrapping expressions. 
It improves code readability by clearly indicating where operators are used in complex expressions.

**C# Code Example:**
```csharp
public class Example
{
    public void WrappedExpression()
    {
        if (true
            && true)  // Operator placed at the beginning of the line.
        {
            // Code block
        }
    }
}

```

### `dotnet_style_prefer_auto_properties = true`

**Explanation:**
This setting specifies a preference for using auto-implemented properties (e.g., public int MyProperty { get; set; }) over manually implemented ones.
Auto properties reduce boilerplate code and improve maintainability.

**C# Code Example:**
```csharp
public class Example
{
    public int MyProperty { get; set; }  // Auto-implemented property.
}
```

### `dotnet_style_prefer_collection_initializer = when_types_loosely_match`

**Explanation:**
This setting specifies a preference for using collection initializer syntax when the collection type matches loosely. 
It simplifies code and improves readability when initializing collections.

**C# Code Example:**
```csharp
public class Example
{
    public List<int> GetNumbers()
    {
        IEnumerable<int> numbers = new List<int> { 1, 2, 3 };  // Collection initializer used when types loosely match.
        return numbers.ToList();
    }
}
```

### `dotnet_style_prefer_compound_assignment = true`

**Explanation:**
This setting specifies a preference for using compound assignment operators (e.g., +=, -=, etc.) over separate assignment and operation. 
It enhances code conciseness and clarity.

**C# Code Example:**
```csharp
public class Example
{
    public void UpdateCounter(ref int counter)
    {
        counter += 10;  // Compound assignment operator used.
    }
}
```

### `dotnet_style_prefer_conditional_expression_over_assignment = true`

**Explanation:**
This setting specifies a preference for using conditional expressions (?:) over assignment statements. 
It can make code more concise and readable in certain conditional assignment scenarios.

**C# Code Example:**
```csharp
public class Example
{
    public int GetAbsoluteValue(int number)
    {
        int absValue = number >= 0 ? number : -number;  // Conditional expression used for absolute value calculation.
        return absValue;
    }
}
```

### `dotnet_style_prefer_conditional_expression_over_return = true`

**Explanation:**
This setting specifies a preference for using conditional expressions (?:) over return statements. 
It can make code more concise and readable when returning values based on conditions.

**C# Code Example:**
```csharp
public class Example
{
    public string GetGreeting(bool isFormal)
    {
        return isFormal ? "Hello, Sir/Madam." : "Hi there!";  // Conditional expression used for returning different greetings.
    }
}
```

### `dotnet_style_prefer_foreach_explicit_cast_in_source = when_strongly_typed`

**Explanation:**
This setting specifies a preference for using an explicit cast in foreach loops when the collection type is strongly typed. 
It ensures type safety and clarity in foreach iterations.

**C# Code Example:**
```csharp
public class Example
{
    public void ProcessNumbers()
    {
        var list = new List<object>();
        foreach (string item in list.Cast<string>())
        {
            // some code
        }
    }
}

```

### `dotnet_style_prefer_inferred_tuple_names = true`

**Explanation:**
This setting specifies a preference for using inferred element names in tuples. 
It simplifies tuple usage by allowing the compiler to infer element names from variable names during tuple initialization.

**C# Code Example:**
```csharp
public class Example
{
    public (int id, string name) GetPerson()
    {
        return (1, "John");  // Tuple with inferred element names.
    }

    public void ProcessPerson()
    {
        var person = GetPerson();
        var (id, name) = person;  // Deconstruction with inferred names.
        Console.WriteLine($"{id}: {name}");
    }
}
```

### `dotnet_style_prefer_is_null_check_over_reference_equality_method = true`

**Explanation:**
This setting specifies a preference for using is null check over reference equality method (== null or != null) for null checks. 
It promotes clearer and more consistent null checks in the code.

**C# Code Example:**
```csharp
public class Example
{
    public void CheckIfNull(string? text)
    {
        if (text is null)  // 'is null' check used.
        {
            Console.WriteLine("Text is null");
        }
    }
}
```

### `dotnet_style_prefer_simplified_boolean_expressions = true`

**Explanation:**
This setting specifies a preference for simplified boolean expressions where possible.  
(that return a constant value of true or false versus retaining conditional expressions with explicit true or false return values)

It encourages using simpler and more readable boolean conditions in if-statements and loops.

**C# Code Example:**
```csharp
public class Example
{
    public bool IsNameValid(string? name)
    {
        // dotnet_style_prefer_simplified_boolean_expressions = true
        return !string.IsNullOrEmpty(name);  // Simplified boolean expression.

        // dotnet_style_prefer_simplified_boolean_expressions = false
        return !string.IsNullOrEmpty(name) ? true : false;  // explicit.
    }
}
```

### `dotnet_style_prefer_simplified_interpolation = true`

**Explanation:**
This setting specifies a preference for simplified string interpolation. 
It encourages using interpolated strings when combining string literals and expressions.

**C# Code Example:**
```csharp
public class Example
{
    public string GreetPerson(string? name)
    {
        return $"Hello, {name}!";  // Simplified string interpolation.

        //return $"Hello, {name.ToString()}!";  // explicit method call.
    }
}
```

## Parameter Preferences

### `dotnet_style_prefer_simplified_interpolation = true`

**Explanation:**
This setting ensures that the compiler warns about all unused parameters in methods, constructors, and indexers. 
This helps in identifying and cleaning up unnecessary code, improving maintainability and readability.

**C# Code Example:**
```csharp
public class Example
{
    // This method has an unused parameter 'unusedParam'.
    public void DoWork(int usedParam, int unusedParam)
    {
        Console.WriteLine(usedParam);
        // Warning: The parameter 'unusedParam' is assigned but its value is never used.
    }
}
```

## Suppression Preferences

### `dotnet_remove_unnecessary_suppression_exclusions = none`

**Explanation:**
This setting specifies that no unnecessary suppression exclusions should be present, enabling the rule for all types of suppressions without any exclusions. 
It ensures that all unnecessary suppressions are automatically removed, keeping the codebase clean from redundant suppression directives.

**C# Code Example:**

```csharp
using System.Diagnostics.CodeAnalysis;

class PragmaExample
{
    // Necessary pragma suppression
    #pragma warning disable IDE0051 // IDE0051: Remove unused member
    private int UnusedMethod() => 0;

    // IDE0079: Unnecessary pragma suppression -> Remove this
    #pragma warning disable IDE0051 // IDE0051: Remove unused member
    private int UsedMethod() => 0;

    public int PublicMethod() => UsedMethod();
}

class SuppressMessageExample
{
    // Necessary SuppressMessage attribute suppression
    [SuppressMessage("CodeQuality", "IDE0051:Remove unused private members", Justification = "<Pending>")]
    private int _unusedField;

    // IDE0079: Unnecessary SuppressMessage attribute suppression -> Remove this
    [SuppressMessage("CodeQuality", "IDE0051:Remove unused private members", Justification = "<Pending>")]
    private int _usedField;

    public int PublicMethod2() => _usedField;
}
```

## New Line Preferences

### `dotnet_style_allow_multiple_blank_lines_experimental = false`

**Explanation:**
This setting disallows the use of multiple blank lines in the code. 
It enforces a cleaner and more compact code structure by preventing unnecessary blank lines.

**C# Code Example:**
```csharp
public class Example
{
    public void Method1()
    {
        Console.WriteLine("Method1");

        // Only one blank line is allowed.
        Console.WriteLine("Multiple blank lines are not allowed here.");
    }
}
```

### `dotnet_style_allow_statement_immediately_after_block_experimental = false`

**Explanation:**
This setting disallows writing statements immediately after a block (such as after a closing brace) without an additional new line. 
It enforces a more readable code structure by requiring a blank line after closing braces.

**C# Code Example:**
```csharp
public class Example
{
    public void Method1()
    {
        if (true)
        {
            Console.WriteLine("Inside block");
        }
        
        // Blank line required after block
        Console.WriteLine("Immediately after block");
    }
}
```