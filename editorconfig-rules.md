# .editorconfig rules

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


## this. and Me. Preferences

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

