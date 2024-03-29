# Typescript (TS) Notes

In the following type-name means "basic type like number or string" or name of a defined type.

## Installing, configuring and compiling TS

TS installation: `npm install -g typescript ts-node`

After installation the `tsc` command is used to compile .ts files into .js files. Compiling app.ts: `tsc app.ts`

Auto compiling single file app.ts: `tsc app.ts --watch` or `tsc app.ts -w`

### TS Compiler Configuration (tsconfig.json)

For auto-compiling all TS files in a project and to use other TS compiler configurations we need to initialize the project for TS.

To initialize a project for TS: `tsc --init`

This will create 'tsconfig.json' configuration file which has a large number of settings with good defaults.

After tsconfig.json is created we can use following commands:

For compiling all .ts files once: just use `tsc`

For auto-compiling .ts files use `tsc --watch` or `tsc -w`

The tsconfig.json is consists of `"option name" : option value ` pairs, where value can be primitive or array. By default TS uses default values for various configuration options. We can add more settings in 'tsconfig.json'. Following are some examples:

`"exclude": [files or paths]` where value of setting is an array of files or paths to be excluded (i.e. these .ts files will not be compiled).
we don't need to use exclude but if we do, then we should add at least "node_modules" in the array like `"exclude": ["node_modules"]`. if exclude is not added then node_modules are excluded by default.
`"include": [files or paths]` where array lists the files or paths to be included. If 'include' property is not specified the TS will compile all the .ts files in a project.

The tsc command compiles the [includes] minus [excludes] .ts files set, note that [excludes] filters the includes files/folder

In general tsc use default values for most of the settings in tsconfig.json if we do not set them ourselves
**but if we do set a setting which has an array as value then its default is gone and we are responsible to set all needed values in the array.**

Along with .js file the tsc command also generates a `.d.ts` file, it is a TypeScript Declaration file. While compiling a .ts file, the compiler strips away all the type information and stores it in this declaration file. The generated .js file (JavaScript file) will not contain any TS specific information.

## TS Concepts

In general TS implicitly infers a variable type based on initial assigned value e.g. for "let x = 5" TS assumes type is "number".

Or the coder can explicitly assign a type to a variable via "_type annotation_" which is like `variable: type-name` e.g.:
`let name: string`; or `let age: number`; etc. Note it is variable name followed by a colon followed by type-name (VCT). There may be optional spaces which an ide/editor will adjust for pretty-formatting.

### Functions Typing

Function parameters type annotation is exactly same as for any other variable.
For function return type annotation place colon+space+type-name(CST) after closing(right) parenthesis.

```ts
function sumTwoNumbers(num1: number, num2: number): string {
return `result is ${num1+num2}`;
}
and for arrow function it is very similar:

let sum = (x: number, y: number): number => {
return x + y;
}

```

Anonymous functions are a little bit different from function declarations. When a function appears in a place where TypeScript can determine how it’s going to be called, the parameters of that function are automatically given types.

### Type-Inference and Contextual Typing

In the following example no type annotations are given, but TypeScript can spot the bug using contextual typing for the anonymous function.

```ts
const names = ["Alice", "Bob", "Eve"];
names.forEach(function (s) {
  console.log(s.toUppercase());
  // TS give following error
  // Property 'toUppercase' does not exist on type 'string'. Did you mean 'toUpperCase'?
});
```

the above is called "contextual typing" as TS infers types from context.

In general Typscript tries to infer types in most cases. If inference is not possible it assigns the type "any".
But if `noImplicitAny = true` flag is set then it generates an error.

TS raises an error if a variable type is established (via inference or explicit annotation ) and later in the code the type of variable is apparently changes somehow.

an "assertion" about a value is an explicit casting of type using "as + space + type-name";

A trivial assertion example: `const x = "hello" as string;` which is equivalent of `const x: number = "hello";`

A more useful assertion example: `const myCanvas = document.getElementById("xyz") as HTMLCanvasElement;`

TS by itself can only infers that document.getElementById() will give some kind of HTMLElement but the coder based on his/her knowledge tells TS, by using above assertion, that the returned object will be HTMLCanvasElement.

Another syntax for making assertion is to use angular brackets (of course not in .tsx files where < and > are used for jsx syntex):

The above example using < >: `const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");`

Note that TS does infer DOM object types to a certain extent.

Non-null Assertion Operator (Postfix "!") asserts that the value is neither "null" nor "undefined"

example: `const prop1 = obj1.prop1!` assures TS that obj1.prop1 is neither null nor 'undefined'

"narrowing" means using "if", "else if" or "else" block. It helps TS in reconciling types with corresponding methods or operations.

### TS Benefits

1.  TS strictly defines what a given variable can contain. A variable have to be of same.

### Combining Types:

Union Type: is a type obtained by combining types with '|' .

For example type1|type2 means a variable can be of type1 or type2

The numOrStr variable defined by `let numOrStr: number|string = 55` can be a number or a string but none other type

TS will only allow an operation if it is valid for every member of the union. For example, if you have the union string | number, you can’t use methods that are only available on string:

The solution is to narrow the union with code, the same as you would in JavaScript without type annotations. Narrowing occurs when TypeScript can deduce a more specific type for a value based on the structure of the code.

For example, TypeScript knows that only a string value will have a typeof value "string":

```ts
function printId(id: number | string) {
  if (typeof id === "string") {
    // In this branch, id is of type 'string' so using string function is ok
    console.log(id.toUpperCase());
  } else {
    // Here, id is of type 'number'
    console.log(id);
  }
}
```

If in a union all the members have something in common. Like arrays and strings both have a slice method. If every member in a union has a property in common, we can use that property without narrowing:

### Type Aliases

A "type alias" is a name for any type. The syntax for a type alias is "type typename = type definition":
type definition can be as simple as basic type like "number" or a a "combined type" (like unions etc.). In the following Point is defined as an object type

```ts
type Point = {
  x: number;
  y: number;
  z?: number;
};
```

then we can use Point any place we wanted `{x: number; y: number; z: number}` .
note that the question mark in "z?" means that z is optional. The TS will not raise error if it does not see z in Point type objects.
Note by convention type aliases are capitalized (e.g. Point not point).

### Interface

An "interface" in TS is an object-like set of "key:type" pairs. Conventionally interface name start with an upper case.:
(An interface declaration is another way to name an object type like Type aliases)

```ts
interface User {
  name: string;
  id: number;
}
```

Note that each key:type pair is separated by ";" while in an object "," is used to separate entries. Although you may also use "," in object type definition as separator. But it is good practice to use ";" to show that it a type not the object.

Now User becomes a type (like number , string) and can be used with any object variable after a colon and space.

```ts
const user: User = {
  name: "Hayes",
  id: 0,
};
```

To add new field (key/type) pair in an interface we use the following:

```ts
interface User {
  age: 35;
}
```

Type aliases and interface are very similar. Note the following though:

You can not add new fields to a type alias once it is defined. But for interface you can as in User above.
Interface is mainly for objects but type aliases are more general.

To extend interface we use "extends" just like JS class "extends" :

```ts
interface NewInterface extends OldInterface {
newProp: type-name
}
```

to extend a type alias for an object we use "&" :

```ts
type NewType = OldType & {
newProp: type-name
}
```

For objects typing, it is highly recommended to use 'interface' not 'type alias'.

### Array Type

To declare an array type simply add "[]" to type-name like const `const arr1: number[];` declares that arr1 is an array of numbers.
Another way for array type is to use Array before type-name in angle brackets. like `const arr2: Array<string>`, or `Array<number>` .

### Type Assertion

Type assertion means an explicit casting of the type of a variable based on coder's knowledge about that variable (which TS can't infer).
type assertion is very simple: just use "variable as type-name"
TS does a lot of inferring about types all across a TS code based on its knowledge about JS constructs and even DOM nodes type and DOM methods return variables higher level types. But it still would not know the specific type of these variables. For example, if you’re using document.getElementById, TypeScript only knows that this will return some kind of HTMLElement, but you might know that your page will always have an HTMLCanvasElement with a given ID. In this situation, you can use a type assertion to specify a more specific type:

const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;

Note that because of TS's DOM support you also have DOM related variable types such as HTMLCanvasElement available to be specified. In other words type-names or type types (no pun intended) are not limited to "number", "string" etc.

TS only allows type assertions which convert to a more specific or less specific version of a type. This rule prevents “impossible” coercions like:

const x = "hello" as number; (will give an error)

### Literal Types

Type could be any literal or any union or any array of literals. In that case the variable's domain space is limited to these literals. Single literal type is not useful because you can simulate it by using "const" instead of "var" or "let". However union or array of literal provide many uses.
Union of literals type is very useful because it checks for if a variable has a values from a specified set of values.

let color: "red"|"blue"|"green"; (will only allow these colors)

To declare an object's property as literal (not changeable) you use "as value" assertion.

`const employee = {name: "john", company: "Microsoft" as "Microsoft"}`

this is a tedious way, you basically repeat the property value. So to declare an object's all properties as literal you can use the assertion suffix "as const"

`const john = {name: "john", company:"Microsoft"} as const;`

In JS null means variable is "absent" while undefined means variable is there but is "un-initialized"

In TS with strictNullChecks "on", when a value is null or undefined, you will need to test for those values before using methods or properties on that value. Just like checking for undefined before using an optional property, we can use narrowing to check for values that might be null:

when you know for sure that a variable can’t be null or undefined you can use non-null assertion postfix "!" after that variable, then TS will not raise any warning even without narrowing (narrowing means checks ("if blacks") null or undefined) e.g. console.log(x!.toFixed()); here the coder tells TS that x will not be null/undefined so please don't yell.

### enum Type:

Almost all of the additional typing-related code that is written to an otherwise JS code will be removed after TS compilation. TS's enum is an exception.  
Enums are a feature added to JavaScript by TypeScript which allows for describing a value which could be one of a set of possible named constants. Unlike most TypeScript features, this is not a type-level addition to JavaScript but something added to the language and runtime.

## Narrowing and Type Guards:

TS analyzes JS constructs like "if/elseif" etc. and if these checks provide paths for allowable types then TS regards these checks paths as "type guard" and does not raise warnings.

The process of refining types to more specific types than the declared ones via "type guards" (or conditional blocks of code) is called "narrowing". In many editors(including vscode) we can observe these types as they change,

```ts
function padLeft2(padding: number | string, input: string) {
  if (typeof padding === "number") {
    return " ".repeat(padding) + input;
  }
  return padding + input;
}
```

In the above example padding can take 2 types of values number or string. Without

In JS constructs which expect boolean arguments like "if" (and logical && and || etc.) first “coerce” their conditions to booleans to make sense of them, and then choose their branches depending on whether the result is true or false. There are only few values that evaluate to false. These are 0, NaN, "" (the empty string), 0n (the bigint version of zero), null and undefined. All other values (including empty arrays) evaluate to true.
following JS/TS constructs (types of statements or expressions) help in "narrowing"

- assignment statements
- in and instanceOf operators
- Truthiness
- Equality
- control flow analysis

In the above 'narrowing' is handled with existing JavaScript constructs, however sometimes you want more direct control over how types change throughout your code.

To define a user-defined type guard, we simply need to define a function whose return type is a "type predicate":

```ts
type Fish = { swim: () => void };
type Bird = { fly: () => void };
declare function getSmallPet(): Fish | Bird;
function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}
// ---cut---
// Both calls to 'swim' and 'fly' are now okay.
let pet = getSmallPet();

if (isFish(pet)) {
  pet.swim();
} else {
  pet.fly();
}
```

The `void` in swim() and fly() means that these methods return nothing.
Note that isFish() return type in the JS code should be a boolean (and it will be on code execution ) but in the TS layer it is annotated as "pet is Fish". This "pet is Fish" is a "type predicate". You may think that boolean true from isFish is equivalent of narrowing pet's type to Fish from a union of Fish|Bird/
Also, classes can use "this is Type" to narrow their type

### Some observations about Typescript

- TypeScript is a "structurally typed type system". Type annotations for two variables may come from 2 different annotations (like one used type-alias while other used interface) but if their type-structure is same then TS treat them equivalently.

### Object Typing

Both interface and type-alias can be used for typing an object literal:

type Employee = {
name: string;
age: number;
};

Interface Employee1 {

}
