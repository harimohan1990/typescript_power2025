### TypeScript  from **beginner to advanced** level. This is designed to take you from knowing nothing about TypeScript to being able to use it confidently in real-world projects and large codebases.

---

## 🧰 **Beginner Level**

### 1. **Introduction to TypeScript**
- What is TypeScript?
- Why use TypeScript?
- TypeScript vs JavaScript
- Installing TypeScript
- Compiling TypeScript (`tsc`)

### 2. **Basic Types**
- `string`, `number`, `boolean`
- `any`, `unknown`, `void`, `never`, `null`, `undefined`
- Type inference
- Type annotations

### 3. **Variables & Constants**
- `let`, `const`, `var` in TS
- Best practices with immutability

### 4. **Functions**
- Typing function parameters and return types
- Optional and default parameters
- Rest parameters
- Function types

### 5. **Objects & Arrays**
- Typing objects
- Typing arrays (`string[]`, `Array<number>`)
- Tuple types

### 6. **Union & Intersection Types**
- Union types (`string | number`)
- Intersection types (`A & B`)

### 7. **Type Aliases & Interfaces**
- Type aliases (`type`)
- Interfaces (`interface`)
- Differences and when to use each
- Readonly and optional properties

---

## ⚙️ **Intermediate Level**

### 8. **Advanced Functions**
- Function overloads
- Call signatures
- Higher-order functions

### 9. **Classes & Inheritance**
- Classes with TypeScript
- Constructors and modifiers (`public`, `private`, `protected`)
- Readonly and static members
- Inheritance and `super`
- Implementing interfaces in classes

### 10. **Generics**
- Generic functions and interfaces
- Constraints with `extends`
- Default generic types
- Generic utility types

### 11. **Modules & Namespaces**
- `import` and `export`
- Default vs named exports
- Organizing TypeScript files
- Declaration merging

### 12. **Enums**
- Numeric and string enums
- Computed and constant members
- Enum pitfalls and alternatives

### 13. **Type Narrowing & Type Guards**
- `typeof`, `instanceof`
- Custom type guards
- Discriminated unions

### 14. **Working with DOM in TS**
- Typing HTML elements
- Event handling in TypeScript

---

## 🚀 **Advanced Level**

### 15. **Advanced Types**
- Conditional types
- Mapped types
- Template literal types
- Keyof, typeof, infer, in
- Recursive types
- Utility types (`Partial`, `Pick`, `Omit`, `Record`, etc.)

### 16. **Type Manipulation**
- Type transformations
- Flattening and deeply nested types
- Branded types

### 17. **Declaration Files**
- What are `.d.ts` files?
- Writing custom type definitions
- Using DefinitelyTyped (`@types`)

### 18. **TypeScript with Tooling**
- Using TS with ESLint and Prettier
- Configuring `tsconfig.json`
- Path aliases and module resolution

### 19. **TypeScript with Frameworks**
- React + TypeScript
- Node.js + TypeScript
- Express + TypeScript

# Introduction to TypeScript

## What is TypeScript?

TypeScript is a strongly-typed, object-oriented programming language developed and maintained by Microsoft. It's a superset of JavaScript, which means that any valid JavaScript code is also valid TypeScript code. TypeScript adds optional static typing and other features to enhance JavaScript's capabilities, especially for large-scale applications.

## Why use TypeScript?

TypeScript offers several advantages over plain JavaScript:

1. **Static Type Checking**: Catches type-related errors during development rather than at runtime
2. **Enhanced IDE Support**: Provides better autocompletion, navigation, and refactoring tools
3. **Improved Code Maintainability**: Type definitions make code more self-documenting
4. **Enterprise-Scale Development**: Better supports large codebases with multiple developers
5. **Future JavaScript Features**: Allows use of newer JavaScript features while maintaining compatibility with older browsers
6. **Safer Refactoring**: Type checking makes it easier to modify code without introducing errors

## TypeScript vs JavaScript

| Feature | TypeScript | JavaScript |
|---------|-----------|------------|
| Type System | Static typing | Dynamic typing |
| Error Detection | Compile-time | Runtime |
| Development Experience | Advanced tooling | Basic tooling |
| Learning Curve | Steeper (types + JS knowledge) | Lower |
| Browser Compatibility | Requires compilation | Native |
| Enterprise Adoption | High | High |
| Community Support | Growing rapidly | Enormous |

TypeScript adds a layer of complexity but provides significant benefits for larger projects and teams.

## Installing TypeScript

You can install TypeScript globally or as a project dependency using npm (Node Package Manager):

**Global installation:**
```bash
npm install -g typescript
```

**Project installation:**
```bash
# Initialize a package.json file if you don't have one
npm init -y
# Install TypeScript as a dev dependency
npm install typescript --save-dev
```

## Compiling TypeScript (`tsc`) in Depth

The TypeScript Compiler (`tsc`) is the core tool that transforms TypeScript code into JavaScript that browsers and Node.js can execute.

### Basic Compilation

The simplest way to compile a TypeScript file is:

```bash
tsc filename.ts
```

This command compiles the TypeScript file to JavaScript with the same name (`filename.js`).

### TypeScript Configuration File (`tsconfig.json`)

For more complex projects, you'll want to create a `tsconfig.json` file to specify compiler options:

```bash
tsc --init
```

This generates a default configuration file with commented options.

### Key Compiler Options

- **target**: Specifies the ECMAScript target version (e.g., "ES5", "ES6", "ES2020")
- **module**: Sets the module system (e.g., "CommonJS", "ESNext", "AMD")
- **outDir**: Defines the output directory for compiled files
- **rootDir**: Specifies the root directory of input files
- **strict**: Enables all strict type checking options
- **esModuleInterop**: Enables interoperability between CommonJS and ES Modules
- **sourceMap**: Generates source map files for debugging

### Watch Mode

To automatically recompile files when they change:

```bash
tsc --watch
```

or

```bash
tsc -w
```

### Project Compilation

To compile an entire project based on `tsconfig.json`:

```bash
tsc
```

### Compiler Internals

The TypeScript compiler works in several phases:

1. **Parsing**: Reads TypeScript source code and produces an Abstract Syntax Tree (AST)
2. **Type Checking**: Verifies type consistency based on explicit and inferred types
3. **Transformation**: Converts TypeScript-specific features to JavaScript equivalents
4. **Emission**: Generates JavaScript output files and optional source maps

### Advanced Compiler Features

- **Declaration Files**: Generate `.d.ts` files with `declaration: true`
- **Project References**: Support for multi-project setups with `references`
- **Incremental Compilation**: Speed up builds with `incremental: true`
- **Build Mode**: Use `tsc --build` for incremental builds of project references
- **Transpilation-Only**: Skip type checking with `transpileOnly: true` (often used with ts-loader)


Here’s a well-organized breakdown of the **Basic Types** in TypeScript based on your outline:

---

## 2. **Basic Types in TypeScript**

### ✅ 1. **Primitive Types**
#### - `string`
Represents textual data.
```ts
let username: string = "John";
```

#### - `number`
Represents all numeric values (integers, floats, etc.).
```ts
let age: number = 25;
```

#### - `boolean`
Represents `true` or `false`.
```ts
let isLoggedIn: boolean = true;
```

---

### 🔁 2. **Special Types**
#### - `any`
Opt-out of type checking.
```ts
let value: any = "Hello";
value = 10; // Allowed
```

#### - `unknown`
Safer alternative to `any`. Must be type-checked before use.
```ts
let data: unknown = 30;

if (typeof data === "number") {
  console.log(data + 1);
}
```

#### - `void`
Used for functions that do not return a value.
```ts
function logMessage(msg: string): void {
  console.log(msg);
}
```

#### - `never`
Represents values that never occur (e.g., function never returns or always throws).
```ts
function throwError(): never {
  throw new Error("Something went wrong!");
}
```

#### - `null` and `undefined`
```ts
let a: null = null;
let b: undefined = undefined;
```

---

### 🧠 3. **Type Inference**
TypeScript can infer types from values automatically.
```ts
let city = "New York"; // inferred as string
let score = 99;        // inferred as number
```
> Good for quick variable declaration, but explicit types improve clarity.

---

### ✍️ 4. **Type Annotations Deep Dive**
You can explicitly annotate types to increase readability and reduce bugs.
```ts
// Variable
let price: number = 150.0;

// Function parameters and return type
function greet(name: string): string {
  return `Hello, ${name}!`;
}

// Arrays
let colors: string[] = ["red", "green", "blue"];

// Objects
let user: { id: number; name: string } = {
  id: 1,
  name: "Alice"
};
```

Here's a clear comparison between **TypeScript** and **JavaScript** to help understand how they differ and when to use one over the other:

---

## ⚔️ TypeScript vs JavaScript

| Feature | **JavaScript** | **TypeScript** |
|--------|----------------|----------------|
| **Type System** | Dynamically typed | Statically typed (with type annotations) |
| **Error Detection** | Runtime | Compile-time (before running the code) |
| **Code Safety** | Low (more prone to bugs) | High (catches errors early) |
| **Tooling & IDE Support** | Good | Excellent (with autocompletion, refactoring, type hints) |
| **Learning Curve** | Easier (no extra syntax) | Slightly steeper (requires understanding of types) |
| **Compilation** | Interpreted directly by browsers | Needs to be compiled to JavaScript |
| **OOP Support** | Limited (prototype-based) | Enhanced (access modifiers, interfaces, abstract classes) |
| **Community & Libraries** | Massive ecosystem | Superset of JS, works with all JS libraries |
| **Scalability** | Good for small to medium projects | Great for large-scale, maintainable codebases |

---

### ✅ **TypeScript Strengths**
- Catches **bugs early**
- Easier **refactoring**
- Better **editor support**
- Ideal for **large teams/projects**

### ⚠️ **JavaScript Strengths**
- **Simpler syntax**, no build step
- Runs **natively in browsers**
- Better for **quick scripts, prototypes**

---

### 🧠 Code Example Comparison

#### JavaScript
```js
function greet(name) {
  return "Hello, " + name;
}
greet(42); // no error until runtime
```

#### TypeScript
```ts
function greet(name: string): string {
  return "Hello, " + name;
}
greet(42); // ❌ Error: Argument of type 'number' is not assignable to parameter of type 'string'
```

---

### 💡 Summary
- Use **JavaScript** for quick tasks, small projects, or if you're just starting out.
- Use **TypeScript** for long-term, maintainable, and scalable applications.

---

TypeScript Types**, including brief explanations and examples for each:

---

## 🧩 **TypeScript Types**

TypeScript includes several built-in and advanced types for writing safer, more predictable code.

---

### ✅ **Primitive Types**

#### `number`
Represents all numbers: integers, floats, hex, binary, etc.
```ts
let count: number = 42;
```

#### `string`
Textual data.
```ts
let username: string = "Alice";
```

#### `boolean`
True/false values.
```ts
let isAdmin: boolean = false;
```

---

### 🔄 **Special Types**

#### `any`
Turns off type checking.
```ts
let data: any = "hello";
data = 42; // allowed
```

#### `void`
Used for functions that return nothing.
```ts
function log(msg: string): void {
  console.log(msg);
}
```

#### `null` & `undefined`
They are their own types.
```ts
let a: null = null;
let b: undefined = undefined;
```

#### `never`
Used for functions that never return.
```ts
function error(msg: string): never {
  throw new Error(msg);
}
```

---

### 🧱 **Object Types**

#### `object`
Non-primitive values.
```ts
let user: object = { name: "John" };
```

#### `symbol`
Creates unique identifiers.
```ts
let sym1: symbol = Symbol("id");
```

---

### 🧮 **Advanced Types**

#### `enum` (Enumerated Types)
Named constants.
```ts
enum Role {
  User,
  Admin,
  SuperAdmin
}
let role: Role = Role.Admin;
```

#### `tuple`
Fixed-length arrays with known types.
```ts
let person: [string, number] = ["John", 30];
```

#### `Array`
Array of a certain type.
```ts
let scores: number[] = [10, 20, 30];
// or
let names: Array<string> = ["Alice", "Bob"];
```

#### `union`
A variable can hold more than one type.
```ts
let id: string | number;
id = "abc";
id = 123;
```

#### `intersection`
Combines multiple types.
```ts
type A = { name: string };
type B = { age: number };
type C = A & B;

const person: C = { name: "John", age: 25 };
```

#### `type` aliases
Custom type names.
```ts
type UserID = string | number;
let userId: UserID = 101;
```

#### `type assertion`
Tell TypeScript the exact type you're using (type casting).
```ts
let someValue: unknown = "hello";
let strLength: number = (someValue as string).length;
```

---

The **latest stable version of TypeScript** as of now is:

> 🔷 **TypeScript 5.4** (Released: February 29, 2024)

---

### 🆕 Key Features in TypeScript 5.4

1. **Preserved Narrowing with `const` in Loops**  
   TypeScript now better understands when `const` is used inside loops and preserves type narrowing.

2. **Control Flow Narrowing for Constant Discriminants**  
   Smarter type narrowing based on discriminated unions with `const` values.

3. **Symbol and Template String Type Improvements**  
   Enhanced support for template literal types and unique `symbol` operations.

4. **More Precise `super` Calls**  
   TypeScript now has better type inference and checking for `super()` in class hierarchies.

5. **Editor Improvements**  
   Enhanced IntelliSense, auto imports, and faster project-wide type checking.

---

### 📦 How to Check TypeScript Version

Use this command in your terminal:
```bash
tsc --version
```

### 🔄 How to Upgrade TypeScript
If you're using `npm`, you can upgrade globally:
```bash
npm install -g typescript
```
Or locally to your project:
```bash
npm install --save-dev typescript
```

---

Awesome! Here’s how to run your **first TypeScript program with HTML and CSS** – no Node.js needed, just your browser. 🔥

---

## 📦 Project Structure

```
project-folder/
│
├── index.html
├── style.css
├── main.ts
├── main.js (generated by TypeScript)
```

---

### 🔹 `index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>TypeScript with HTML & CSS</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1 id="greeting">Loading...</h1>

  <script src="main.js"></script>
</body>
</html>
```

---

### 🔹 `style.css`
```css
body {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 100px;
  background-color: #f0f0f0;
  color: #333;
}

h1 {
  font-size: 3rem;
  color: #007acc;
}
```

---

### 🔹 `main.ts`
```ts
function greet(name: string): string {
  return `Hello, ${name}! 👋`;
}

const greetingElement = document.getElementById("greeting");

if (greetingElement) {
  greetingElement.textContent = greet("TypeScript + HTML + CSS");
}
```

---

### 🛠️ Compile TypeScript

Run this in your terminal:

```bash
tsc main.ts
```

This generates `main.js`, which the HTML file loads.

---

### 🌐 Open in Browser

Just open `index.html` in your browser. You’ll see:

> **Hello, TypeScript + HTML + CSS! 👋**

---

### 💡 Optional: Auto-Compile TypeScript
Run this to watch for changes:

```bash
tsc main.ts --watch
```

Or use a `tsconfig.json` for a cleaner setup.

---
 **first TypeScript program using ReactJS** with HTML and CSS.

---

## ⚛️ TypeScript + React Setup

### ✅ Quickest Way: Using `Vite` (recommended for speed and simplicity)

---

### 🛠️ Step 1: Create Project

```bash
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
```

This gives you:
- React
- TypeScript
- Vite for fast development
- CSS support

---

### 📂 Project Structure

```
my-app/
├── public/
├── src/
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── index.html
├── tsconfig.json
├── vite.config.ts
```

---

### 🧑‍💻 Step 2: Edit `App.tsx`

```tsx
// src/App.tsx
import './App.css';

type Props = {
  name: string;
};

function App({ name }: Props) {
  return (
    <div className="container">
      <h1>Hello, {name}! 👋</h1>
    </div>
  );
}

export default App;
```

---

### 🧠 Step 3: Use `App` in `main.tsx`

```tsx
// src/main.tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App name="TypeScript + React" />
  </React.StrictMode>
);
```

---

### 🎨 Step 4: Add Styles in `App.css`

```css
/* src/App.css */
.container {
  text-align: center;
  margin-top: 100px;
  font-family: sans-serif;
  background-color: #f0f8ff;
  padding: 2rem;
  border-radius: 12px;
}

h1 {
  color: #007acc;
  font-size: 3rem;
}
```

---

### 🚀 Step 5: Run the App

```bash
npm run dev
```

Open `http://localhost:5173` and you’ll see:

> **Hello, TypeScript + React! 👋**

---

Great question! Let’s break down the **difference between `null` and `undefined`** in JavaScript/TypeScript:

---

## 🔍 `null` vs `undefined`

| Feature        | `null`                           | `undefined`                        |
|----------------|----------------------------------|------------------------------------|
| **Meaning**    | *Intentional* absence of value   | *Unintentional* absence (not assigned) |
| **Type**       | `object`                         | `undefined`                        |
| **Set by**     | Developer (manually assigned)    | JavaScript (automatically)         |
| **Common Usage** | Used when you want to "empty" a variable | Default value for uninitialized variables |
| **Equality**   | `null == undefined` → `true` <br> `null === undefined` → `false` | same |
| **Use Case**   | Reset value, explicit "nothing"  | Unset, uninitialized, missing      |

---

### 💡 Code Examples

#### `undefined`
```ts
let a;
console.log(a); // undefined (not assigned)

function doSomething(): void {}
let result = doSomething(); // result is undefined
```

#### `null`
```ts
let b: string | null = null;
console.log(b); // null (explicitly assigned)

let user = {
  name: null, // explicitly means "no name"
};
```

---

### ✅ TypeScript Usage

You can explicitly type variables to accept one or both:

```ts
let value: string | null; // can be string or null
let anotherValue: number | undefined; // number or not yet set
```

> In TypeScript `strictNullChecks` mode, `null` and `undefined` are not assignable unless explicitly allowed in the type.

---

### 🧠 Summary

| Concept       | `null`                    | `undefined`                      |
|---------------|---------------------------|----------------------------------|
| You set it    | ✅                        | ❌ (unless explicitly done)       |
| JS sets it    | ❌                        | ✅                                |
| Means         | "Empty" / nothing here    | "Not assigned yet"               |

---

 **rules for valid variable names** in JavaScript/TypeScript:

### 1. **The variable name must start with an alphabet or an underscore (`_`) or a dollar sign (`$`)**
   - **Valid:**
     - `age`
     - `_name`
     - `$amount`
   - **Invalid:**
     - `123age` (starts with a number, which is not allowed)

### 2. **The variable name cannot start with digits**
   - **Valid:** 
     - `age1`
     - `_2ndName`
     - `$amount2`
   - **Invalid:**
     - `123var` (starts with digits)
     - `1stName` (starts with digits)

### 3. **The variable name cannot contain spaces or special characters, except for the underscore (`_`) and dollar sign (`$`)**
   - **Valid:**
     - `user_name`
     - `firstName`
     - `total$amount`
   - **Invalid:**
     - `user name` (contains space)
     - `first-name` (contains a hyphen `-`)
     - `total@amount` (contains `@`, a special character)

### 🧩 **General Rules Summary**
| Rule                               | Example          | Valid/Invalid |
|------------------------------------|------------------|---------------|
| Starts with an alphabet or `_` or `$` | `age`, `_name`, `$amount` | ✅ Valid |
| Cannot start with digits           | `1stName`, `123var` | ❌ Invalid |
| No spaces or special characters (except `_` and `$`) | `user_name`, `total$amount` | ✅ Valid |
| Examples of invalid variable names | `user name`, `first-name`, `total@amount` | ❌ Invalid |

### 💡 Additional Notes:
- JavaScript/TypeScript is **case-sensitive**, meaning `userName` and `username` are two different variables.
- You can use **camelCase** (e.g., `firstName`), **snake_case** (e.g., `first_name`), or **PascalCase** (e.g., `FirstName`) for variable names depending on your coding style or conventions.

---

### 🖋️ Examples in Code

#### Valid Variable Names:
```ts
let age: number = 30;
let _name: string = "John";
let $salary: number = 5000;
```

#### Invalid Variable Names:
```ts
let 123abc: string = "Invalid"; // Starts with a number
let first-name: string = "Invalid"; // Contains a hyphen
let user name: string = "Invalid"; // Contains a space
```

---
In TypeScript (just like JavaScript), operators are symbols or keywords used to perform operations on variables and values. Here's a breakdown of the key **operators** in TypeScript:

---

### 1. **Arithmetic Operators**
These operators perform basic mathematical operations.

| Operator  | Description          | Example        |
|-----------|----------------------|----------------|
| `+`       | Addition             | `5 + 3 = 8`    |
| `-`       | Subtraction          | `5 - 3 = 2`    |
| `*`       | Multiplication       | `5 * 3 = 15`   |
| `/`       | Division             | `6 / 3 = 2`    |
| `%`       | Modulus (remainder)  | `5 % 2 = 1`    |
| `**`      | Exponentiation       | `2 ** 3 = 8`   |

---

### 2. **Assignment Operators**
These operators assign values to variables.

| Operator | Description                 | Example            |
|----------|-----------------------------|--------------------|
| `=`      | Assigns value to variable    | `let x = 5;`       |
| `+=`     | Adds and assigns            | `x += 3;` // `x = x + 3;` |
| `-=`     | Subtracts and assigns       | `x -= 2;` // `x = x - 2;` |
| `*=`     | Multiplies and assigns      | `x *= 2;` // `x = x * 2;` |
| `/=`     | Divides and assigns         | `x /= 4;` // `x = x / 4;` |
| `%=`     | Modulus and assigns         | `x %= 3;` // `x = x % 3;` |

---

### 3. **Comparison Operators**
These operators compare two values and return a boolean (`true` or `false`).

| Operator | Description               | Example           |
|----------|---------------------------|-------------------|
| `==`     | Equal to                  | `5 == 5` → `true` |
| `===`    | Strictly equal to         | `5 === '5'` → `false` |
| `!=`     | Not equal to              | `5 != 3` → `true` |
| `!==`    | Strictly not equal to     | `5 !== '5'` → `true` |
| `>`      | Greater than              | `5 > 3` → `true`  |
| `<`      | Less than                 | `3 < 5` → `true`  |
| `>=`     | Greater than or equal to  | `5 >= 5` → `true` |
| `<=`     | Less than or equal to     | `3 <= 5` → `true` |

---

### 4. **Logical Operators**
These operators are used to combine conditional expressions.

| Operator | Description                 | Example                        |
|----------|-----------------------------|--------------------------------|
| `&&`     | Logical AND (both true)      | `true && false` → `false`      |
| `||`     | Logical OR (either true)     | `true || false` → `true`       |
| `!`      | Logical NOT (negation)       | `!true` → `false`              |

---

### 5. **Bitwise Operators**
These operators work on binary representations of numbers.

| Operator | Description                     | Example          |
|----------|---------------------------------|------------------|
| `&`      | Bitwise AND                     | `5 & 3` → `1`    |
| `|`      | Bitwise OR                      | `5 | 3` → `7`    |
| `^`      | Bitwise XOR (exclusive OR)      | `5 ^ 3` → `6`    |
| `~`      | Bitwise NOT (inverts bits)      | `~5` → `-6`      |
| `<<`     | Left shift (shifts bits left)   | `5 << 1` → `10`  |
| `>>`     | Right shift (shifts bits right) | `5 >> 1` → `2`   |
| `>>>`    | Zero-fill right shift          | `-5 >>> 1` → `2147483642` |

---

### 6. **Type Operators**
These are used to manipulate types in TypeScript.

| Operator    | Description                                       | Example                 |
|-------------|---------------------------------------------------|-------------------------|
| `typeof`    | Returns the type of a variable (runtime type)     | `typeof "hello"` → `string` |
| `instanceof`| Checks if an object is an instance of a class     | `obj instanceof Class`   |
| `in`        | Checks if a property exists in an object or type  | `'name' in obj` → `true` |
| `as`        | Type assertion (casting)                         | `let str = someVar as string;` |

---

### 7. **Ternary Operator (Conditional Operator)**
A shorthand for `if-else` statements. It takes three operands.

```ts
let age = 20;
let canVote = (age >= 18) ? "Yes" : "No"; // "Yes"
```

Syntax:
```ts
condition ? exprIfTrue : exprIfFalse;
```

---

### 8. **Nullish Coalescing Operator (`??`)**
Used to provide a default value when a variable is `null` or `undefined`.

```ts
let name = null;
let displayName = name ?? "Default Name"; // "Default Name"
```

---

### 9. **Spread and Rest Operators**

#### Spread (`...`)
Expands elements of an array or object into individual items.

```ts
let arr = [1, 2, 3];
let newArr = [...arr, 4, 5];  // [1, 2, 3, 4, 5]
```

#### Rest (`...`)
Collects multiple items into an array (typically in function parameters).

```ts
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}
```

---

### 10. **Optional Chaining (`?.`)**
Allows safe access to deeply nested properties without causing runtime errors.

```ts
let person = { name: "Alice", address: { city: "Wonderland" } };
let city = person.address?.city; // "Wonderland"
```

---

### Summary Table:

| Operator                | Description                                  |
|-------------------------|----------------------------------------------|
| `+`, `-`, `*`, `/`, `%`, `**` | Arithmetic Operators                        |
| `=`, `+=`, `-=`          | Assignment Operators                         |
| `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=` | Comparison Operators        |
| `&&`, `||`, `!`          | Logical Operators                            |
| `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>` | Bitwise Operators           |
| `typeof`, `instanceof`, `in`, `as` | Type Operators                      |
| `?:`                    | Ternary Operator                             |
| `??`                    | Nullish Coalescing Operator                  |
| `...`                   | Spread and Rest Operators                    |
| `?.`                    | Optional Chaining Operator                   |

---


Here are **TypeScript examples** for the operators mentioned:

---

### 1. **Arithmetic Operators**

```ts
let x: number = 10;
let y: number = 5;

let addition = x + y; // 10 + 5 = 15
let subtraction = x - y; // 10 - 5 = 5
let multiplication = x * y; // 10 * 5 = 50
let division = x / y; // 10 / 5 = 2
let modulus = x % y; // 10 % 5 = 0
let exponentiation = x ** 2; // 10 ** 2 = 100

console.log(addition, subtraction, multiplication, division, modulus, exponentiation);
```

---

### 2. **Assignment Operators**

```ts
let a: number = 10;
a += 5; // a = a + 5 → a = 15
a -= 3; // a = a - 3 → a = 12
a *= 2; // a = a * 2 → a = 24
a /= 4; // a = a / 4 → a = 6
a %= 3; // a = a % 3 → a = 0

console.log(a); // 0
```

---

### 3. **Comparison Operators**

```ts
let a: number = 10;
let b: number = 5;

console.log(a == b);  // false
console.log(a === b); // false (type checking as well)
console.log(a != b);  // true
console.log(a > b);   // true
console.log(a < b);   // false
console.log(a >= b);  // true
console.log(a <= b);  // false
```

---

### 4. **Logical Operators**

```ts
let a: boolean = true;
let b: boolean = false;

console.log(a && b); // false (both must be true)
console.log(a || b); // true (either can be true)
console.log(!a);     // false (negation)
```

---

### 5. **Bitwise Operators**

```ts
let x: number = 5;  // 0101 in binary
let y: number = 3;  // 0011 in binary

console.log(x & y);  // Bitwise AND → 0101 & 0011 = 0001 → 1
console.log(x | y);  // Bitwise OR → 0101 | 0011 = 0111 → 7
console.log(x ^ y);  // Bitwise XOR → 0101 ^ 0011 = 0110 → 6
console.log(~x);     // Bitwise NOT → ~0101 = 1010 → -6 (two's complement representation)
console.log(x << 1); // Left shift → 0101 << 1 = 1010 → 10
console.log(x >> 1); // Right shift → 0101 >> 1 = 0010 → 2
```

---

### 6. **Type Operators**

#### `typeof`

```ts
let name: string = "Alice";
let age: number = 25;

console.log(typeof name); // "string"
console.log(typeof age);  // "number"
```

#### `instanceof`

```ts
class Person {
  constructor(public name: string) {}
}

let p = new Person("John");

console.log(p instanceof Person); // true
```

#### `in`

```ts
let person = { name: "Alice", age: 25 };

console.log("name" in person); // true
console.log("address" in person); // false
```

#### `as` (Type Assertion)

```ts
let value: any = "This is a string";
let length = (value as string).length;

console.log(length); // 16
```

---

### 7. **Ternary Operator**

```ts
let age: number = 18;
let message: string = (age >= 18) ? "You are an adult" : "You are a minor";
console.log(message); // "You are an adult"
```

---

### 8. **Nullish Coalescing Operator (`??`)**

```ts
let name: string | null = null;
let greeting: string = name ?? "Guest"; // "Guest" (because name is null)

let age: number | undefined = undefined;
let validAge: number = age ?? 30; // 30 (because age is undefined)

console.log(greeting, validAge);
```

---

### 9. **Spread and Rest Operators**

#### Spread Operator (`...`)

```ts
let arr1: number[] = [1, 2, 3];
let arr2: number[] = [...arr1, 4, 5]; // Spread arr1 and add 4 and 5

console.log(arr2); // [1, 2, 3, 4, 5]
```

#### Rest Operator (`...`)

```ts
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

---

### 10. **Optional Chaining (`?.`)**

```ts
let person = { name: "Alice", address: { city: "Wonderland" } };

let city = person.address?.city; // "Wonderland"
let zipCode = person.address?.zipCode; // undefined (safe access)

console.log(city, zipCode);
```

---

### Summary of Operators in TypeScript

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`, `**`
- **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, `%=` 
- **Comparison Operators**: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`
- **Logical Operators**: `&&`, `||`, `!`
- **Bitwise Operators**: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`
- **Type Operators**: `typeof`, `instanceof`, `in`, `as`
- **Ternary Operator**: `condition ? exprIfTrue : exprIfFalse`
- **Nullish Coalescing**: `??`
- **Spread & Rest Operators**: `...`
- **Optional Chaining**: `?.`

---

In TypeScript (and JavaScript), **conditions** and **loops** are fundamental concepts for controlling the flow of your program. Let's dive deep into these concepts, how they work, and how to use them in TypeScript.

### **Conditions in TypeScript**

Conditions help you make decisions based on the values of variables or expressions. In TypeScript, the syntax for conditions is the same as in JavaScript, with additional support for types.

#### **1. If-Else Statement**

The most common way to test conditions is with the `if` statement. It checks a condition, and if the condition is `true`, it executes the code block inside.

```ts
let age: number = 18;

if (age >= 18) {
  console.log("You are an adult.");
} else {
  console.log("You are a minor.");
}
```

#### **2. Else If Statement**

If you have multiple conditions to check, you can chain them with `else if`.

```ts
let age: number = 20;

if (age < 13) {
  console.log("You are a child.");
} else if (age >= 13 && age < 18) {
  console.log("You are a teenager.");
} else if (age >= 18 && age < 65) {
  console.log("You are an adult.");
} else {
  console.log("You are a senior.");
}
```

#### **3. Switch-Case Statement**

The `switch` statement is used to perform multiple checks against a single variable. It's especially useful when you have many different cases.

```ts
let day: number = 3;
let dayName: string;

switch (day) {
  case 1:
    dayName = "Monday";
    break;
  case 2:
    dayName = "Tuesday";
    break;
  case 3:
    dayName = "Wednesday";
    break;
  case 4:
    dayName = "Thursday";
    break;
  case 5:
    dayName = "Friday";
    break;
  case 6:
    dayName = "Saturday";
    break;
  case 7:
    dayName = "Sunday";
    break;
  default:
    dayName = "Invalid day";
}

console.log(dayName); // "Wednesday"
```

### **Loops in TypeScript**

Loops allow you to run a block of code multiple times. TypeScript supports a variety of loops, which are explained below.

#### **1. For Loop**

A `for` loop is one of the most commonly used loops. It iterates over a block of code for a specified number of times.

```ts
for (let i = 0; i < 5; i++) {
  console.log(i); // Outputs: 0, 1, 2, 3, 4
}
```

The `for` loop has three parts:
- **Initialization**: `let i = 0` sets up the loop.
- **Condition**: `i < 5` checks if the loop should continue.
- **Increment/Decrement**: `i++` increases the loop counter after each iteration.

#### **2. For-In Loop**

The `for-in` loop is used to iterate over the **properties of an object** or the **indexes of an array**.

##### Example with Object:

```ts
let person = { name: "Alice", age: 25, city: "Wonderland" };

for (let key in person) {
  console.log(key, person[key]); 
  // Outputs: name Alice, age 25, city Wonderland
}
```

##### Example with Array (index-based):

```ts
let colors = ["red", "green", "blue"];

for (let index in colors) {
  console.log(index, colors[index]);
  // Outputs: 0 red, 1 green, 2 blue
}
```

#### **3. For-Of Loop**

The `for-of` loop is used to iterate over **iterable objects** (like arrays, strings, maps, sets, etc.).

```ts
let colors = ["red", "green", "blue"];

for (let color of colors) {
  console.log(color); 
  // Outputs: red, green, blue
}
```

`for-of` is often preferred over `for-in` when iterating over arrays or collections because it directly accesses the value, not the index.

#### **4. While Loop**

The `while` loop runs as long as a specified condition is true. The condition is evaluated before each iteration.

```ts
let i: number = 0;

while (i < 5) {
  console.log(i); // Outputs: 0, 1, 2, 3, 4
  i++;
}
```

If the condition is `false` initially, the loop will not run at all.

#### **5. Do-While Loop**

The `do-while` loop is similar to the `while` loop, but it guarantees that the loop will run at least once because the condition is checked **after** the code block is executed.

```ts
let i: number = 0;

do {
  console.log(i); // Outputs: 0, 1, 2, 3, 4
  i++;
} while (i < 5);
```

#### **6. Break and Continue**

- `break` is used to **exit** a loop before it completes.
- `continue` is used to **skip** the current iteration and proceed to the next iteration of the loop.

##### Example of `break`:

```ts
for (let i = 0; i < 5; i++) {
  if (i === 3) {
    break; // Exit the loop when i equals 3
  }
  console.log(i); // Outputs: 0, 1, 2
}
```

##### Example of `continue`:

```ts
for (let i = 0; i < 5; i++) {
  if (i === 3) {
    continue; // Skip when i equals 3
  }
  console.log(i); // Outputs: 0, 1, 2, 4
}
```

---

### **Advanced Conditional Expressions in TypeScript**

#### **1. Type Narrowing with `if`**

TypeScript has **type narrowing**, which allows you to safely check types within conditions. This is particularly useful when dealing with unions or types like `null`, `undefined`, or `any`.

```ts
function greet(name: string | null) {
  if (name) {
    console.log(`Hello, ${name}`);
  } else {
    console.log("Hello, Guest");
  }
}

greet("Alice"); // Outputs: Hello, Alice
greet(null); // Outputs: Hello, Guest
```

In the example above, TypeScript automatically narrows the type of `name` to `string` inside the `if` block and `null` inside the `else` block.

#### **2. Using `switch` with Type Guards**

You can combine `switch` with custom type guards to handle different types or values.

```ts
type Animal = "dog" | "cat" | "fish";

function sound(animal: Animal) {
  switch (animal) {
    case "dog":
      console.log("Woof!");
      break;
    case "cat":
      console.log("Meow!");
      break;
    case "fish":
      console.log("Blub!");
      break;
    default:
      throw new Error("Unknown animal");
  }
}

sound("dog"); // Woof!
sound("cat"); // Meow!
```

---

### **Key Points to Remember:**

- **`if`** and **`else`** are used for basic decision-making.
- **`switch`** is better for multiple conditions checking against a single value.
- **Loops** (such as `for`, `while`, `do-while`) are used to iterate over blocks of code.
- **`for-in`** iterates over object properties or array indices, while **`for-of`** iterates over the actual values.
- **Type narrowing** in TypeScript helps to safely check types within conditionals.

---

Arrays in TypeScript are used to store multiple values in a single variable. They can hold elements of the same type or elements of different types (if needed). TypeScript offers enhanced type safety compared to JavaScript by allowing you to explicitly define the types of the elements within an array.

Let’s dive deep into arrays in TypeScript:

### **1. Defining Arrays in TypeScript**

There are multiple ways to define arrays in TypeScript, and you can use both `array` notation and `generic` notation.

#### **1.1 Using Array Type Notation**

In TypeScript, you can define an array type using the `type[]` syntax.

```ts
let numbers: number[] = [1, 2, 3, 4, 5];
let strings: string[] = ["apple", "banana", "cherry"];
```

Here, `numbers` is an array that can only contain numbers, and `strings` is an array that can only contain strings.

#### **1.2 Using Generic Notation**

You can also define arrays using the `Array<type>` generic syntax.

```ts
let numbers: Array<number> = [1, 2, 3, 4, 5];
let strings: Array<string> = ["apple", "banana", "cherry"];
```

Both methods are equivalent and provide the same functionality. You can choose whichever style you prefer.

---

### **2. Multidimensional Arrays**

TypeScript also supports multidimensional arrays, such as 2D or 3D arrays.

```ts
let matrix: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

In the above example, `matrix` is a 2D array (array of arrays), where each inner array contains numbers.

You can also define arrays with more than two dimensions:

```ts
let threeD: number[][][] = [
  [
    [1, 2],
    [3, 4]
  ],
  [
    [5, 6],
    [7, 8]
  ]
];
```

---

### **3. Array of Mixed Types**

In some cases, you might need an array that can hold multiple types of values. TypeScript allows you to define arrays with union types.

```ts
let mixedArray: (string | number | boolean)[] = [1, "apple", true, 2, "banana"];
```

Here, `mixedArray` can contain strings, numbers, and booleans.

Alternatively, you can use the generic syntax:

```ts
let mixedArray: Array<string | number | boolean> = [1, "apple", true, 2, "banana"];
```

---

### **4. Array Methods in TypeScript**

TypeScript arrays support the same methods as JavaScript arrays. However, because TypeScript provides type safety, it ensures that these methods are used in the correct manner according to the array's type.

#### **4.1 Basic Array Methods**

```ts
let numbers: number[] = [1, 2, 3, 4, 5];

// push() - Adds elements to the end
numbers.push(6); // [1, 2, 3, 4, 5, 6]

// pop() - Removes the last element
let lastElement = numbers.pop(); // 6

// shift() - Removes the first element
let firstElement = numbers.shift(); // 1

// unshift() - Adds elements to the beginning
numbers.unshift(0); // [0, 2, 3, 4, 5]

// splice() - Adds/removes elements at a specific index
numbers.splice(2, 1, 8); // Removes 1 element at index 2 and adds 8
console.log(numbers); // [0, 2, 8, 4, 5]
```

#### **4.2 Array Iteration Methods**

```ts
let colors: string[] = ["red", "green", "blue"];

// forEach() - Iterates over the array
colors.forEach(color => console.log(color)); // "red", "green", "blue"

// map() - Transforms each element and returns a new array
let upperColors = colors.map(color => color.toUpperCase());
console.log(upperColors); // ["RED", "GREEN", "BLUE"]

// filter() - Filters elements based on a condition
let longColors = colors.filter(color => color.length > 3);
console.log(longColors); // ["green", "blue"]

// reduce() - Reduces the array to a single value
let concatenatedColors = colors.reduce((acc, color) => acc + color, "");
console.log(concatenatedColors); // "redgreenblue"
```

#### **4.3 Searching and Sorting Arrays**

```ts
let numbers: number[] = [5, 2, 8, 1, 4];

// sort() - Sorts the array in ascending order
numbers.sort((a, b) => a - b); // [1, 2, 4, 5, 8]

// find() - Finds the first element that satisfies a condition
let foundNumber = numbers.find(num => num > 3);
console.log(foundNumber); // 4

// indexOf() - Returns the index of the first occurrence
let index = numbers.indexOf(4);
console.log(index); // 3
```

---

### **5. Array Destructuring**

You can use array destructuring to easily extract values from an array.

```ts
let numbers: number[] = [1, 2, 3];

// Destructuring assignment
let [first, second] = numbers;
console.log(first, second); // 1, 2

// Skipping elements with commas
let [, , third] = numbers;
console.log(third); // 3
```

You can also use the rest operator `...` to collect remaining elements into an array.

```ts
let numbers: number[] = [1, 2, 3, 4, 5];

// Collect the rest of the elements into the remaining array
let [first, second, ...rest] = numbers;
console.log(first);  // 1
console.log(second); // 2
console.log(rest);   // [3, 4, 5]
```

---

### **6. Array Type Assertions**

If you are confident that a variable is an array, but TypeScript cannot infer it, you can use a type assertion to tell TypeScript what type the variable should be.

```ts
let input = "1,2,3";
let numbers = <number[]>input.split(","); // TypeScript assumes it's a number array
console.log(numbers); // [1, 2, 3]
```

Note that this approach should be used carefully, as it bypasses TypeScript’s type checking.

---

### **7. Tuple Types**

TypeScript also supports **tuples**, which are fixed-size arrays where each element can have a different type.

```ts
let person: [string, number] = ["Alice", 25]; // A tuple with a string and a number
console.log(person[0]); // "Alice"
console.log(person[1]); // 25
```

You can even define arrays of tuples:

```ts
let people: [string, number][] = [
  ["Alice", 25],
  ["Bob", 30]
];
```

---

### **8. Array Index Signatures**

In some cases, you may want to define an array where the indices are numbers, but the values could be any valid type.

```ts
let array: { [index: number]: string } = ["apple", "banana", "cherry"];
console.log(array[0]); // "apple"
```

---

### **9. Read-only Arrays**

If you want to create an array that cannot be modified (immutable), you can use the `readonly` modifier.

```ts
let numbers: readonly number[] = [1, 2, 3];

// The following will result in an error:
// numbers.push(4); // Error: Property 'push' does not exist on type 'readonly number[]'
```

Alternatively, you can define a `readonly` tuple:

```ts
let point: readonly [number, number] = [0, 0];
// point[0] = 10; // Error: Index signature in type 'readonly [number, number]' only permits reading
```

---

### **Summary**

- TypeScript arrays can be defined using `type[]` or `Array<type>`.
- You can create arrays with mixed types using union types: `(string | number)[]`.
- TypeScript supports multidimensional arrays.
- Built-in methods like `map()`, `forEach()`, `filter()`, and `reduce()` provide easy ways to manipulate arrays.
- Array destructuring and the rest operator make it easy to work with array values.
- Type assertions can be used when you need to bypass TypeScript’s type checks.
- **Tuples** allow you to create arrays with fixed sizes and different types for each element.




In TypeScript, the `string` type is used to represent sequences of characters. It is one of the primitive types, and like JavaScript, it is used to store text data. TypeScript provides several ways to work with `string` types, including string literals, string methods, and more advanced features like template literals and string manipulation.

Let’s dive deep into strings in TypeScript:

### **1. Declaring Strings**

You can declare a string variable in TypeScript just like in JavaScript, using `string` type annotation.

#### **1.1 Declaring a String Variable**

```ts
let name: string = "Alice";
```

Here, the variable `name` is of type `string`, and it is assigned the value `"Alice"`.

#### **1.2 String Initialization**

You can initialize a string with either single quotes (`'`), double quotes (`"`), or backticks (``` ` ```):

```ts
let greeting1: string = 'Hello';
let greeting2: string = "World";
let greeting3: string = `Hello, ${name}!`; // Template string
```

### **2. String Template Literals**

In TypeScript, template literals (or template strings) allow for embedding expressions inside strings. This is done using backticks (`` ` ``).

#### **2.1 Basic Template Literals**

```ts
let name: string = "Alice";
let message: string = `Hello, ${name}!`; // Template string with variable
console.log(message); // Outputs: Hello, Alice!
```

#### **2.2 Multi-line Strings**

Template literals also allow multi-line strings, which is useful for formatting strings that span multiple lines.

```ts
let multilineString: string = `
  This is a multi-line string.
  It can span across multiple lines.
`;
console.log(multilineString);
```

#### **2.3 Expression Substitution**

You can insert any expression inside `${}` in template literals:

```ts
let a: number = 10;
let b: number = 20;
let sum: string = `The sum of ${a} and ${b} is ${a + b}.`;
console.log(sum); // Outputs: The sum of 10 and 20 is 30.
```

### **3. String Methods**

TypeScript provides all the JavaScript string methods, allowing you to manipulate and work with strings efficiently.

#### **3.1 String Length**

You can get the length of a string using the `.length` property:

```ts
let str: string = "Hello, World!";
console.log(str.length); // 13
```

#### **3.2 String Methods**

Here are some common string methods in TypeScript:

- **`.toUpperCase()`** – Converts a string to uppercase.
  
  ```ts
  let str: string = "hello";
  console.log(str.toUpperCase()); // "HELLO"
  ```

- **`.toLowerCase()`** – Converts a string to lowercase.
  
  ```ts
  let str: string = "HELLO";
  console.log(str.toLowerCase()); // "hello"
  ```

- **`.trim()`** – Removes whitespace from both ends of the string.
  
  ```ts
  let str: string = "   hello   ";
  console.log(str.trim()); // "hello"
  ```

- **`.substring(start, end)`** – Returns a part of the string between two indexes.
  
  ```ts
  let str: string = "Hello, World!";
  console.log(str.substring(0, 5)); // "Hello"
  ```

- **`.slice(start, end)`** – Similar to `.substring()`, but allows negative indexing.
  
  ```ts
  let str: string = "Hello, World!";
  console.log(str.slice(0, 5)); // "Hello"
  console.log(str.slice(-6)); // "World!"
  ```

- **`.indexOf(searchValue)`** – Returns the index of the first occurrence of a substring or `-1` if not found.
  
  ```ts
  let str: string = "Hello, World!";
  console.log(str.indexOf("World")); // 7
  ```

- **`.replace(searchValue, newValue)`** – Replaces the first occurrence of a substring with another string.
  
  ```ts
  let str: string = "Hello, World!";
  console.log(str.replace("World", "TypeScript")); // "Hello, TypeScript!"
  ```

- **`.split(separator)`** – Splits a string into an array of substrings based on the separator.
  
  ```ts
  let str: string = "apple,banana,grape";
  let fruits: string[] = str.split(",");
  console.log(fruits); // ["apple", "banana", "grape"]
  ```

#### **3.3 Template Literal with String Interpolation**

Another advantage of template literals is the ability to insert dynamic values or expressions directly within strings. You can also use complex expressions:

```ts
let x: number = 10;
let y: number = 20;
let result: string = `The result of ${x} + ${y} is ${x + y}.`;
console.log(result); // "The result of 10 + 20 is 30."
```

### **4. String Indexing**

TypeScript allows you to access the characters of a string using the index (similar to arrays). However, it will return a `string` type.

```ts
let str: string = "Hello, TypeScript!";
console.log(str[0]); // "H"
console.log(str[7]); // "T"
```

Note that string indexing in TypeScript is zero-based (the first character has index 0).

### **5. TypeScript String Literal Types**

TypeScript allows you to define string literals, which are types that represent specific string values rather than a general `string` type. This is particularly useful for defining enums or specific values.

#### **5.1 Defining String Literal Types**

```ts
let greeting: "hello" | "hi" = "hello"; // Only "hello" or "hi" are allowed.
greeting = "hi"; // Valid
greeting = "bye"; // Error: Type '"bye"' is not assignable to type '"hello" | "hi"'.
```

#### **5.2 Using String Literals with Enums**

```ts
enum Status {
  Success = "success",
  Error = "error"
}

let currentStatus: Status = Status.Success;
console.log(currentStatus); // "success"
```

### **6. String Interpolation with Functions**

You can also use string interpolation with function calls:

```ts
function greet(name: string): string {
  return `Hello, ${name}! Welcome to TypeScript.`;
}

let message = greet("Alice");
console.log(message); // "Hello, Alice! Welcome to TypeScript."
```

### **7. String Manipulation with Regular Expressions**

You can perform pattern matching and string manipulations using regular expressions in TypeScript, just like in JavaScript.

```ts
let text: string = "Hello, TypeScript!";
let regex: RegExp = /TypeScript/;

console.log(regex.test(text)); // true
console.log(text.replace(regex, "JavaScript")); // "Hello, JavaScript!"
```

---

### **8. String Type Inference**

TypeScript automatically infers that a variable is of type `string` when you assign it a string value, so explicit type annotations are not always required.

```ts
let greeting = "Hello, World!"; // Inferred as string
```

### **9. Concatenating Strings**

You can concatenate strings in TypeScript using both the `+` operator and template literals.

#### **9.1 Using the `+` Operator:**

```ts
let name: string = "Alice";
let message: string = "Hello, " + name + "!";
console.log(message); // "Hello, Alice!"
```

#### **9.2 Using Template Literals:**

```ts
let name: string = "Alice";
let message: string = `Hello, ${name}!`;
console.log(message); // "Hello, Alice!"
```

---

### **Summary**

- **Basic Declaration:** You can declare strings using `string` type annotations or type inference.
- **Template Literals:** Template strings (backticks) are used for interpolation, multi-line strings, and expression embedding.
- **Common Methods:** Methods like `.toUpperCase()`, `.trim()`, `.split()`, and `.indexOf()` are available to manipulate strings.
- **String Literals:** TypeScript allows specific string values using string literal types.
- **String Manipulation:** You can perform complex string manipulations, including regex matching, indexing, and concatenation.

TypeScript strings are quite similar to JavaScript strings but with added type safety. You can utilize all standard string methods, along with TypeScript's powerful type system, to build reliable and maintainable code.

In TypeScript, **objects** are used to store collections of data and more complex entities. Unlike primitive types like `string` or `number`, objects can contain multiple values and even other objects or functions. TypeScript allows you to define objects with specific types, ensuring that you handle data correctly.

Let’s dive deeper into **objects in TypeScript**:

### **1. Defining Objects**

Objects in TypeScript can be defined in various ways, such as using explicit types, interfaces, or type aliases.

#### **1.1 Using Type Annotations**

You can define an object using a specific type structure (key-value pairs) using the following syntax:

```ts
let person: { name: string; age: number } = {
  name: "Alice",
  age: 30
};
```

Here, the `person` object has two properties:
- `name` of type `string`
- `age` of type `number`

#### **1.2 Optional Properties**

You can make object properties optional using the `?` modifier. Optional properties are not required during initialization.

```ts
let person: { name: string; age?: number } = {
  name: "Alice"
};

let person2: { name: string; age?: number } = {
  name: "Bob",
  age: 25
};
```

In this example, `age` is optional, so it can be omitted when defining the object.

#### **1.3 Readonly Properties**

You can make properties of an object `readonly`, which prevents them from being modified after initialization.

```ts
let person: { readonly name: string; age: number } = {
  name: "Alice",
  age: 30
};

person.age = 31; // This is allowed
person.name = "Bob"; // Error: Cannot assign to 'name' because it is a read-only property.
```

---

### **2. Interfaces and Objects**

Using **interfaces** in TypeScript is a more powerful way to define the structure of objects. Interfaces allow you to define reusable object shapes and enforce consistent structures across different parts of your application.

#### **2.1 Defining an Object Shape with an Interface**

```ts
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Alice",
  age: 30
};
```

Here, the `Person` interface defines the structure for any object that is supposed to represent a person, and the `person` object is validated against this structure.

#### **2.2 Optional Properties in Interfaces**

You can also define optional properties in an interface using the `?` syntax.

```ts
interface Person {
  name: string;
  age?: number; // Optional property
}

let person1: Person = { name: "Alice" };
let person2: Person = { name: "Bob", age: 25 };
```

#### **2.3 Readonly Properties in Interfaces**

Similar to object type annotations, you can define readonly properties within an interface.

```ts
interface Person {
  readonly name: string;
  age: number;
}

let person: Person = { name: "Alice", age: 30 };

person.age = 31; // Valid
person.name = "Bob"; // Error: Cannot assign to 'name' because it is a read-only property.
```

#### **2.4 Extending Interfaces**

You can extend an interface to create a new interface that includes the properties of the original interface, and you can add more properties or modify existing ones.

```ts
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  jobTitle: string;
}

let employee: Employee = {
  name: "Alice",
  age: 30,
  jobTitle: "Developer"
};
```

Here, the `Employee` interface extends `Person` and adds a new property, `jobTitle`.

---

### **3. Type Aliases for Objects**

You can also use **type aliases** to define objects with a specific structure. Type aliases are similar to interfaces but are more flexible and can be used for union types, intersections, and other advanced type combinations.

#### **3.1 Defining an Object with a Type Alias**

```ts
type Person = {
  name: string;
  age: number;
};

let person: Person = {
  name: "Alice",
  age: 30
};
```

#### **3.2 Type Aliases with Optional and Readonly Properties**

Just like with interfaces, you can define optional and readonly properties with type aliases:

```ts
type Person = {
  name: string;
  age?: number;
  readonly city: string;
};

let person: Person = {
  name: "Alice",
  city: "New York"
};

person.city = "Los Angeles"; // Error: Cannot assign to 'city' because it is a read-only property.
```

---

### **4. Nested Objects**

You can define objects within objects in TypeScript, and TypeScript will infer types recursively.

#### **4.1 Simple Nested Objects**

```ts
let person: {
  name: string;
  address: {
    street: string;
    city: string;
  };
} = {
  name: "Alice",
  address: {
    street: "123 Main St",
    city: "New York"
  }
};
```

#### **4.2 Nested Objects with Interfaces**

You can also use interfaces for nested objects:

```ts
interface Address {
  street: string;
  city: string;
}

interface Person {
  name: string;
  address: Address;
}

let person: Person = {
  name: "Alice",
  address: {
    street: "123 Main St",
    city: "New York"
  }
};
```

---

### **5. Destructuring Objects**

TypeScript supports destructuring syntax, which allows you to extract values from objects and assign them to variables in a more concise way.

```ts
let person = { name: "Alice", age: 30 };

// Destructuring
let { name, age }: { name: string; age: number } = person;

console.log(name); // "Alice"
console.log(age);  // 30
```

#### **5.1 Destructuring with Default Values**

You can also provide default values while destructuring objects.

```ts
let person = { name: "Alice" };

// Destructuring with default value for age
let { name, age = 25 }: { name: string; age: number } = person;

console.log(name); // "Alice"
console.log(age);  // 25 (default value)
```

#### **5.2 Renaming Destructured Variables**

You can rename the variables during destructuring.

```ts
let person = { name: "Alice", age: 30 };

// Renaming while destructuring
let { name: fullName, age: yearsOld }: { name: string; age: number } = person;

console.log(fullName);  // "Alice"
console.log(yearsOld);  // 30
```

---

### **6. Object Spread Operator**

You can use the object spread operator (`...`) to create a shallow copy of an object or to merge multiple objects.

```ts
let person = { name: "Alice", age: 30 };

// Copying an object
let personCopy = { ...person };
console.log(personCopy); // { name: "Alice", age: 30 }

// Merging objects
let additionalInfo = { jobTitle: "Developer" };
let mergedPerson = { ...person, ...additionalInfo };
console.log(mergedPerson); // { name: "Alice", age: 30, jobTitle: "Developer" }
```

---

### **7. Index Signature**

If you don’t know the exact properties of an object ahead of time but know they will have a specific type, you can use **index signatures**.

```ts
interface Person {
  name: string;
  [key: string]: string | number; // Index signature
}

let person: Person = {
  name: "Alice",
  age: 30,
  jobTitle: "Developer"
};
```

In this example, the `Person` interface has a property `name` and can have any other string-named properties whose values are either a `string` or `number`.

---

### **8. Type Inference with Objects**

TypeScript can infer the types of properties in objects if the object is initialized with values. You don’t need to explicitly define the type if TypeScript can automatically infer it.

```ts
let person = { name: "Alice", age: 30 }; // TypeScript infers { name: string, age: number }

console.log(person.name); // "Alice"
console.log(person.age);  // 30
```

---

### **Summary**

- **Defining Objects:** Use `{}` for inline object definitions or use interfaces/type aliases for reusable object structures.
- **Optional & Readonly Properties:** Use `?` for optional properties and `readonly` to make properties immutable.
- **Nested Objects:** TypeScript supports nested objects, and you can use interfaces to define them.
- **Destructuring:** Destructure objects to extract values into variables easily.
- **Object Spread:** Use the spread operator (`...`) to copy or merge objects.
- **Index Signatures:** Use index signatures when object properties are dynamic but have a specific type.
- **Type Inference:** TypeScript can infer types based on object initialization, making it easy to write concise code.

Objects are a fundamental part of TypeScript, and understanding how to work with them effectively can make your code more robust and readable. Let me know if you'd like more examples or have specific use cases you'd like to explore!

In TypeScript, **tuples** are a special kind of array that allows you to store a fixed number of elements of different types. Unlike arrays, which are generally homogeneous (all elements of the same type), tuples allow you to store heterogeneous elements. They are particularly useful when you want to represent a set of related but different types in a specific order.

### **1. Defining Tuples**

You define a tuple by using square brackets (`[]`) and specifying the types of the elements at specific positions.

#### **1.1 Basic Tuple Definition**

```ts
let tuple: [string, number] = ["Alice", 30];
```

In this example, `tuple` is an array with two elements:
- The first element is a `string` (`"Alice"`)
- The second element is a `number` (`30`)

The type of the tuple is `[string, number]`, which means the first element must always be a string, and the second element must always be a number.

#### **1.2 Accessing Tuple Elements**

You access elements of a tuple using their index, just like arrays:

```ts
let tuple: [string, number] = ["Alice", 30];

console.log(tuple[0]); // "Alice"
console.log(tuple[1]); // 30
```

### **2. Tuple with Mixed Types**

Tuples can hold elements of different types, making them ideal for representing data with mixed types, such as coordinates or a pair of related values.

```ts
let coordinate: [number, number] = [10, 20];
let nameAndAge: [string, number] = ["Bob", 25];
```

### **3. Tuples with Optional Elements**

You can define tuples where some elements are optional. Use `?` to indicate an optional element in the tuple.

```ts
let tuple: [string, number?, boolean?] = ["Alice", 30];
let tuple2: [string, number?, boolean?] = ["Bob", 25, true];
```

In this case:
- The second and third elements (`number` and `boolean`) are optional, meaning the tuple can have just one or two elements.
  
### **4. Tuple with Fixed Length**

Tuples in TypeScript are **fixed-length arrays**. Once you define the number of elements in the tuple, that number cannot be changed. For example:

```ts
let tuple: [string, number] = ["Alice", 30];
tuple.push("Extra"); // Error: Tuple type '[string, number]' of length '2' has no element at index '2'.
```

### **5. Tuple with Different Lengths**

Tuples can have more than two elements with different types:

```ts
let person: [string, number, boolean] = ["Alice", 30, true];
```

Here, `person` is a tuple with three elements:
- `string` (name)
- `number` (age)
- `boolean` (isActive)

### **6. Using Tuples for Returning Multiple Values from Functions**

Tuples are often used to return multiple values from functions, especially when returning related values of different types.

#### **6.1 Function Returning a Tuple**

```ts
function getPersonInfo(): [string, number] {
  return ["Alice", 30];
}

let person = getPersonInfo();
console.log(person[0]); // "Alice"
console.log(person[1]); // 30
```

In this example, the function `getPersonInfo` returns a tuple containing a `string` (name) and a `number` (age).

#### **6.2 Destructuring a Tuple**

You can also destructure tuples directly into variables:

```ts
let [name, age] = getPersonInfo();
console.log(name); // "Alice"
console.log(age);  // 30
```

### **7. Tuple Type Inference**

TypeScript can infer the types of a tuple based on the values you assign to it. If you don't explicitly define the type, TypeScript will infer it based on the provided values.

```ts
let tuple = ["Alice", 30]; // Inferred type: [string, number]
```

However, it is often a good practice to explicitly define the tuple type to ensure type safety.

### **8. Tuple with Type Aliases**

You can also define tuple types using **type aliases** for easier reuse:

```ts
type PersonInfo = [string, number];

let person: PersonInfo = ["Alice", 30];
let anotherPerson: PersonInfo = ["Bob", 25];
```

Here, `PersonInfo` is a type alias for a tuple of `[string, number]`, making it reusable across your application.

### **9. Tuple with Rest Elements**

Starting from TypeScript 4.0, you can use **rest elements** in tuples, which allows you to define tuples with a fixed number of initial elements, followed by a variable number of additional elements.

```ts
let tuple: [string, ...number[]] = ["Alice", 30, 25, 40];
```

In this case, the tuple has a fixed first element of type `string`, and the remaining elements are of type `number`.

### **10. Tuples in Arrays**

You can also create arrays of tuples, each with its own specific type structure:

```ts
let people: [string, number][] = [
  ["Alice", 30],
  ["Bob", 25]
];
```

This defines an array of tuples, where each tuple contains a `string` (name) and a `number` (age).

---

### **Summary**

- **Defining Tuples:** Use square brackets `[]` to define a tuple, specifying the types of each element in order.
- **Accessing Elements:** You can access tuple elements using their index.
- **Optional Properties:** Tuple elements can be made optional with the `?` modifier.
- **Fixed Length:** Tuples have a fixed length, which cannot be changed after initialization.
- **Multiple Values from Functions:** Tuples are great for returning multiple values of different types from functions.
- **Destructuring:** Tuples can be destructured into individual variables.
- **Rest Elements:** You can use rest elements (`...`) to allow a tuple to have a fixed number of elements, followed by any number of additional elements.

Tuples are useful for grouping together multiple values of different types, especially when those values are closely related but don't necessarily belong in an array. They add a level of type safety and flexibility to your data structures in TypeScript. Let me know if you need further clarification or examples!



In TypeScript, **tuples** are a special kind of array that allows you to store a fixed number of elements of different types. Unlike arrays, which are generally homogeneous (all elements of the same type), tuples allow you to store heterogeneous elements. They are particularly useful when you want to represent a set of related but different types in a specific order.

### **1. Defining Tuples**

You define a tuple by using square brackets (`[]`) and specifying the types of the elements at specific positions.

#### **1.1 Basic Tuple Definition**

```ts
let tuple: [string, number] = ["Alice", 30];
```

In this example, `tuple` is an array with two elements:
- The first element is a `string` (`"Alice"`)
- The second element is a `number` (`30`)

The type of the tuple is `[string, number]`, which means the first element must always be a string, and the second element must always be a number.

#### **1.2 Accessing Tuple Elements**

You access elements of a tuple using their index, just like arrays:

```ts
let tuple: [string, number] = ["Alice", 30];

console.log(tuple[0]); // "Alice"
console.log(tuple[1]); // 30
```

### **2. Tuple with Mixed Types**

Tuples can hold elements of different types, making them ideal for representing data with mixed types, such as coordinates or a pair of related values.

```ts
let coordinate: [number, number] = [10, 20];
let nameAndAge: [string, number] = ["Bob", 25];
```

### **3. Tuples with Optional Elements**

You can define tuples where some elements are optional. Use `?` to indicate an optional element in the tuple.

```ts
let tuple: [string, number?, boolean?] = ["Alice", 30];
let tuple2: [string, number?, boolean?] = ["Bob", 25, true];
```

In this case:
- The second and third elements (`number` and `boolean`) are optional, meaning the tuple can have just one or two elements.
  
### **4. Tuple with Fixed Length**

Tuples in TypeScript are **fixed-length arrays**. Once you define the number of elements in the tuple, that number cannot be changed. For example:

```ts
let tuple: [string, number] = ["Alice", 30];
tuple.push("Extra"); // Error: Tuple type '[string, number]' of length '2' has no element at index '2'.
```

### **5. Tuple with Different Lengths**

Tuples can have more than two elements with different types:

```ts
let person: [string, number, boolean] = ["Alice", 30, true];
```

Here, `person` is a tuple with three elements:
- `string` (name)
- `number` (age)
- `boolean` (isActive)

### **6. Using Tuples for Returning Multiple Values from Functions**

Tuples are often used to return multiple values from functions, especially when returning related values of different types.

#### **6.1 Function Returning a Tuple**

```ts
function getPersonInfo(): [string, number] {
  return ["Alice", 30];
}

let person = getPersonInfo();
console.log(person[0]); // "Alice"
console.log(person[1]); // 30
```

In this example, the function `getPersonInfo` returns a tuple containing a `string` (name) and a `number` (age).

#### **6.2 Destructuring a Tuple**

You can also destructure tuples directly into variables:

```ts
let [name, age] = getPersonInfo();
console.log(name); // "Alice"
console.log(age);  // 30
```

### **7. Tuple Type Inference**

TypeScript can infer the types of a tuple based on the values you assign to it. If you don't explicitly define the type, TypeScript will infer it based on the provided values.

```ts
let tuple = ["Alice", 30]; // Inferred type: [string, number]
```

However, it is often a good practice to explicitly define the tuple type to ensure type safety.

### **8. Tuple with Type Aliases**

You can also define tuple types using **type aliases** for easier reuse:

```ts
type PersonInfo = [string, number];

let person: PersonInfo = ["Alice", 30];
let anotherPerson: PersonInfo = ["Bob", 25];
```

Here, `PersonInfo` is a type alias for a tuple of `[string, number]`, making it reusable across your application.

### **9. Tuple with Rest Elements**

Starting from TypeScript 4.0, you can use **rest elements** in tuples, which allows you to define tuples with a fixed number of initial elements, followed by a variable number of additional elements.

```ts
let tuple: [string, ...number[]] = ["Alice", 30, 25, 40];
```

In this case, the tuple has a fixed first element of type `string`, and the remaining elements are of type `number`.

### **10. Tuples in Arrays**

You can also create arrays of tuples, each with its own specific type structure:

```ts
let people: [string, number][] = [
  ["Alice", 30],
  ["Bob", 25]
];
```

This defines an array of tuples, where each tuple contains a `string` (name) and a `number` (age).

---

### **Summary**

- **Defining Tuples:** Use square brackets `[]` to define a tuple, specifying the types of each element in order.
- **Accessing Elements:** You can access tuple elements using their index.
- **Optional Properties:** Tuple elements can be made optional with the `?` modifier.
- **Fixed Length:** Tuples have a fixed length, which cannot be changed after initialization.
- **Multiple Values from Functions:** Tuples are great for returning multiple values of different types from functions.
- **Destructuring:** Tuples can be destructured into individual variables.
- **Rest Elements:** You can use rest elements (`...`) to allow a tuple to have a fixed number of elements, followed by any number of additional elements.

Tuples are useful for grouping together multiple values of different types, especially when those values are closely related but don't necessarily belong in an array. They add a level of type safety and flexibility to your data structures in TypeScript. Let me know if you need further clarification or examples!




In TypeScript, **type aliases** and **interfaces** are both ways to define custom types, and they share some similarities, but there are key differences in how and when they should be used. Let’s dive into both concepts and explore their differences, similarities, and use cases.

### **1. Type Aliases**

A **type alias** is used to give a name to a specific type. You can use type aliases to create complex types, including object types, union types, tuple types, and more. Type aliases are generally more flexible than interfaces because they allow more complex type expressions, like unions and intersections.

#### **1.1 Basic Syntax**

You define a type alias using the `type` keyword:

```ts
type Person = {
  name: string;
  age: number;
};

let person: Person = {
  name: "Alice",
  age: 30
};
```

Here, `Person` is a type alias that defines an object type with two properties: `name` (a `string`) and `age` (a `number`).

#### **1.2 Using Type Aliases for Unions and Intersections**

Type aliases allow you to define more complex types, such as union and intersection types:

- **Union types** represent a value that can be one of several types.

```ts
type ID = string | number; // ID can be either a string or a number

let userId: ID = 123;
userId = "abc123"; // Valid
```

- **Intersection types** combine multiple types into one.

```ts
type Name = { name: string };
type Age = { age: number };

type Person = Name & Age;

let person: Person = { name: "Alice", age: 30 }; // Combines Name and Age
```

#### **1.3 Type Aliases for Tuples and Arrays**

Type aliases can also be used for defining tuple and array types.

```ts
type Coordinate = [number, number]; // Tuple type
let point: Coordinate = [10, 20]; // Tuple with two numbers

type StringArray = string[]; // Array type
let words: StringArray = ["hello", "world"];
```

#### **1.4 Type Aliases for Function Types**

You can define function types using type aliases:

```ts
type Greet = (name: string) => string;

let greet: Greet = (name) => `Hello, ${name}`;
```

---

### **2. Interfaces**

An **interface** is a way to define the structure of an object or class. Interfaces are used to describe the shape of objects and are generally used for objects with a fixed structure. Interfaces are often preferred when dealing with object-oriented designs or when defining contracts for objects, especially when working with classes.

#### **2.1 Basic Syntax**

You define an interface using the `interface` keyword:

```ts
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Alice",
  age: 30
};
```

Here, `Person` is an interface that defines the shape of an object with two properties: `name` (a `string`) and `age` (a `number`).

#### **2.2 Extending Interfaces**

Interfaces can extend other interfaces, meaning they can inherit the properties of other interfaces and add new properties.

```ts
interface Employee extends Person {
  jobTitle: string;
}

let employee: Employee = {
  name: "Alice",
  age: 30,
  jobTitle: "Developer"
};
```

In this example, the `Employee` interface extends the `Person` interface, meaning an `Employee` object must also have `name` and `age` properties, in addition to the `jobTitle` property.

#### **2.3 Implementing Interfaces with Classes**

Interfaces can be used to define the shape of a class. When a class implements an interface, it must define all the properties and methods specified by that interface.

```ts
interface Greetable {
  greet(): void;
}

class Person implements Greetable {
  constructor(public name: string) {}
  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

let person = new Person("Alice");
person.greet(); // "Hello, Alice"
```

#### **2.4 Optional Properties and Readonly Properties**

You can define optional properties using the `?` syntax and `readonly` properties in interfaces:

```ts
interface Person {
  name: string;
  age?: number; // Optional property
  readonly city: string; // Readonly property
}

let person: Person = { name: "Alice", city: "New York" };
person.city = "Los Angeles"; // Error: Cannot assign to 'city' because it is a read-only property.
```

---

### **3. Key Differences Between Type Aliases and Interfaces**

While both **type aliases** and **interfaces** serve the purpose of defining types, there are some key differences between them:

#### **3.1 Extending and Implementing**

- **Interfaces** can be **extended** by other interfaces using the `extends` keyword, and they can be **implemented** by classes using the `implements` keyword. This is particularly useful in object-oriented programming and class design.
  
- **Type aliases** cannot be **implemented** by classes, but they can create complex types by using unions, intersections, and other advanced type features.

```ts
// Extending interfaces
interface Person {
  name: string;
}

interface Employee extends Person {
  jobTitle: string;
}

// Type aliases cannot be extended in the same way
type Person = { name: string };
// Error: Type alias 'Person' cannot be extended.
type Employee = Person & { jobTitle: string };
```

#### **3.2 Declaration Merging**

- **Interfaces** support **declaration merging**, meaning that if you declare an interface with the same name multiple times, TypeScript will automatically merge those declarations into a single interface.

```ts
interface Person {
  name: string;
}

interface Person {
  age: number;
}

let person: Person = { name: "Alice", age: 30 }; // Merged interface
```

- **Type aliases** do not support declaration merging. If you try to declare a type alias with the same name twice, TypeScript will throw an error.

```ts
type Person = { name: string };
type Person = { age: number }; // Error: Duplicate identifier 'Person'.
```

#### **3.3 Type Aliases are More Flexible**

Type aliases are more flexible and can represent more complex types, such as union types, intersection types, and tuples.

```ts
type ID = string | number; // Union type
type Point = [number, number]; // Tuple type
type Person = { name: string } & { age: number }; // Intersection type
```

Interfaces are more restrictive in this regard, as they are designed primarily to define object shapes.

---

### **4. When to Use Type Aliases vs Interfaces**

- **Use Interfaces** when:
  - You are defining the shape of an object, especially when you plan to extend or implement it.
  - You are working with classes and want to ensure that the class implements a specific contract.
  - You want to take advantage of declaration merging, which is useful for extending third-party types or augmenting existing types.

- **Use Type Aliases** when:
  - You need to create more complex types, such as unions, intersections, or tuples.
  - You want to create an alias for a primitive type or function type.
  - You don't need to take advantage of declaration merging.

### **5. Conclusion**

Both **type aliases** and **interfaces** are essential features of TypeScript, and they are often used in different scenarios. 

- **Interfaces** are great for defining object shapes and creating reusable contracts, especially for classes and inheritance.
- **Type aliases** are ideal when you need more flexibility, such as defining union types, intersection types, and tuples.

In general, it is recommended to use **interfaces** when working with object shapes and **type aliases** when working with more advanced types or complex combinations.



In TypeScript, **type aliases** and **interfaces** are both ways to define custom types, and they share some similarities, but there are key differences in how and when they should be used. Let’s dive into both concepts and explore their differences, similarities, and use cases.

### **1. Type Aliases**

A **type alias** is used to give a name to a specific type. You can use type aliases to create complex types, including object types, union types, tuple types, and more. Type aliases are generally more flexible than interfaces because they allow more complex type expressions, like unions and intersections.

#### **1.1 Basic Syntax**

You define a type alias using the `type` keyword:

```ts
type Person = {
  name: string;
  age: number;
};

let person: Person = {
  name: "Alice",
  age: 30
};
```

Here, `Person` is a type alias that defines an object type with two properties: `name` (a `string`) and `age` (a `number`).

#### **1.2 Using Type Aliases for Unions and Intersections**

Type aliases allow you to define more complex types, such as union and intersection types:

- **Union types** represent a value that can be one of several types.

```ts
type ID = string | number; // ID can be either a string or a number

let userId: ID = 123;
userId = "abc123"; // Valid
```

- **Intersection types** combine multiple types into one.

```ts
type Name = { name: string };
type Age = { age: number };

type Person = Name & Age;

let person: Person = { name: "Alice", age: 30 }; // Combines Name and Age
```

#### **1.3 Type Aliases for Tuples and Arrays**

Type aliases can also be used for defining tuple and array types.

```ts
type Coordinate = [number, number]; // Tuple type
let point: Coordinate = [10, 20]; // Tuple with two numbers

type StringArray = string[]; // Array type
let words: StringArray = ["hello", "world"];
```

#### **1.4 Type Aliases for Function Types**

You can define function types using type aliases:

```ts
type Greet = (name: string) => string;

let greet: Greet = (name) => `Hello, ${name}`;
```

---

### **2. Interfaces**

An **interface** is a way to define the structure of an object or class. Interfaces are used to describe the shape of objects and are generally used for objects with a fixed structure. Interfaces are often preferred when dealing with object-oriented designs or when defining contracts for objects, especially when working with classes.

#### **2.1 Basic Syntax**

You define an interface using the `interface` keyword:

```ts
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Alice",
  age: 30
};
```

Here, `Person` is an interface that defines the shape of an object with two properties: `name` (a `string`) and `age` (a `number`).

#### **2.2 Extending Interfaces**

Interfaces can extend other interfaces, meaning they can inherit the properties of other interfaces and add new properties.

```ts
interface Employee extends Person {
  jobTitle: string;
}

let employee: Employee = {
  name: "Alice",
  age: 30,
  jobTitle: "Developer"
};
```

In this example, the `Employee` interface extends the `Person` interface, meaning an `Employee` object must also have `name` and `age` properties, in addition to the `jobTitle` property.

#### **2.3 Implementing Interfaces with Classes**

Interfaces can be used to define the shape of a class. When a class implements an interface, it must define all the properties and methods specified by that interface.

```ts
interface Greetable {
  greet(): void;
}

class Person implements Greetable {
  constructor(public name: string) {}
  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

let person = new Person("Alice");
person.greet(); // "Hello, Alice"
```

#### **2.4 Optional Properties and Readonly Properties**

You can define optional properties using the `?` syntax and `readonly` properties in interfaces:

```ts
interface Person {
  name: string;
  age?: number; // Optional property
  readonly city: string; // Readonly property
}

let person: Person = { name: "Alice", city: "New York" };
person.city = "Los Angeles"; // Error: Cannot assign to 'city' because it is a read-only property.
```

---

### **3. Key Differences Between Type Aliases and Interfaces**

While both **type aliases** and **interfaces** serve the purpose of defining types, there are some key differences between them:

#### **3.1 Extending and Implementing**

- **Interfaces** can be **extended** by other interfaces using the `extends` keyword, and they can be **implemented** by classes using the `implements` keyword. This is particularly useful in object-oriented programming and class design.
  
- **Type aliases** cannot be **implemented** by classes, but they can create complex types by using unions, intersections, and other advanced type features.

```ts
// Extending interfaces
interface Person {
  name: string;
}

interface Employee extends Person {
  jobTitle: string;
}

// Type aliases cannot be extended in the same way
type Person = { name: string };
// Error: Type alias 'Person' cannot be extended.
type Employee = Person & { jobTitle: string };
```

#### **3.2 Declaration Merging**

- **Interfaces** support **declaration merging**, meaning that if you declare an interface with the same name multiple times, TypeScript will automatically merge those declarations into a single interface.

```ts
interface Person {
  name: string;
}

interface Person {
  age: number;
}

let person: Person = { name: "Alice", age: 30 }; // Merged interface
```

- **Type aliases** do not support declaration merging. If you try to declare a type alias with the same name twice, TypeScript will throw an error.

```ts
type Person = { name: string };
type Person = { age: number }; // Error: Duplicate identifier 'Person'.
```

#### **3.3 Type Aliases are More Flexible**

Type aliases are more flexible and can represent more complex types, such as union types, intersection types, and tuples.

```ts
type ID = string | number; // Union type
type Point = [number, number]; // Tuple type
type Person = { name: string } & { age: number }; // Intersection type
```

Interfaces are more restrictive in this regard, as they are designed primarily to define object shapes.

---

### **4. When to Use Type Aliases vs Interfaces**

- **Use Interfaces** when:
  - You are defining the shape of an object, especially when you plan to extend or implement it.
  - You are working with classes and want to ensure that the class implements a specific contract.
  - You want to take advantage of declaration merging, which is useful for extending third-party types or augmenting existing types.

- **Use Type Aliases** when:
  - You need to create more complex types, such as unions, intersections, or tuples.
  - You want to create an alias for a primitive type or function type.
  - You don't need to take advantage of declaration merging.

### **5. Conclusion**

Both **type aliases** and **interfaces** are essential features of TypeScript, and they are often used in different scenarios. 

- **Interfaces** are great for defining object shapes and creating reusable contracts, especially for classes and inheritance.
- **Type aliases** are ideal when you need more flexibility, such as defining union types, intersection types, and tuples.

In general, it is recommended to use **interfaces** when working with object shapes and **type aliases** when working with more advanced types or complex combinations.




In TypeScript, **union types** allow you to define a type that can accept multiple types. A value of a union type can be one of several types, and TypeScript will enforce that the value is one of those types. Union types are represented using the `|` (pipe) operator.

### **1. Syntax**

The syntax for a union type is simple: you list the possible types separated by the `|` operator.

```ts
type MyType = Type1 | Type2 | Type3;
```

In this example, `MyType` can be either `Type1`, `Type2`, or `Type3`.

### **2. Basic Example**

Here’s a basic example where a variable can be either a `string` or a `number`:

```ts
let value: string | number;

value = "Hello"; // Valid
value = 42; // Valid
value = true; // Error: 'true' is not assignable to type 'string | number'
```

In this case, `value` can be assigned either a string or a number, but not any other type.

### **3. Union Types with Functions**

Union types are also useful when you want to define a function that accepts different types of arguments:

```ts
function printId(id: string | number) {
  console.log(id);
}

printId("abc123"); // Valid
printId(100); // Valid
printId(true); // Error: Argument of type 'true' is not assignable to parameter of type 'string | number'.
```

Here, the `printId` function can accept either a `string` or a `number` as an argument.

### **4. Using Union Types with Objects**

You can use union types to define objects that can have different shapes. For example, you may have a function that accepts either a `User` object or a `Product` object, each with different properties.

```ts
type User = { name: string, age: number };
type Product = { productName: string, price: number };

function displayDetails(data: User | Product) {
  if ("name" in data) {
    console.log(`User: ${data.name}, Age: ${data.age}`);
  } else {
    console.log(`Product: ${data.productName}, Price: $${data.price}`);
  }
}

displayDetails({ name: "Alice", age: 30 }); // User: Alice, Age: 30
displayDetails({ productName: "Laptop", price: 1000 }); // Product: Laptop, Price: $1000
```

In this example, `data` can either be a `User` object or a `Product` object, and we use type guards (e.g., `"name" in data`) to distinguish between the two.

### **5. Union Types with Arrays**

You can also use union types with arrays. For example, an array that contains either strings or numbers:

```ts
let mixedArray: (string | number)[] = ["Hello", 42, "World"];
console.log(mixedArray);
```

This array can hold both `string` and `number` elements.

### **6. Type Guards with Union Types**

When working with union types, TypeScript doesn’t automatically know which type a variable is at runtime. You can use **type guards** to narrow the type and perform different actions based on the type.

#### **6.1 Using `typeof` for Primitive Types**

For primitive types like `string` and `number`, you can use `typeof` to check the type of the value:

```ts
function printValue(value: string | number) {
  if (typeof value === "string") {
    console.log(`String value: ${value}`);
  } else {
    console.log(`Number value: ${value}`);
  }
}

printValue("Hello"); // String value: Hello
printValue(42); // Number value: 42
```

#### **6.2 Using `in` for Object Types**

For object types, you can use the `in` operator to check if a property exists, which helps distinguish between different types in a union.

```ts
type Dog = { breed: string, bark: () => void };
type Cat = { breed: string, meow: () => void };

function speak(animal: Dog | Cat) {
  if ("bark" in animal) {
    animal.bark(); // Dog-specific method
  } else {
    animal.meow(); // Cat-specific method
  }
}

const dog: Dog = { breed: "Beagle", bark: () => console.log("Woof!") };
const cat: Cat = { breed: "Siamese", meow: () => console.log("Meow!") };

speak(dog); // Woof!
speak(cat); // Meow!
```

In this example, the `speak` function uses the `in` operator to differentiate between `Dog` and `Cat` types, based on the methods they have (`bark` and `meow`).

### **7. Using `null` and `undefined` in Union Types**

You can also include `null` and `undefined` in union types:

```ts
let value: string | null = "Hello";
value = null; // Valid
value = "Goodbye"; // Valid
```

In this example, the variable `value` can either be a `string` or `null`.

### **8. Union Types with Type Aliases**

Union types are often used in conjunction with **type aliases** to create more complex and reusable types.

```ts
type Status = "active" | "inactive" | "pending";

function getStatus(status: Status) {
  return `The status is: ${status}`;
}

console.log(getStatus("active")); // The status is: active
console.log(getStatus("pending")); // The status is: pending
```

In this example, `Status` is a type alias for a union of string literals. The function `getStatus` accepts one of those string values as its argument.

### **9. Combining Union and Intersection Types**

You can combine **union types** with **intersection types** for even more powerful type compositions.

```ts
type Car = { wheels: number, brand: string };
type Boat = { sails: number, brand: string };

type CarBoat = Car & Boat; // Intersection type

let carBoat: CarBoat = { wheels: 4, sails: 2, brand: "Hybrid" };
```

In this case, `CarBoat` is an intersection of `Car` and `Boat`, meaning the object must have the properties of both types (`wheels`, `sails`, and `brand`).

### **10. Union Types with Generics**

Union types can also be used with **generics** to create flexible and reusable types.

```ts
function combine<T extends string | number>(a: T, b: T): T {
  return (a as any) + (b as any);
}

let result1 = combine(10, 20); // 30
let result2 = combine("Hello", " World"); // Hello World
```

In this example, the generic function `combine` accepts either two `string` values or two `number` values and returns the combined result.

---

### **11. Summary**

- **Union types** allow a value to be one of multiple types, using the `|` operator.
- They can be used with primitive types (`string | number`), objects, arrays, and more.
- Type guards (e.g., `typeof`, `in`) help differentiate between union types at runtime.
- Union types are especially useful for functions and data structures where a value can belong to different types.
- **Type aliases** can be used to simplify union types, making them easier to reuse across your application.

In TypeScript, **functions** are a fundamental part of the language and offer strong typing features to help ensure correctness in your code. Functions in TypeScript are similar to JavaScript functions, but with additional type annotations for parameters, return values, and more. Let’s explore how to define and use functions in TypeScript.

### **1. Function Basics**

The basic syntax for defining a function in TypeScript is similar to JavaScript, but you can add type annotations for the parameters and return type.

#### **1.1 Basic Function Definition**

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}

let message = greet("Alice");
console.log(message); // Output: Hello, Alice
```

In this example:
- The function `greet` takes one parameter `name` of type `string`.
- The function returns a `string` type.

#### **1.2 Function with Multiple Parameters**

You can define functions that accept multiple parameters, each with its own type annotation.

```ts
function add(a: number, b: number): number {
  return a + b;
}

let result = add(5, 10);
console.log(result); // Output: 15
```

Here, the function `add` takes two parameters (`a` and `b`), both of type `number`, and returns a `number`.

### **2. Optional and Default Parameters**

TypeScript allows you to specify **optional** parameters and **default** parameters in functions.

#### **2.1 Optional Parameters**

Optional parameters are denoted by a `?` after the parameter name.

```ts
function greet(name: string, age?: number): string {
  if (age) {
    return `Hello, ${name}. You are ${age} years old.`;
  } else {
    return `Hello, ${name}.`;
  }
}

console.log(greet("Alice")); // Hello, Alice.
console.log(greet("Bob", 30)); // Hello, Bob. You are 30 years old.
```

- The `age` parameter is optional, and if not provided, the function will just greet the person by name.

#### **2.2 Default Parameters**

Default parameters have a default value if not provided when the function is called.

```ts
function greet(name: string, age: number = 25): string {
  return `Hello, ${name}. You are ${age} years old.`;
}

console.log(greet("Alice")); // Hello, Alice. You are 25 years old.
console.log(greet("Bob", 30)); // Hello, Bob. You are 30 years old.
```

- Here, `age` defaults to `25` if it is not passed as an argument.

### **3. Function Expressions**

You can also define functions using **function expressions** in TypeScript. This is useful when you want to assign a function to a variable or pass it around as an argument.

#### **3.1 Anonymous Function Expressions**

```ts
const greet = function(name: string): string {
  return `Hello, ${name}`;
};

console.log(greet("Alice")); // Output: Hello, Alice
```

#### **3.2 Arrow Function Expressions**

Arrow functions are a shorthand way to define functions. They also have different behavior for `this`, which is lexically bound.

```ts
const greet = (name: string): string => `Hello, ${name}`;

console.log(greet("Alice")); // Output: Hello, Alice
```

In this case, the function `greet` is an arrow function, which has a concise syntax.

### **4. Function Types**

In TypeScript, you can define the type of a function separately, which is useful when you want to reuse the function type or when you're working with higher-order functions.

#### **4.1 Defining Function Types**

You can define the type of a function using type annotations:

```ts
type GreetFunction = (name: string) => string;

const greet: GreetFunction = (name) => `Hello, ${name}`;

console.log(greet("Alice")); // Output: Hello, Alice
```

Here, `GreetFunction` is a type alias for a function that takes a `string` and returns a `string`.

#### **4.2 Function Type with Multiple Parameters**

```ts
type AddFunction = (a: number, b: number) => number;

const add: AddFunction = (a, b) => a + b;

console.log(add(5, 10)); // Output: 15
```

### **5. Rest Parameters**

TypeScript supports **rest parameters**, which allow you to pass an arbitrary number of arguments into a function.

```ts
function sum(...numbers: number[]): number {
  return numbers.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
console.log(sum(5, 10)); // Output: 15
```

Here, the `...numbers` syntax allows the function to accept any number of `number` arguments.

### **6. `this` in Functions**

In TypeScript, the behavior of `this` in functions can be controlled using the `this` parameter in the function type. This helps ensure that the `this` keyword refers to the correct context in your code.

#### **6.1 Arrow Functions and `this`**

Arrow functions lexically bind `this`, meaning `this` refers to the enclosing scope.

```ts
const person = {
  name: "Alice",
  greet: () => {
    console.log(`Hello, ${this.name}`); // 'this' refers to the global object (in browsers, it's 'window')
  }
};

person.greet(); // Output: Hello, undefined
```

#### **6.2 Regular Functions and `this`**

Regular functions bind `this` to the object that calls the function.

```ts
const person = {
  name: "Alice",
  greet() {
    console.log(`Hello, ${this.name}`); // 'this' refers to the 'person' object
  }
};

person.greet(); // Output: Hello, Alice
```

### **7. Function Overloading**

Function overloading allows you to define multiple function signatures for the same function name, which is useful when the function behaves differently depending on the types or number of arguments passed to it.

```ts
function greet(name: string): string;
function greet(age: number): string;
function greet(value: string | number): string {
  if (typeof value === "string") {
    return `Hello, ${value}`;
  } else {
    return `You are ${value} years old`;
  }
}

console.log(greet("Alice")); // Output: Hello, Alice
console.log(greet(30)); // Output: You are 30 years old
```

In this example:
- The function `greet` has two different signatures (one for `string` and one for `number`).
- The implementation then checks the type of the argument and returns a response accordingly.

### **8. Callbacks and Higher-Order Functions**

TypeScript makes working with **callbacks** and **higher-order functions** (functions that take other functions as arguments or return them) safer and more expressive.

#### **8.1 Callback Function Example**

```ts
function processData(data: string, callback: (result: string) => void): void {
  const processedData = data.toUpperCase();
  callback(processedData);
}

processData("hello", (result) => {
  console.log(result); // Output: HELLO
});
```

In this example, `processData` takes a string `data` and a `callback` function that takes a `string` and returns `void`.

#### **8.2 Higher-Order Function Example**

```ts
function multiplyBy(factor: number) {
  return function (num: number) {
    return num * factor;
  };
}

const multiplyBy2 = multiplyBy(2);
console.log(multiplyBy2(5)); // Output: 10
```

Here, `multiplyBy` is a higher-order function that returns a function.

### **9. Summary**

- Functions in TypeScript are similar to JavaScript functions, but with added **type annotations** for parameters and return types.
- You can define functions with **optional**, **default**, and **rest parameters**.
- **Function types** allow you to specify the type of a function and use it in other places in your code.
- TypeScript functions support **overloading**, **callbacks**, and **higher-order functions**.
- Understanding **`this`** in TypeScript is crucial, especially when using **arrow functions** vs **regular functions**.

# TypeScript Casting

Type casting in TypeScript is the process of overriding the compiler's type inference to treat a value as a different type. This is essential when working with complex types, external libraries, or when the TypeScript compiler can't automatically infer the correct type.

## Casting Syntax Options

TypeScript provides two main syntax options for type casting:

### 1. Angle Bracket Syntax

```typescript
let someValue: any = "hello world";
let strLength: number = (<string>someValue).length;
```

This syntax is the original TypeScript casting syntax but has limitations - it cannot be used in JSX because it conflicts with XML tag syntax.

### 2. "as" Syntax (Preferred)

```typescript
let someValue: any = "hello world";
let strLength: number = (someValue as string).length;
```

The `as` syntax is more modern and works in all contexts, including JSX. It's generally recommended to use this approach for consistency.

## Common Casting Scenarios

### Casting from "any" Type

When working with values of type `any`, casting helps to regain type safety:

```typescript
const userInput: any = getUserInput();
const username = userInput as string;
```

### DOM Manipulation

When working with DOM elements, TypeScript often needs help to understand specific element types:

```typescript
// Generic element type
const element = document.getElementById("myElement");

// Casting to specific element type
const inputElement = document.getElementById("myInput") as HTMLInputElement;
inputElement.value = "New value"; // Now TypeScript knows this has a value property
```

### Working with Complex Objects

When dealing with complex objects or libraries:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
}

const data: any = fetchUserData();
const user = data as User;
console.log(user.name); // TypeScript now knows this exists
```

## Type Assertions vs. Type Conversions

It's important to understand that TypeScript casting is a **compile-time operation** that doesn't change the actual value at runtime:

```typescript
// This doesn't convert the value, just tells TypeScript to treat it as a string
const num = 42 as any as string;

// This is still 42, not a string!
console.log(typeof num); // "number"
```

For actual value conversions, you need JavaScript conversion methods:

```typescript
const num = 42;
const str = String(num); // Actual conversion to string
console.log(typeof str); // "string"
```

## Double Casting

Sometimes you need to cast through `any` to bypass TypeScript's type checking:

```typescript
// Error: Conversion of type 'number' to type 'string' may be a mistake
// const str = 42 as string;

// Works, but potentially dangerous
const str = 42 as any as string;
```

This technique is sometimes called "force casting" and should be used sparingly, as it can introduce type safety issues.

## Type Guards vs. Casting

Type guards provide a safer alternative to casting in many scenarios:

```typescript
function isString(value: any): value is string {
  return typeof value === 'string';
}

const value: any = "test";

if (isString(value)) {
  // In this block, TypeScript knows value is a string
  console.log(value.toUpperCase());
}
```

Type guards perform runtime checks, making them more reliable than simple compile-time assertions.

## Best Practices

1. **Minimize casting**: Use proper typing whenever possible
2. **Prefer type guards**: They're safer than assertions for runtime checks
3. **Use the `as` syntax**: It's more consistent and works everywhere
4. **Avoid force casting**: Double casting with `any` bypasses TypeScript's safety features
5. **Cast at the source**: Cast values as close as possible to where they originate

# TypeScript Classes

TypeScript offers a robust implementation of classes that builds upon JavaScript's ES2015 class syntax while adding powerful type features. Classes in TypeScript provide a way to define blueprints for creating objects with specific properties and methods.

## Basic Class Syntax

Here's how to create a basic class in TypeScript:

```typescript
class Person {
  // Properties
  name: string;
  age: number;
  
  // Constructor
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // Method
  greet(): string {
    return `Hello, my name is ${this.name} and I'm ${this.age} years old.`;
  }
}

// Creating an instance
const person = new Person("Alice", 28);
console.log(person.greet()); // "Hello, my name is Alice and I'm 28 years old."
```

## Access Modifiers

TypeScript provides three access modifiers to control visibility of class members:

```typescript
class Employee {
  // Public - accessible from anywhere (default)
  public name: string;
  
  // Private - only accessible within the class
  private salary: number;
  
  // Protected - accessible within class and subclasses
  protected department: string;
  
  constructor(name: string, salary: number, department: string) {
    this.name = name;
    this.salary = salary; 
    this.department = department;
  }
  
  // Private method
  private calculateBonus(): number {
    return this.salary * 0.1;
  }
  
  // Public method calling private method
  public getYearlyCompensation(): number {
    return this.salary + this.calculateBonus();
  }
}
```

## Parameter Properties

TypeScript provides a concise way to define and initialize class members:

```typescript
class Product {
  // Parameter properties - automatically creates and initializes class members
  constructor(
    public id: number,
    public name: string,
    private price: number,
    protected category: string
  ) {}
  
  getFormattedPrice(): string {
    return `$${this.price.toFixed(2)}`;
  }
}
```

## Readonly Properties

You can make properties immutable after initialization:

```typescript
class Config {
  readonly apiKey: string;
  readonly maxRetries: number = 3;
  
  constructor(apiKey: string) {
    this.apiKey = apiKey;
    // Can set readonly properties in constructor
  }
  
  updateKey(newKey: string) {
    // Error: Cannot assign to 'apiKey' because it is a read-only property
    // this.apiKey = newKey;
  }
}
```

## Inheritance

Classes can inherit properties and methods from other classes:

```typescript
class Animal {
  constructor(protected name: string) {}
  
  move(distance: number = 0) {
    console.log(`${this.name} moved ${distance} meters.`);
  }
}

class Dog extends Animal {
  constructor(name: string) {
    super(name); // Call the parent constructor
  }
  
  bark() {
    console.log('Woof! Woof!');
  }
  
  // Override parent method
  move(distance: number = 5) {
    console.log('Running...');
    super.move(distance); // Call parent's move method
  }
}

const dog = new Dog('Rex');
dog.bark(); // "Woof! Woof!"
dog.move(); // "Running..." then "Rex moved 5 meters."
```

## Abstract Classes

Abstract classes serve as base classes that cannot be instantiated directly:

```typescript
abstract class Shape {
  constructor(protected color: string) {}
  
  abstract calculateArea(): number; // Must be implemented by subclasses
  
  displayColor() {
    console.log(`This shape is ${this.color}`);
  }
}

class Circle extends Shape {
  constructor(color: string, private radius: number) {
    super(color);
  }
  
  calculateArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

// Error: Cannot create an instance of an abstract class
// const shape = new Shape('red');

const circle = new Circle('blue', 5);
console.log(circle.calculateArea()); // ~78.54
circle.displayColor(); // "This shape is blue"
```

## Static Properties and Methods

Static members belong to the class itself, not to instances:

```typescript
class MathUtils {
  static PI: number = 3.14159;
  
  static square(x: number): number {
    return x * x;
  }
  
  static get random(): number {
    return Math.random();
  }
}

console.log(MathUtils.PI); // 3.14159
console.log(MathUtils.square(4)); // 16
console.log(MathUtils.random); // Random number between 0 and 1
```

## Getters and Setters

TypeScript supports accessor properties:

```typescript
class BankAccount {
  private _balance: number = 0;
  
  // Getter
  get balance(): number {
    return this._balance;
  }
  
  // Setter
  set balance(amount: number) {
    if (amount < 0) {
      throw new Error('Balance cannot be negative');
    }
    this._balance = amount;
  }
  
  deposit(amount: number) {
    this.balance += amount;
  }
}

const account = new BankAccount();
account.deposit(100);
console.log(account.balance); // 100

// Will throw an error due to setter validation
// account.balance = -50;
```

## Implementing Interfaces

Classes can implement interfaces to ensure they adhere to a contract:

```typescript
interface Printable {
  print(): void;
  getFormattedContent(): string;
}

class Invoice implements Printable {
  constructor(private client: string, private amount: number) {}
  
  print(): void {
    console.log(this.getFormattedContent());
  }
  
  getFormattedContent(): string {
    return `Invoice to ${this.client} for $${this.amount.toFixed(2)}`;
  }
}
```

## Generic Classes

TypeScript allows creating reusable, type-safe classes:

```typescript
class Queue<T> {
  private items: T[] = [];
  
  enqueue(item: T): void {
    this.items.push(item);
  }
  
  dequeue(): T | undefined {
    return this.items.shift();
  }
  
  peek(): T | undefined {
    return this.items[0];
  }
}

const numberQueue = new Queue<number>();
numberQueue.enqueue(10);
numberQueue.enqueue(20);

const stringQueue = new Queue<string>();
stringQueue.enqueue("hello");
stringQueue.enqueue("world");
```

In TypeScript, visibility modifiers are used to control the accessibility of class members (properties and methods). The three main visibility modifiers are:

### **1. `public`**

The `public` modifier is the default visibility in TypeScript. When you declare a class member as `public`, it means that the member can be accessed from anywhere, both inside and outside of the class.

- **Default**: If no modifier is specified, the member is automatically considered `public`.
  
```ts
class Person {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  public greet(): string {
    return `Hello, my name is ${this.name}`;
  }
}

const person = new Person("Alice");
console.log(person.name); // Accessing public member from outside the class
console.log(person.greet()); // Calling public method from outside the class
```

In this example:
- `name` and `greet()` are `public` by default, so they can be accessed from outside the `Person` class.

### **2. `private`**

The `private` modifier restricts access to a class member. A `private` member can only be accessed within the class that defines it. It is not accessible from outside the class, including derived classes.

```ts
class Person {
  private name: string;

  constructor(name: string) {
    this.name = name;
  }

  private greet(): string {
    return `Hello, my name is ${this.name}`;
  }

  public showGreeting() {
    return this.greet(); // Can call private method inside the class
  }
}

const person = new Person("Alice");

console.log(person.showGreeting()); // Valid: Accessing private method through a public method
console.log(person.name); // Error: Property 'name' is private and only accessible within class 'Person'.
console.log(person.greet()); // Error: Method 'greet' is private and only accessible within class 'Person'.
```

In this example:
- `name` and `greet()` are `private` and cannot be accessed directly from outside the `Person` class.
- However, you can access them via a **public** method (`showGreeting`) within the class.

### **3. `protected`**

The `protected` modifier allows access to the class member from the class that defines it and any classes that **inherit** from it. This means derived classes can access `protected` members, but they are not accessible from outside the class hierarchy.

```ts
class Person {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }

  protected greet(): string {
    return `Hello, my name is ${this.name}`;
  }
}

class Employee extends Person {
  private jobTitle: string;

  constructor(name: string, jobTitle: string) {
    super(name);
    this.jobTitle = jobTitle;
  }

  public introduce() {
    return `${this.greet()} and I work as a ${this.jobTitle}.`; // Can access protected method from parent class
  }
}

const employee = new Employee("Bob", "Developer");

console.log(employee.introduce()); // Valid: Accessing protected method via derived class
console.log(employee.name); // Error: Property 'name' is protected and only accessible within class 'Person' and its subclasses.
console.log(employee.greet()); // Error: Method 'greet' is protected and only accessible within class 'Person' and its subclasses.
```

In this example:
- `name` and `greet()` are `protected`, so they can be accessed within the `Person` class and by the `Employee` class (which inherits from `Person`).
- However, they are **not** accessible directly from an instance of `Employee` outside of the class hierarchy.

### **Summary of Visibility Modifiers**

- **`public`**: The member is accessible from anywhere, both inside and outside the class. It is the default if no modifier is specified.
- **`private`**: The member is only accessible inside the class that defines it. It cannot be accessed from derived classes or instances of the class.
- **`protected`**: The member is accessible inside the class and any derived classes (subclasses). It is **not** accessible from instances outside the class hierarchy.

### **Use Cases**

- **`public`** is ideal for properties or methods that should be accessible by any code using the class.
- **`private`** is used when you want to hide the internal details of a class and only expose necessary functionality.
- **`protected`** is useful when you want to share functionality with subclasses but not expose it to the outside world.




**Generics** in TypeScript allow you to write reusable, type-safe code by allowing you to define components (such as functions, classes, and interfaces) that can work with multiple types while preserving type information. Generics provide a way to make code flexible and adaptable while ensuring type safety.

Let’s dive into the basics of **generics** in TypeScript:

### **1. Generic Functions**

Generics allow you to define functions that can work with any type while still maintaining type safety. You define a placeholder type (e.g., `T`) in the function signature, which can then be replaced by any type when the function is called.

#### **1.1 Basic Example**

```ts
function identity<T>(arg: T): T {
  return arg;
}

let result = identity(5); // `T` is inferred as `number`
let stringResult = identity("Hello"); // `T` is inferred as `string`

console.log(result); // Output: 5
console.log(stringResult); // Output: Hello
```

- In this example, the `identity` function takes a parameter `arg` of type `T` and returns the same type `T`.
- Type `T` is a placeholder for any type, and TypeScript will infer it based on the type of the argument passed to the function.

#### **1.2 Explicit Type for Generics**

You can also explicitly specify the type for the generic:

```ts
function identity<T>(arg: T): T {
  return arg;
}

let result = identity<number>(5); // T is explicitly set to `number`
let stringResult = identity<string>("Hello"); // T is explicitly set to `string`

console.log(result); // Output: 5
console.log(stringResult); // Output: Hello
```

### **2. Generic Interfaces**

Generics can also be used in **interfaces** to define types that work with any type, making interfaces more reusable.

#### **2.1 Generic Interface Example**

```ts
interface Box<T> {
  value: T;
}

let box: Box<number> = { value: 42 }; // Box that holds a number
let stringBox: Box<string> = { value: "Hello" }; // Box that holds a string

console.log(box.value); // Output: 42
console.log(stringBox.value); // Output: Hello
```

- The `Box` interface is generic and can hold a value of any type `T`.
- The `value` property can be of type `number`, `string`, or any other type, depending on how the interface is used.

### **3. Generic Classes**

You can use generics in **classes** as well. This allows you to define classes that can operate on multiple types.

#### **3.1 Generic Class Example**

```ts
class GenericBox<T> {
  private value: T;

  constructor(value: T) {
    this.value = value;
  }

  getValue(): T {
    return this.value;
  }

  setValue(value: T): void {
    this.value = value;
  }
}

let numberBox = new GenericBox<number>(42);
console.log(numberBox.getValue()); // Output: 42

let stringBox = new GenericBox<string>("Hello");
console.log(stringBox.getValue()); // Output: Hello
```

- In this example, the `GenericBox` class is able to store a value of type `T`, and it can be used with different types (`number`, `string`, etc.).

### **4. Generic Constraints**

Sometimes you might want to limit the types that can be passed to a generic. You can do this by using **constraints**. Constraints allow you to define that a generic type `T` must extend a specific type or interface.

#### **4.1 Generic with Constraints**

```ts
interface Lengthy {
  length: number;
}

function logLength<T extends Lengthy>(item: T): void {
  console.log(item.length);
}

logLength("Hello"); // Output: 5
logLength([1, 2, 3]); // Output: 3
// logLength(5); // Error: Argument of type '5' is not assignable to parameter of type 'Lengthy'.
```

- In this example, the generic `T` is constrained to types that have a `length` property, which could be a string, array, or other object with a `length` property.

#### **4.2 Using Constraints in Classes**

```ts
class Container<T extends Lengthy> {
  private value: T;

  constructor(value: T) {
    this.value = value;
  }

  getValueLength(): number {
    return this.value.length;
  }
}

const stringContainer = new Container("Hello");
console.log(stringContainer.getValueLength()); // Output: 5

const arrayContainer = new Container([1, 2, 3]);
console.log(arrayContainer.getValueLength()); // Output: 3
```

- The `Container` class works only with types that have a `length` property, such as strings or arrays.

### **5. Generic Default Types**

You can specify a default type for a generic. If no type is provided when the function or class is used, TypeScript will use the default type.

#### **5.1 Default Type Example**

```ts
function wrap<T = string>(value: T): T {
  return value;
}

let result1 = wrap(123); // T is inferred as `number`
let result2 = wrap(); // T defaults to `string` and `value` is `undefined`

console.log(result1); // Output: 123
console.log(result2); // Output: undefined
```

- In this case, if no type argument is passed, TypeScript uses `string` as the default.

### **6. Generic with Multiple Types**

You can also use multiple type parameters in generics.

#### **6.1 Multiple Generic Types Example**

```ts
function merge<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

let merged = merge({ name: "Alice" }, { age: 30 });
console.log(merged); // Output: { name: 'Alice', age: 30 }
```

- The `merge` function takes two objects, `obj1` and `obj2`, of types `T` and `U`, and returns an object that is a combination of both (`T & U` means the intersection of both types).

### **7. Generic Type Inference**

TypeScript can automatically infer the type of a generic based on the provided arguments.

#### **7.1 Example of Type Inference**

```ts
function identity<T>(arg: T): T {
  return arg;
}

let numberValue = identity(42); // TypeScript infers T as number
let stringValue = identity("Hello"); // TypeScript infers T as string

console.log(numberValue); // Output: 42
console.log(stringValue); // Output: Hello
```

- TypeScript will automatically infer the type `T` based on the arguments passed, eliminating the need to explicitly specify the type.

### **8. Summary**

- **Generics** allow you to write functions, classes, and interfaces that are flexible and type-safe.
- They enable you to define a placeholder for types (e.g., `T`) and let TypeScript infer the type when the function/class/interface is used.
- You can use **generic constraints** to restrict the types that can be used with a generic.
- **Default types** can be provided for generics, and **multiple types** can be used in a single generic definition.

# TypeScript Utility Types

TypeScript provides several built-in utility types that help with common type transformations. These utilities allow you to manipulate types without repeating code, making your type definitions cleaner and more maintainable.

## Partial\<T>

Makes all properties of a type optional:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  role: string;
}

// All properties are optional
type PartialUser = Partial<User>;

// Valid - can include any subset of User properties
const userUpdate: PartialUser = {
  name: "John Smith",
  email: "john@example.com"
};
```

## Required\<T>

Makes all properties of a type required (removes optionality):

```typescript
interface BlogPost {
  title?: string;
  content?: string;
  author?: string;
  publishDate?: Date;
}

// All properties are now required
type RequiredBlogPost = Required<BlogPost>;

// Error: Missing properties
// const post: RequiredBlogPost = { title: "Hello World" };

// Valid
const completePost: RequiredBlogPost = {
  title: "Hello World",
  content: "This is my first post",
  author: "Jane Doe",
  publishDate: new Date()
};
```

## Readonly\<T>

Makes all properties readonly (cannot be reassigned):

```typescript
interface Config {
  apiUrl: string;
  timeout: number;
}

type ReadonlyConfig = Readonly<Config>;

const config: ReadonlyConfig = {
  apiUrl: "https://api.example.com",
  timeout: 3000
};

// Error: Cannot assign to 'apiUrl' because it is a read-only property
// config.apiUrl = "https://new-api.example.com";
```

## Record\<K, T>

Creates a type with properties of type K and values of type T:

```typescript
type UserRoles = Record<string, string>;

const roles: UserRoles = {
  admin: "Administrator",
  user: "Standard User",
  guest: "Guest User"
};

// With literal types
type ColorMap = Record<"primary" | "secondary" | "success" | "error", string>;

const colors: ColorMap = {
  primary: "#0275d8",
  secondary: "#6c757d",
  success: "#5cb85c",
  error: "#d9534f"
};
```

## Pick\<T, K>

Creates a type by picking a set of properties K from type T:

```typescript
interface Product {
  id: number;
  name: string;
  price: number;
  description: string;
  category: string;
  tags: string[];
}

// Only includes the specified properties
type ProductSummary = Pick<Product, "id" | "name" | "price">;

const productSummary: ProductSummary = {
  id: 1,
  name: "Laptop",
  price: 999
};
```

## Omit\<T, K>

Creates a type by omitting a set of properties K from type T:

```typescript
interface Article {
  id: number;
  title: string;
  content: string;
  author: string;
  createdAt: Date;
  updatedAt: Date;
}

// Excludes specified properties
type ArticlePreview = Omit<Article, "content" | "updatedAt">;

const preview: ArticlePreview = {
  id: 123,
  title: "Understanding TypeScript",
  author: "Jane Doe",
  createdAt: new Date()
};
```

## Exclude\<T, U>

Creates a type by excluding from T all union members that are assignable to U:

```typescript
type Status = "pending" | "in-progress" | "completed" | "cancelled" | "failed";

// Removes "cancelled" and "failed" from Status
type PositiveStatus = Exclude<Status, "cancelled" | "failed">;
// Result: "pending" | "in-progress" | "completed"

const status: PositiveStatus = "in-progress"; // Valid
// const badStatus: PositiveStatus = "cancelled"; // Error
```

## Extract\<T, U>

Creates a type by extracting from T all union members that are assignable to U:

```typescript
type Events = "click" | "focus" | "blur" | "keydown" | "keyup";
type MouseEvents = "click" | "mousedown" | "mouseup";

// Gets the intersection: "click"
type SupportedMouseEvents = Extract<Events, MouseEvents>;

const handler = (event: SupportedMouseEvents) => {
  console.log(event);
};

handler("click"); // Valid
// handler("focus"); // Error
```

## NonNullable\<T>

Creates a type by excluding null and undefined from T:

```typescript
type NullableString = string | null | undefined;

type DefiniteString = NonNullable<NullableString>;
// Result: string

const value: DefiniteString = "Hello"; // Valid
// const badValue: DefiniteString = null; // Error 
```

## ReturnType\<T>

Extracts the return type of a function type:

```typescript
function fetchUser(id: number) {
  return {
    id,
    name: "User " + id,
    isActive: true
  };
}

type User = ReturnType<typeof fetchUser>;
// Equivalent to: { id: number; name: string; isActive: boolean; }

const user: User = {
  id: 1,
  name: "User 1",
  isActive: true
};
```

## Parameters\<T>

Extracts the parameter types of a function type as a tuple:

```typescript
function createPost(title: string, content: string, tags: string[]) {
  return { title, content, tags };
}

type PostParams = Parameters<typeof createPost>;
// Type: [string, string, string[]]

const postData: PostParams = ["New Post", "Content here", ["typescript", "utility"]];
const post = createPost(...postData);
```

## InstanceType\<T>

Extracts the instance type of a constructor function:

```typescript
class APIClient {
  baseUrl: string;
  
  constructor(baseUrl: string) {
    this.baseUrl = baseUrl;
  }
  
  get(endpoint: string) {
    return `${this.baseUrl}/${endpoint}`;
  }
}

type Client = InstanceType<typeof APIClient>;
// Equivalent to the instance type of APIClient

function createClient(): Client {
  return new APIClient("https://api.example.com");
}
```

## Practical Use Cases

### Form State Management

```typescript
interface UserForm {
  username: string;
  email: string;
  password: string;
  confirmPassword: string;
}

// Track which fields have errors
type FormErrors = Partial<Record<keyof UserForm, string>>;

// Track which fields have been touched/modified
type TouchedFields = Record<keyof UserForm, boolean>;

const errors: FormErrors = {
  email: "Invalid email format",
  confirmPassword: "Passwords do not match"
};

const touched: TouchedFields = {
  username: true,
  email: true,
  password: false,
  confirmPassword: false
};
```

### API Request/Response Types

```typescript
interface User {
  id: number;
  username: string;
  email: string;
  password: string;
  createdAt: Date;
  lastLogin: Date;
}

// For create requests (no id or timestamps)
type CreateUserRequest = Omit<User, "id" | "createdAt" | "lastLogin">;

// For update requests (all fields optional except id)
type UpdateUserRequest = Partial<Omit<User, "id">> & { id: number };

// For responses (no password)
type UserResponse = Omit<User, "password">;
```

TypeScript 5.x introduced several significant features and improvements aimed at enhancing developer productivity, performance, and language expressiveness. Here's an overview of the key updates:

---

## 🆕 TypeScript 5.0 Highlights (Released March 16, 2023)

### 1. **Decorators (Stage 2 Proposal)**TypeScript 5.0 introduces decorators, allowing developers to add metadata or modify the behavior of classes and their membersThis brings TypeScript closer to aligning with the ECMAScript proposal for decorators citeturn0search0

### 2. **Const Type Parameters**The `const` modifier can now be applied to type parameters, enabling more precise type inference and ensuring immutabilityThis is particularly useful when working with literals, tuples, or arrays citeturn0search10

### 3. **All Enums Are Union Enums**All enums are now treated as union types of their member values, even if members are computed at runtimeThis simplifies type checking and improves predictability citeturn0search10

### 4. **Bundler Module Resolution**A new `bundler` module resolution strategy improves compatibility with modern bundlers like Webpack and Parcel, aligning TypeScript's module resolution with how these tools handle ECMAScript modules citeturn0search10

### 5. **Verbatim Module Syntax**The `--verbatimModuleSyntax` flag prevents TypeScript from removing type-only imports during compilation, ensuring that type information is preserved in the emitted JavaScript citeturn0search10

---

## 🔧 TypeScript 5.1 Enhancements (Released June 1, 2023)

### 1. **Independent Getter and Setter Types*
TypeScript 5.1 allows getter and setter methods to have completely unrelated types, provided they have explicit type annotation. This enhances flexibility when defining accessor propertie. citeturn0search1

### 2. **Performance Improvements*
Significant optimizations have been made to reduce unnecessary type instantiations, leading to faster type-checkin. For instance, type-checking times for some projects have been reduced by over 50. citeturn0search3

### 3. **Simplified Undefined Return Handling*
Functions that return `undefined` no longer require an explicit return statemen. This simplifies the syntax for such function. citeturn0search7

---

## 🔄 Breaking Changes and Deprecation

TypeScript 5.x introduces several breaking changes and deprecatios:

- **Module Resolution Changes*: The new `bundler` module resolution strategy may affect projects relying on the previous `node16` or `nodenext` strategis. citeturn0search10

- **Decorator Metadata*: The behavior of decorators has been updated to align with the ECMAScript proposal, which may impact existing decorator implementatios. citeturn0search0

---

## 🚀 Getting Started with TypeScript 5.x

To start using TypeScript 5.x in your project:

1. **Install TypeScript**:

   ```bash
   npm install -D typescript
   ``


2. **Initialize a TypeScript Project**:

   ```bash
   npx tsc --init
   ``


3. **Configure `tsconfig.json`**:

   ```json
   {
     "compilerOptions": {
       "moduleResolution": "bundler",
       "experimentalDecorators": true,
       "emitDecoratorMetadata": true
     }
   }
   ``


This setup enables the new module resolution strategy and decorator supprt.

--

For a comprehensive list of changes, refer to the official TypeScript 5.0 and 5.1 release noes:

- [TypeScript 5.0 Release Notes](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-0.html)

- [TypeScript 5.1 Release Notes](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-1.html)



# TypeScript for Beginners

## What is TypeScript?

TypeScript is a programming language developed by Microsoft that adds static types to JavaScript. It's a superset of JavaScript, which means that all JavaScript code is valid TypeScript code, but TypeScript adds additional features like type checking.

## Why Use TypeScript?

- **Catch errors early** during development instead of at runtime
- **Better code completion** in your editor
- **Easier to understand code** with clear type definitions
- **Safer refactoring** when making changes to your code
- **Popular in professional development** environments

## Basic Types

```typescript
// Basic types
let isDone: boolean = false;
let count: number = 10;
let name: string = "John";

// Arrays
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];

// Object
let person: { name: string; age: number } = {
  name: "John",
  age: 30
};

// Optional properties
let user: { name: string; email?: string } = {
  name: "Alice"
  // email is optional
};
```

## Functions

```typescript
// Function with typed parameters and return type
function add(x: number, y: number): number {
  return x + y;
}

// Optional parameters
function greet(name: string, greeting?: string): string {
  if (greeting) {
    return `${greeting}, ${name}!`;
  }
  return `Hello, ${name}!`;
}

// Default parameters
function createUser(name: string, active: boolean = true) {
  // ...
}
```

## Type Aliases and Interfaces

```typescript
// Type alias
type Point = {
  x: number;
  y: number;
};

// Using the type
let position: Point = { x: 10, y: 20 };

// Interface
interface User {
  id: number;
  name: string;
  email: string;
}

// Using the interface
const user: User = {
  id: 1,
  name: "John",
  email: "john@example.com"
};
```

## Union Types

```typescript
// Can be either string or number
let id: string | number;
id = 101;  // Valid
id = "ABC"; // Valid

// Function accepting multiple types
function printId(id: string | number) {
  console.log(`ID: ${id}`);
}
```

## Type Assertions

```typescript
// Sometimes you know more about a type than TypeScript
let someValue: any = "Hello World";

// Two ways to do type assertion:
let strLength1: number = (someValue as string).length;
let strLength2: number = (<string>someValue).length; // Not usable in JSX
```

## Classes

```typescript
class Person {
  // Properties
  name: string;
  age: number;

  // Constructor
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  // Method
  greet() {
    return `Hello, my name is ${this.name}`;
  }
}

// Create an instance
const person = new Person("Alice", 30);
console.log(person.greet());
```

## Enums

```typescript
// Define a set of named constants
enum Color {
  Red,
  Green,
  Blue
}

let backgroundColor: Color = Color.Blue;

// String enums
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT"
}
```

## Basic Generics

```typescript
// Generic function
function identity<T>(arg: T): T {
  return arg;
}

let output1 = identity<string>("myString");
let output2 = identity(42); // Type inference works too
```

## Getting Started with TypeScript

1. **Install TypeScript**:
   ```bash
   npm install -g typescript
   ```

2. **Create a TypeScript file** (e.g., `app.ts`):
   ```typescript
   function sayHello(name: string) {
     console.log(`Hello, ${name}!`);
   }
   
   sayHello("TypeScript Beginner");
   ```

3. **Compile to JavaScript**:
   ```bash
   tsc app.ts
   ```

4. **Run the JavaScript**:
   ```bash
   node app.js
   ```

## tsconfig.json

Create a configuration file for your TypeScript project:

```json
{
  "compilerOptions": {
    "target": "es2016",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist",
    "esModuleInterop": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

## Common Error Messages

- **Type '...' is not assignable to type '...'** - You're trying to use a value of the wrong type
- **Property '...' does not exist on type '...'** - You're trying to access a property that doesn't exist
- **Parameter '...' implicitly has an 'any' type** - You need to add type annotations

# TypeScript for Mid-Level Developers

## Advanced Type System Features

### Discriminated Unions

```typescript
interface Circle {
  kind: "circle";
  radius: number;
}

interface Rectangle {
  kind: "rectangle";
  width: number;
  height: number;
}

type Shape = Circle | Rectangle;

function calculateArea(shape: Shape): number {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "rectangle":
      return shape.width * shape.height;
  }
}
```

### Type Narrowing

```typescript
function process(value: string | number) {
  // Type guard using typeof
  if (typeof value === "string") {
    // TypeScript knows value is a string here
    return value.toUpperCase();
  } else {
    // TypeScript knows value is a number here
    return value.toFixed(2);
  }
}

// Custom type guards
function isUser(obj: any): obj is User {
  return obj && typeof obj === "object" && "name" in obj && "id" in obj;
}
```

### Intersection Types

```typescript
type DatabaseEntity = {
  id: number;
  createdAt: Date;
  updatedAt: Date;
};

type UserData = {
  name: string;
  email: string;
  role: string;
};

// Combines both types
type UserEntity = UserData & DatabaseEntity;
```

## Working with Functions

### Function Overloads

```typescript
// Overload signatures
function parseValue(value: string): string;
function parseValue(value: number): number;
function parseValue(value: boolean): string;
// Implementation signature
function parseValue(value: string | number | boolean): string | number {
  if (typeof value === "string") {
    return value.trim();
  } else if (typeof value === "number") {
    return value;
  } else {
    return value ? "true" : "false";
  }
}
```

### Generic Constraints

```typescript
interface HasLength {
  length: number;
}

// T must have a length property
function logAndReturn<T extends HasLength>(value: T): T {
  console.log(`Length: ${value.length}`);
  return value;
}

// Valid
logAndReturn("hello");
logAndReturn([1, 2, 3]);
logAndReturn({ length: 10, name: "something" });

// Error: number doesn't have length property
// logAndReturn(42);
```

## Class & Interface Advanced Patterns

### Abstract Classes

```typescript
abstract class BaseComponent {
  constructor(protected element: HTMLElement) {}
  
  // Method that must be implemented
  abstract render(): void;
  
  // Method with default implementation
  initialize(): void {
    console.log("Component initialized");
  }
}

class Button extends BaseComponent {
  render(): void {
    this.element.innerHTML = `<button>Click me</button>`;
  }
}
```

### Interface Merging

```typescript
// Declaration merging - both declarations combine
interface API {
  getUsers(): Promise<User[]>;
}

interface API {
  getPosts(): Promise<Post[]>;
}

// Result includes both methods
const api: API = {
  getUsers: async () => [],
  getPosts: async () => []
};
```

## Utility Types

```typescript
interface Product {
  id: number;
  name: string;
  price: number;
  category: string;
  description: string;
}

// Only some fields required
type ProductCreationParams = Pick<Product, "name" | "price" | "category">;

// All fields optional
type ProductUpdateParams = Partial<Product>;

// All fields required, none optional
type RequiredProduct = Required<Product>;

// Remove specific fields
type ProductPreview = Omit<Product, "description">;

// Map over keys and transform values
type ReadonlyProduct = Readonly<Product>;
```

## Advanced Generics

```typescript
// Multiple type parameters
function merge<T extends object, U extends object>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

// Generic constraints with keyof
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

// Generic classes with constraints
class StateManager<T extends object> {
  private state: T;
  
  constructor(initialState: T) {
    this.state = { ...initialState };
  }
  
  get<K extends keyof T>(key: K): T[K] {
    return this.state[key];
  }
  
  set<K extends keyof T>(key: K, value: T[K]): void {
    this.state[key] = value;
  }
}
```

## Practical Project Structure

```
project/
├── src/
│   ├── components/
│   │   └── Button.ts
│   ├── models/
│   │   └── User.ts
│   ├── services/
│   │   └── api.ts
│   ├── utils/
│   │   └── helpers.ts
│   ├── types/
│   │   └── index.ts
│   └── index.ts
├── tsconfig.json
└── package.json
```

### Type Organization

```typescript
// types/api.ts
export interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

// types/models.ts
export interface User {
  id: number;
  name: string;
  email: string;
}

// types/index.ts
export * from './api';
export * from './models';
```

## Working with Libraries and Modules

### Declaration Files

```typescript
// typings.d.ts
declare module 'untyped-module' {
  export function doSomething(value: string): number;
  export const VERSION: string;
}
```

### Module Augmentation

```typescript
// Add properties to existing module/library
declare module 'express-session' {
  interface SessionData {
    user: {
      id: string;
      role: string;
    }
  }
}
```

## Advanced Configuration

### Path Aliases

```json
// tsconfig.json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@components/*": ["src/components/*"],
      "@services/*": ["src/services/*"],
      "@utils/*": ["src/utils/*"],
      "@types/*": ["src/types/*"]
    }
  }
}
```

### Strict Type Checking

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictBindCallApply": true,
    "strictPropertyInitialization": true,
    "noImplicitThis": true,
    "useUnknownInCatchVariables": true
  }
}
```

## Testing with TypeScript

```typescript
// Using Jest with TypeScript
import { sum } from '../utils/math';

describe('Math utils', () => {
  test('adds two numbers correctly', () => {
    expect(sum(1, 2)).toBe(3);
  });
});
```

## Practical Tips

1. **Use unknown instead of any** when you don't know a type
2. **Enable strictest compiler options** and work with the constraints
3. **Limit type assertions** to situations where you know more than the compiler
4. **Create type declarations** for untyped libraries you use often
5. **Use eslint with typescript plugins** to catch common mistakes
6. **Organize types by domain** rather than putting all types in one file
7. **When unsure about a library API**, check DefinitelyTyped or the source
8. **Use type predicates** for cleaner type narrowing in complex cases


# TypeScript for Expert-Level Developers

## Advanced Type System Engineering

### Conditional Types with Distributive Properties

```typescript
// Distributive conditional types operate on union types
type ToArray<T> = T extends any ? T[] : never;
type StrOrNumArr = ToArray<string | number>; // string[] | number[]

// Filter union types
type NonNullable<T> = T extends null | undefined ? never : T;
type Filtered = NonNullable<string | null | undefined>; // string
```

### Type Inference in Conditional Types

```typescript
// Extract return type from function
type ReturnTypeOf<T extends (...args: any) => any> = 
  T extends (...args: any) => infer R ? R : any;

// Extract components from tuple types
type First<T extends any[]> = T extends [infer F, ...any[]] ? F : never;
type Last<T extends any[]> = T extends [...any[], infer L] ? L : never;

// Extract types from promises
type UnpackPromise<T> = T extends Promise<infer U> ? U : T;
```

### Template Literal Type Manipulation

```typescript
// Powerful string manipulations at type level
type EventName<T extends string> = `${T}Changed`;
type UserEvents = EventName<"name" | "email" | "password">; // "nameChanged" | "emailChanged" | "passwordChanged"

// Extract parts from strings in types
type ExtractDomain<T extends string> = 
  T extends `https://${infer Domain}/${string}` ? Domain : never;

// Convert case at type level
type CamelToSnake<S extends string> = 
  S extends `${infer T}${infer U}` ?
    T extends Capitalize<T> ?
      `_${Lowercase<T>}${CamelToSnake<U>}` :
      `${T}${CamelToSnake<U>}` :
    S;
```

### Advanced Mapped Types

```typescript
// Recursive mapped types
type DeepReadonly<T> = {
  readonly [P in keyof T]: T[P] extends object 
    ? T[P] extends Function
      ? T[P] 
      : DeepReadonly<T[P]>
    : T[P]
};

// Conditional property mapping
type ConditionalMapper<T> = {
  [K in keyof T]: T[K] extends Function 
    ? T[K] 
    : T[K] extends object
      ? ConditionalMapper<T[K]>
      : T[K] extends string 
        ? string | null
        : T[K]
};

// Filtering keys by value type
type KeysOfType<T, U> = {
  [K in keyof T]: T[K] extends U ? K : never
}[keyof T];
```

## TypeScript Compiler API

```typescript
import * as ts from "typescript";

// Create a virtual source file
function createSourceFile(content: string) {
  return ts.createSourceFile(
    "file.ts",
    content,
    ts.ScriptTarget.Latest,
    true
  );
}

// Basic AST traversal
function findFunctions(sourceFile: ts.SourceFile) {
  const functions: ts.FunctionDeclaration[] = [];
  
  function visit(node: ts.Node) {
    if (ts.isFunctionDeclaration(node)) {
      functions.push(node);
    }
    ts.forEachChild(node, visit);
  }
  
  visit(sourceFile);
  return functions;
}

// Parse and analyze a TypeScript file
function analyzeTypes(code: string) {
  const sourceFile = createSourceFile(code);
  const program = ts.createProgram(
    ["file.ts"], 
    {
      target: ts.ScriptTarget.ESNext,
      module: ts.ModuleKind.ESNext,
    }, 
    {
      getSourceFile: (fileName) => 
        fileName === "file.ts" ? sourceFile : undefined,
      writeFile: () => {},
      getDefaultLibFileName: () => "lib.d.ts",
      getCurrentDirectory: () => "",
      getDirectories: () => [],
      fileExists: () => true,
      readFile: () => "",
      getCanonicalFileName: (f) => f,
      useCaseSensitiveFileNames: () => true,
      getNewLine: () => "\n",
    }
  );
  
  const checker = program.getTypeChecker();
  // Now use checker to analyze types
}
```

## Type-Level Programming

```typescript
// Numeric operations at type level
type Add<A extends number, B extends number> = 
  [...BuildTuple<A>, ...BuildTuple<B>]['length'];
type BuildTuple<N extends number, T extends unknown[] = []> = 
  T['length'] extends N ? T : BuildTuple<N, [...T, unknown]>;

// Type-level recursion
type Fibonacci<N extends number> = 
  N extends 0 ? 0 :
  N extends 1 ? 1 :
  Add<Fibonacci<Subtract<N, 1>>, Fibonacci<Subtract<N, 2>>>;

// Type-safe state machine
type State = 'idle' | 'loading' | 'success' | 'error';
type Event = 'fetch' | 'resolve' | 'reject' | 'reset';

type Transitions = {
  idle: { fetch: 'loading' };
  loading: { resolve: 'success'; reject: 'error' };
  success: { reset: 'idle' };
  error: { reset: 'idle'; fetch: 'loading' };
};

type NextState<S extends State, E extends Event> = 
  S extends keyof Transitions 
    ? E extends keyof Transitions[S] 
      ? Transitions[S][E] 
      : S 
    : S;
```

## Performance Optimizations

### Type Definition Techniques for Performance

```typescript
// Use interfaces for better structural type performance
interface FastInterface {
  prop: string;
  method(): void;
}

// Avoid excessive union types with many members
type Efficient = "a" | "b" | "c";
// Rather than:
// type Inefficient = "a" | "b" | "c" | ... // hundreds of literals

// Use lookup types instead of extending interfaces multiple times
interface ApiRoutes {
  users: {
    get: '/api/users';
    post: '/api/users/create';
    // ...
  };
  products: {
    get: '/api/products';
    // ...
  };
}
type UserRoutes = ApiRoutes['users']; // Efficient lookup
```

### Project Structure for Large Codebases

```typescript
// Barrel files with selective re-exports
// utils/index.ts
export { formatDate, parseDate } from './dateUtils';
export { mapCollection, filterCollection } from './collectionUtils';
// Don't export everything indiscriminately

// Organize code by domain features rather than technical components
// Better:
// src/features/user/components, src/features/user/services
// Rather than:
// src/components/user, src/services/user

// Use path aliases for absolute imports
// tsconfig.json
{
  "compilerOptions": {
    "paths": {
      "@features/*": ["src/features/*"],
      "@core/*": ["src/core/*"],
      "@shared/*": ["src/shared/*"]
    }
  }
}
```

## Monorepos and Project References

```typescript
// root tsconfig.json
{
  "files": [],
  "references": [
    { "path": "./packages/common" },
    { "path": "./packages/server" },
    { "path": "./packages/client" }
  ]
}

// packages/server/tsconfig.json
{
  "extends": "../../tsconfig.base.json",
  "compilerOptions": {
    "composite": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "references": [
    { "path": "../common" }
  ]
}

// Working with project references
// packages/server/src/index.ts
import { SharedType } from '@project/common';
// TypeScript knows the dependency relationship
```

## Advanced Decorator Patterns

```typescript
// Method decorator with parameters
function Validate<T>(schema: Schema<T>) {
  return function(
    target: any,
    propertyKey: string,
    descriptor: PropertyDescriptor
  ) {
    const originalMethod = descriptor.value;
    
    descriptor.value = function(...args: any[]) {
      // Validate input against schema
      const valid = schema.validate(args[0]);
      if (!valid) {
        throw new Error(`Validation failed for ${propertyKey}`);
      }
      
      return originalMethod.apply(this, args);
    };
    
    return descriptor;
  };
}

// Property decorator with metadata
function Property() {
  return function(target: any, propertyKey: string) {
    // Using metadata API (requires experimentalDecorators)
    const properties = Reflect.getMetadata('properties', target) || [];
    properties.push(propertyKey);
    Reflect.defineMetadata('properties', properties, target);
  };
}

// Class decorator factory
function Entity(options: EntityOptions) {
  return function<T extends { new(...args: any[]): {} }>(constructor: T) {
    return class extends constructor {
      __entityName = options.name;
      __tableName = options.table;
      
      save() {
        // Use metadata to perform operation
        const properties = Reflect.getMetadata('properties', this) || [];
        const values = properties.map(p => (this as any)[p]);
        // Save to database...
      }
    };
  };
}
```

## Advanced Testing Patterns

```typescript
// Type testing using conditional types
type Assert<T extends true> = T;
type Equal<X, Y> = (<T>() => T extends X ? 1 : 2) extends
  (<T>() => T extends Y ? 1 : 2) ? true : false;

// Example type tests
type tests = [
  Assert<Equal<string, string>>,
  Assert<Equal<{ a: number; b: string }, { a: number; b: string }>>,
  Assert<Equal<string[], Array<string>>>
];

// Mock type creation for testing
type MockOf<T> = {
  [K in keyof T]: T[K] extends (...args: infer Args) => infer R
    ? jest.Mock<R, Args>
    : T[K]
};

function createMock<T>(): MockOf<T> {
  return new Proxy({} as any, {
    get: (target, prop) => {
      if (!target[prop]) {
        target[prop] = jest.fn();
      }
      return target[prop];
    }
  });
}
```

## Build Process Optimization

```typescript
// tsconfig.json for optimal builds
{
  "compilerOptions": {
    "incremental": true,
    "tsBuildInfoFile": "./buildcache/tsbuildinfo",
    "composite": true,
    "declaration": true,
    "sourceMap": true,
    "declarationMap": true
  }
}

// Splitting configs for dev and production
// tsconfig.dev.json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "sourceMap": true,
    "inlineSourceMap": false,
    "noUnusedLocals": false
  }
}

// tsconfig.prod.json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "sourceMap": false,
    "inlineSourceMap": false,
    "noUnusedLocals": true,
    "removeComments": true
  }
}
```

## Advanced Module Interoperability

```typescript
// Interoperability with ESM and CommonJS
// package.json
{
  "name": "my-package",
  "type": "module",
  "exports": {
    ".": {
      "import": "./dist/index.js",
      "require": "./dist/cjs/index.js",
      "types": "./dist/index.d.ts"
    }
  }
}

// Supporting both module formats in TypeScript
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "esModuleInterop": true,
  }
}

// tsconfig.cjs.json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "module": "CommonJS",
    "outDir": "./dist/cjs"
  }
}
```

This overview covers expert-level TypeScript techniques that focus on advanced type manipulation, compiler optimizations, and patterns for large-scale application development. These techniques demonstrate how TypeScript can be used as a powerful type-level programming language alongside its role as a JavaScript superset.




# TypeScript Interview Questions and Answers

## Beginner Level Questions

### 1. What is TypeScript and why would you use it over JavaScript?

**Answer**: TypeScript is a strongly-typed superset of JavaScript developed by Microsoft that compiles to plain JavaScript. You would use TypeScript over JavaScript for:
- Static type checking that catches errors during development rather than runtime
- Enhanced IDE support with better autocompletion and navigation
- More maintainable code for large applications
- Type annotations that serve as documentation
- Support for modern JavaScript features that work across browsers after compilation

### 2. Explain the difference between `interface` and `type` in TypeScript.

**Answer**: Both `interface` and `type` can be used to define object shapes, but they have some differences:

- `interface` is focused on defining object shapes and can be extended or implemented
- `type` is more flexible and can represent primitive types, unions, tuples, and other advanced types
- `interface` supports declaration merging (multiple declarations are merged)
- `type` can create mapped types, conditional types, and use utility types
- `interface` is generally preferred for public API definitions and when you want to allow extension

Example:
```typescript
// Interface
interface User {
  name: string;
  age: number;
}

// Type
type User = {
  name: string;
  age: number;
};
```

### 3. What are TypeScript access modifiers?

**Answer**: TypeScript provides three access modifiers for class members:

- `public`: Members are accessible from anywhere (default if not specified)
- `private`: Members are only accessible within the class they're defined in
- `protected`: Members are accessible within the class they're defined in and in derived classes

Example:
```typescript
class Person {
  public name: string;
  private ssn: string;
  protected age: number;
  
  constructor(name: string, ssn: string, age: number) {
    this.name = name;
    this.ssn = ssn;
    this.age = age;
  }
}
```

### 4. How do you define optional properties in TypeScript?

**Answer**: You can define optional properties using the `?` symbol after the property name:

```typescript
interface Product {
  id: number;
  name: string;
  price: number;
  description?: string; // Optional property
  category?: string;    // Optional property
}

const book: Product = {
  id: 1,
  name: "TypeScript Guide",
  price: 29.99
  // description and category can be omitted
};
```

## Intermediate Level Questions

### 5. Explain TypeScript generics with an example.

**Answer**: Generics allow you to create reusable components that work with a variety of types rather than a single type. They help you write flexible, type-safe code:

```typescript
// A generic function
function identity<T>(arg: T): T {
  return arg;
}

// Using the generic function
const str = identity<string>("hello"); // str has type string
const num = identity(42);             // num has type number (type inference)

// Generic interface
interface Box<T> {
  value: T;
}

const stringBox: Box<string> = { value: "hello" };
const numberBox: Box<number> = { value: 10 };
```

### 6. What is the difference between `unknown` and `any` types?

**Answer**: Both `unknown` and `any` can hold values of any type, but they differ in type safety:

- `any`: Bypasses type checking completely. You can perform any operations on values of type `any`.
- `unknown`: A type-safe alternative to `any`. You must perform type checking before performing operations on `unknown` values.

Example:
```typescript
let anyValue: any = 10;
anyValue.foo(); // No error, but might fail at runtime

let unknownValue: unknown = 10;
// unknownValue.foo(); // Error: Object is of type 'unknown'

// Must check type before using
if (typeof unknownValue === "number") {
  console.log(unknownValue + 5); // Valid after type check
}
```

### 7. How do union types work in TypeScript?

**Answer**: Union types allow a value to be one of several types. You define a union type using the pipe (`|`) operator:

```typescript
// A function that works with multiple types
function formatValue(value: string | number): string {
  if (typeof value === "string") {
    return value.trim();
  }
  return value.toFixed(2);
}

formatValue("hello ");  // Returns "hello"
formatValue(42.5);      // Returns "42.50"
```

### 8. What are TypeScript decorators and what are they used for?

**Answer**: Decorators are a feature that allow you to add metadata to classes, methods, properties, or parameters. They're often used in frameworks like Angular:

```typescript
// A simple class decorator
function LogClass(target: any) {
  console.log(`Class created: ${target.name}`);
}

// A method decorator
function LogMethod(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const original = descriptor.value;
  descriptor.value = function(...args: any[]) {
    console.log(`Calling ${propertyKey} with:`, args);
    return original.apply(this, args);
  };
  return descriptor;
}

@LogClass
class Calculator {
  @LogMethod
  add(a: number, b: number): number {
    return a + b;
  }
}
```

## Advanced Level Questions

### 9. Explain how conditional types work in TypeScript.

**Answer**: Conditional types help you create types that depend on other types, using a syntax similar to conditional expressions:

```typescript
type TypeName<T> = 
  T extends string ? "string" :
  T extends number ? "number" :
  T extends boolean ? "boolean" :
  T extends undefined ? "undefined" :
  T extends Function ? "function" :
  "object";

// Using the conditional type
type T0 = TypeName<string>;      // "string"
type T1 = TypeName<number[]>;    // "object"
type T2 = TypeName<() => void>;  // "function"
```

### 10. How do you work with discriminated unions in TypeScript?

**Answer**: Discriminated unions combine union types with a common, singleton type property (the discriminant) to create a type-safe way to work with heterogeneous data:

```typescript
interface Square {
  kind: "square";
  size: number;
}

interface Rectangle {
  kind: "rectangle";
  width: number;
  height: number;
}

interface Circle {
  kind: "circle";
  radius: number;
}

type Shape = Square | Rectangle | Circle;

function calculateArea(shape: Shape): number {
  switch (shape.kind) {
    case "square":
      return shape.size * shape.size;
    case "rectangle":
      return shape.width * shape.height;
    case "circle":
      return Math.PI * shape.radius ** 2;
    default:
      // Exhaustiveness check
      const _exhaustiveCheck: never = shape;
      return _exhaustiveCheck;
  }
}
```

### 11. Explain how to use mapped types in TypeScript.

**Answer**: Mapped types allow you to create new types by transforming properties of existing types:

```typescript
// Making all properties optional
type Partial<T> = {
  [P in keyof T]?: T[P];
};

// Making all properties readonly
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

// Creating a type with the same properties but different value types
type Stringify<T> = {
  [P in keyof T]: string;
};

interface Person {
  name: string;
  age: number;
  active: boolean;
}

// All properties are now optional
type PartialPerson = Partial<Person>;

// All properties are now strings
type StringifyPerson = Stringify<Person>;
// Equivalent to: { name: string; age: string; active: string; }
```

### 12. How does TypeScript's type inference work, and when might it fail?

**Answer**: TypeScript analyzes code flow to automatically determine types without explicit annotations:

```typescript
// Type inference for variables
let x = 3; // x is inferred as number

// Type inference for return types
function add(a: number, b: number) {
  return a + b; // Return type is inferred as number
}

// Type inference for arrays
const numbers = [1, 2, 3]; // inferred as number[]
const mixed = [1, "hello"]; // inferred as (string | number)[]
```

Type inference might fail when:
- Working with complex object structures
- Using third-party libraries without type definitions
- When the analyzer doesn't have enough information from the context
- With complex generic types that need explicit type parameters

### 13. What are declaration merging and module augmentation in TypeScript?

**Answer**: Declaration merging allows multiple declarations with the same name to be combined automatically:

```typescript
// Declaration merging with interfaces
interface User {
  name: string;
}

interface User {
  age: number;
}

// Results in:
// interface User {
//   name: string;
//   age: number;
// }

// Module augmentation to add to existing modules
declare module "lodash" {
  interface LoDashStatic {
    customFunction(arg: string): number;
  }
}
```

Module augmentation is particularly useful for adding types to existing libraries or extending the global scope.

### 14. Explain how the `infer` keyword works in TypeScript.

**Answer**: The `infer` keyword is used within conditional types to extract type information:

```typescript
// Extract the return type of a function
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : any;

function fetchData(): Promise<string> {
  return Promise.resolve("data");
}

type Result = ReturnType<typeof fetchData>; // Promise<string>

// Extract the element type of an array
type ElementType<T> = T extends (infer U)[] ? U : never;

type Numbers = ElementType<number[]>; // number
```

### 15. How would you handle asynchronous code typing in TypeScript?

**Answer**: TypeScript provides excellent support for asynchronous code using Promises and async/await:

```typescript
// Defining Promise types
function fetchUser(id: string): Promise<User> {
  return fetch(`/api/users/${id}`)
    .then(response => response.json());
}

// Async/await with proper typing
async function getUserData(id: string): Promise<UserData> {
  try {
    const user = await fetchUser(id);
    const permissions = await fetchPermissions(user.id);
    return { user, permissions };
  } catch (error) {
    // Type guard for error handling
    if (error instanceof ApiError) {
      console.error(error.message);
    }
    throw error;
  }
}

// Generic async utilities
async function mapAsync<T, U>(
  array: T[],
  callback: (item: T) => Promise<U>
): Promise<U[]> {
  return Promise.all(array.map(callback));
}
```

These questions and answers cover a wide range of TypeScript topics that are frequently asked in interviews, from basic concepts to advanced type manipulations.


Here’s a curated list of **Mid-Level TypeScript Interview Questions and Answers** — perfect for refreshing before an interview or evaluating candidates.

---

## ⚙️ **1. What are the key differences between `any`, `unknown`, and `never`?**

### ✅ Answer:
- `any`: Disables type checking. You can do anything with an `any` type.
- `unknown`: Safer version of `any`; you must perform type-checks before operating on it.
- `never`: Represents values that never occur (e.g., function throws error or infinite loop).

```ts
let a: any = "Hello";        // No type safety
let u: unknown = "Hello";    // Must check type before usage
let n: never;                // Used in exhaustive checks
```

---

## ⚙️ **2. What is type inference in TypeScript?**

### ✅ Answer:
TypeScript can automatically infer types based on values.

```ts
let count = 5; // inferred as number
```

You can still add type annotations explicitly if needed:

```ts
let count: number = 5;
```

---

## ⚙️ **3. What are interfaces and how are they different from type aliases?**

### ✅ Answer:
- **Interfaces**: Used to define shape of objects. Extendable.
- **Type Aliases**: Can alias any type (primitives, unions, intersections, etc).

```ts
interface Person {
  name: string;
  age: number;
}

type Employee = Person & { jobTitle: string };
```

- **Interfaces** are better for OOP-style class contracts.
- **Types** are more flexible and can represent more things (like unions).

---

## ⚙️ **4. How does `readonly` work in TypeScript?**

### ✅ Answer:
`readonly` makes properties immutable after initialization.

```ts
interface Car {
  readonly vin: string;
  model: string;
}

const myCar: Car = { vin: "123ABC", model: "Tesla" };
myCar.vin = "456DEF"; // ❌ Error: vin is readonly
```

---

## ⚙️ **5. What are generics and why are they useful?**

### ✅ Answer:
Generics provide a way to write reusable components while maintaining type safety.

```ts
function identity<T>(arg: T): T {
  return arg;
}

const num = identity<number>(5); // Generic with number
```

They allow you to create functions, interfaces, and classes that can work with a variety of types.

---

## ⚙️ **6. What is the difference between `interface` and `abstract class`?**

### ✅ Answer:
- `interface`: Pure type contract, cannot have implementation.
- `abstract class`: Can have implementation and abstract methods.

```ts
interface Animal {
  makeSound(): void;
}

abstract class AnimalBase {
  abstract makeSound(): void;
  move(): void {
    console.log("Moving");
  }
}
```

Use `abstract class` when you need shared implementation, use `interface` for pure contracts.

---

## ⚙️ **7. Explain the use of `keyof`, `typeof`, `in` in TypeScript**

### ✅ Answer:
- `keyof`: Gets the keys of a type as a union.
- `typeof`: Gets the type of a variable or object.
- `in`: Used for mapping types or narrowing.

```ts
type Person = { name: string; age: number };
type PersonKeys = keyof Person; // "name" | "age"

const user = { id: 1, name: "Alice" };
type UserType = typeof user;

type Flags = { [K in 'start' | 'stop']: boolean };
```

---

## ⚙️ **8. What is a discriminated union?**

### ✅ Answer:
A **discriminated union** uses a common property to distinguish between types.

```ts
type Shape =
  | { kind: 'circle'; radius: number }
  | { kind: 'square'; size: number };

function getArea(shape: Shape) {
  if (shape.kind === 'circle') return Math.PI * shape.radius ** 2;
  if (shape.kind === 'square') return shape.size ** 2;
}
```

It enables exhaustive type checking with `never`:

```ts
function assertNever(value: never): never {
  throw new Error(`Unexpected value: ${value}`);
}
```

---

## ⚙️ **9. Can a TypeScript interface extend a type alias?**

### ✅ Answer:
Yes, as long as the type alias resolves to an object type.

```ts
type Base = { id: number };
interface Extended extends Base {
  name: string;
}
```

---

## ⚙️ **10. How is `Partial<T>`, `Required<T>`, `Readonly<T>`, and `Pick<T, K>` used?**

### ✅ Answer:
These are utility types in TypeScript.

```ts
interface User {
  name: string;
  age: number;
}

const p: Partial<User> = {};           // All optional
const r: Required<User> = { name: 'A', age: 20 };
const ro: Readonly<User> = { name: 'A', age: 20 };
const pk: Pick<User, 'name'> = { name: 'A' };
```

---

## ⚙️ **11. How does TypeScript handle async/await with types?**

### ✅ Answer:
You define return type using `Promise<T>`:

```ts
async function fetchData(): Promise<string> {
  return "Data loaded";
}
```

---

## ⚙️ **12. What’s the difference between `type assertion` and `type casting`?**

### ✅ Answer:
They are mostly the same in TypeScript — used to tell the compiler about a more specific type:

```ts
let input = document.getElementById("username") as HTMLInputElement;
```

Also possible via:

```ts
let input = <HTMLInputElement>document.getElementById("username");
```

---

## ⚙️ **13. What is the use of the `as const` assertion?**

### ✅ Answer:
It makes an object or array deeply immutable and narrows its type to literals.

```ts
let x = [10, 20] as const;
// x: readonly [10, 20]

const config = {
  env: "production",
  port: 3000
} as const;
```

---

## ⚙️ **14. How can you ensure type safety when working with third-party JS libraries?**

### ✅ Answer:
- Use type definitions via `@types/library-name`
- Manually define a `.d.ts` declaration file if no types exist.

```bash
npm install --save-dev @types/lodash
```

---

## ⚙️ **15. What are module augmentation and declaration merging?**

### ✅ Answer:
TypeScript allows extending existing types/interfaces or modules.

```ts
declare module 'express' {
  interface Request {
    user?: any;
  }
}
```

Used when you need to add new properties to third-party types.

---

Here are **Expert-Level TypeScript Interview Questions and Answers** — covering advanced features, type system mechanics, and performance-level concerns.

---

## 🔍 **1. How does TypeScript’s structural typing work?**

### ✅ Answer:
TypeScript uses **structural typing**, not nominal typing. That means types are compatible if their shape matches — regardless of declared type names.

```ts
type Point = { x: number; y: number };
const draw = (point: Point) => { /* ... */ };

const myPoint = { x: 10, y: 20, z: 30 };
draw(myPoint); // ✅ Allowed: extra props are OK
```

---

## 🔍 **2. What is conditional typing in TypeScript?**

### ✅ Answer:
A powerful feature for type logic branching.

```ts
type IsString<T> = T extends string ? true : false;

type A = IsString<'hello'>; // true
type B = IsString<42>;      // false
```

Can be used with generics and `infer` to extract types dynamically.

---

## 🔍 **3. How does `infer` work in conditional types?**

### ✅ Answer:
`infer` allows you to infer types within a conditional type block.

```ts
type Unpack<T> = T extends Promise<infer U> ? U : T;

type A = Unpack<Promise<string>>; // string
type B = Unpack<number>;          // number
```

Used in utility types like `ReturnType`, `Parameters`, etc.

---

## 🔍 **4. Explain the difference between type narrowing and type guarding.**

### ✅ Answer:
- **Narrowing**: TypeScript reduces a union to a specific type based on control flow.
- **Type Guards**: Functions/conditions that help narrow types.

```ts
function isString(value: unknown): value is string {
  return typeof value === 'string';
}
```

This enables safe operations on types post-check.

---

## 🔍 **5. How does TypeScript's declaration merging work?**

### ✅ Answer:
When multiple declarations share a name, TypeScript merges them.

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

// Resulting type: { name: string; age: number; }
```

Also works with modules and namespaces.

---

## 🔍 **6. Can you explain how mapped types work?**

### ✅ Answer:
Mapped types transform properties of a type:

```ts
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

type User = { name: string; age: number };
type ReadonlyUser = Readonly<User>;
```

Used to build utility types like `Partial`, `Required`, `Readonly`, etc.

---

## 🔍 **7. What is the difference between interface merging and type intersections?**

### ✅ Answer:
- **Interface Merging**: Automatic, across multiple `interface` declarations.
- **Type Intersections (`&`)**: Combine multiple types into one.

```ts
type A = { a: string };
type B = { b: number };
type C = A & B; // { a: string; b: number }
```

Intersections can be more flexible, but less intuitive in edge cases.

---

## 🔍 **8. How does TypeScript handle overloads and why are they needed?**

### ✅ Answer:
Function overloads enable multiple signatures with distinct parameter types.

```ts
function add(a: number, b: number): number;
function add(a: string, b: string): string;
function add(a: any, b: any): any {
  return a + b;
}
```

They help provide developer-friendly IntelliSense while maintaining runtime flexibility.

---

## 🔍 **9. How would you create a type-safe event emitter?**

### ✅ Answer:

```ts
type Events = {
  login: { user: string };
  logout: void;
};

class Emitter {
  private handlers: { [K in keyof Events]?: ((payload: Events[K]) => void)[] } = {};

  on<K extends keyof Events>(event: K, handler: (payload: Events[K]) => void) {
    (this.handlers[event] ||= []).push(handler);
  }

  emit<K extends keyof Events>(event: K, payload: Events[K]) {
    this.handlers[event]?.forEach(fn => fn(payload));
  }
}
```

This ensures full type-safety for both `on` and `emit` calls.

---

## 🔍 **10. What are template literal types?**

### ✅ Answer:
Introduced in TS 4.1, they allow construction of string literal types from unions:

```ts
type Lang = 'en' | 'fr';
type Msg = `welcome_${Lang}`; // "welcome_en" | "welcome_fr"
```

---

## 🔍 **11. What are recursive types?**

### ✅ Answer:
Types that reference themselves — useful for trees, JSON, etc.

```ts
type Json = string | number | boolean | null | Json[] | { [key: string]: Json };
```

Watch out for depth limitations — TS can't handle infinitely deep types.

---

## 🔍 **12. How would you strongly type form field values based on a schema?**

### ✅ Answer:

```ts
const formSchema = {
  name: "string",
  age: "number"
} as const;

type Schema = typeof formSchema;
type FormValues = {
  [K in keyof Schema]: Schema[K] extends "string" ? string : number;
};

// Result: { name: string; age: number }
```

---

## 🔍 **13. How does discriminated unions help with exhaustiveness checking?**

### ✅ Answer:
TS ensures all possible cases are handled using `never`:

```ts
type Shape = { kind: "circle"; r: number } | { kind: "square"; size: number };

function area(shape: Shape): number {
  switch (shape.kind) {
    case "circle": return Math.PI * shape.r ** 2;
    case "square": return shape.size ** 2;
    default:
      const _exhaustive: never = shape; // Error if case is missing
      return _exhaustive;
  }
}
```

---

## 🔍 **14. Can you create a utility type that makes all properties of a type optional recursively?**

### ✅ Answer:

```ts
type DeepPartial<T> = {
  [P in keyof T]?: T[P] extends object ? DeepPartial<T[P]> : T[P];
};
```

---

## 🔍 **15. What's the difference between `extends` and `implements`?**

### ✅ Answer:
- `extends` is used for **inheritance** (class-to-class or type-to-type).
- `implements` enforces that a class conforms to an interface.

```ts
interface A { x: number }
class B implements A { x = 1 }
class C extends B {}
```

---

