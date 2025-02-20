# Data Template Syntax Guide

This document provides an overview of the data template syntax used for generating mock data. It leverages a set of predefined placeholders to generate random data, including strings, numbers, dates, and more.

## Important Note 

**Placeholders are only valid if they start with `@`.** If the placeholder does not start with `@`, it will be treated as a plain string and displayed as-is in the output. 

For example: 

- `@name` will generate a random name. 
- `name` (without the `@`) will be displayed exactly as "name" in the output.

## Template Example

```json
{
  "id": "@id",
  "name": "@name",
  "age": "@integer(10, 100)",
  "gender": "@boolean",
  "email": "@email",
  "birthday": "@date('yyyy-MM-dd')",
  "description": "@string(10, 20)",
  "children|1-3": [
    {
      "id": "@id",
      "name": "@name"
    }
  ]
}
```

### Template Fields Description

**`@id`**: Generates a unique identifier (UUID).

**`@name`**: Generates a random name (often in the form of first name and last name).

**`@integer(min, max)`**: Generates a random integer between the `min` and `max` values (inclusive). Example: `@integer(10, 100)` generates a number between 10 and 100.

**`@boolean`**: Generates a random boolean value (`true` or `false`).

**`@email`**: Generates a random email address.

**`@date('yyyy-MM-dd')`**: Generates a random date, formatted according to the specified format (`yyyy-MM-dd` in this case).

**`@string(min, max)`**: Generates a random string with a length between `min` and `max` characters.

**`children|1-3`**: Generates between 1 and 3 child objects. Each child object follows the structure defined inside the array, and their count is randomly determined between 1 and 3.

### Additional Notes

**Randomness**: The values generated by placeholders such as `@id`, `@name`, and `@integer` are completely random, and each template generation will produce different results.

**Date Format**: The `@date` placeholder allows you to specify the date format. You can use standard date formatting patterns like `yyyy-MM-dd`, `yyyy/MM/dd`, `MM-dd-yyyy`, etc.

**Customizable Strings**: The `@string` placeholder allows you to specify the length of the random string to be generated, ranging from `min` to `max` characters.

**Array Elements**: When using array-like placeholders such as `children|1-3`, you can specify the number of array items to generate, and each item can have its own structure.

### Example Output

Here's an example of a generated mock object based on the above template:

```json
{
  "id": "d14f7743-68a2-4f70-b47f-1f697d8f6b27",
  "name": "John Doe",
  "age": 28,
  "gender": true,
  "email": "john.doe@example.com",
  "birthday": "1993-04-15",
  "description": "A random description text",
  "children": [
    {
      "id": "9a72fdfd-651f-4932-ae71-9fd58c63651a",
      "name": "Jane Doe"
    }
  ]
}

```

## Data Template Syntax Reference 

This document provides a comprehensive guide to the template syntax used for generating mock data. It includes placeholders for generating random values such as numbers, strings, booleans, dates, and more. The placeholders are often used in templates to generate dynamic mock data for testing and development purposes.

  ### Available Placeholders

| Placeholder             | Description                                                  | Example                                              | Example Generated Value                        |
| ----------------------- | ------------------------------------------------------------ | ---------------------------------------------------- | ---------------------------------------------- |
| `@id`                   | Generates a unique identifier (UUID)                         | `"id": "@id"`                                        | `"id": "b9d2fd58-7e2d-44e4-b5c2-3c77ef4d09b2"` |
| `@name`                 | Generates a random name                                      | `"name":"@name"`                                     | `"name": "John Doe"`                           |
| `@integer(min,max)`     | Generates a random integer between `min` and `max` . Each param can be replaced with _ | `"age": "@integer(10, 100)"`                         | `"age": 42`                                    |
| `@float(min,max,d)`     | Generates a random floating-point number between `min` and `max`, with `d` decimal places. | `"height": "@float(1.5, 2.0, 2)"`                    | `"height": 1.78`                               |
| `@email`                | Generates a random email address.                            | `"email": "@email"`                                  | `"email": "example@domain.com"`                |
| `@date(format)`         | Generates a random date in the specified format.             | `"birthday": "@date('yyyy-MM-dd')"`                  | `"birthday": "1995-08-25"`                     |
| `@string(len)`          | Generates a random string of `len` characters.               | `"description": "@string(10)"`                       | `"description": "Xtw43jf0g8"`                  |
| `@string(min, max)`     | Generates a random string with length between `min` and `max`. | `"description": "@string(5, 15)"`                    | `"description": "Xtw43jf0g8"`                  |
| `@natural(min, max)`    | Generates a random natural number (non-negative integer) between `min` and `max`. | `"quantity": "@natural(1, 100)"`                     | `"quantity": 57`                               |
| `@boolean`              | Generates a random boolean value (`true` or `false`).        | `"isVerified": "@boolean"`                           | `"isVerified": false`                          |
| `@url`                  | Generates a random URL.                                      | `"profile": "@url"`                                  | `"profile": "http://example.com"`              |
| `@image(width, height)` | Generates a random image URL with the specified width and height. | `"profilePic": "@image(200, 200)"`                   | `"profilePic": "http://example.com/200x200"`   |
| `key\|min-max`           | Generates an array with a random length between `min` and `max`. | `"children\|1-3": [{ "id": "@id", "name": "@name" }]` | `"children": [{ "id": "abc", "name": "Tom" }]` |

