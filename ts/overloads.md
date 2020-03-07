# Understanding overloads

## in a nutshell
sometimes a function may have multiple return types which are ambiguous at compile time. Overloads allow for repeated calls to a function which demonstrate to the compiler what should be returned depending on input.

## Problem
```ts
// Type definition of RGB
type RGB = {
  r: number;
  g: number;
  b: number;
}

// Simple function that takes in two arguments (RGB or string and percentage). It returns either an RGB object or string
function colorShade(color: RGB | string, percent: number): RGB | string {
  ...
} 
```

Running the above will result in an error upon compiling. The compiler doesn't know what the return type will be.

## Solution 
Create overloads for the function before it is invoked! 

```ts
colorShade(color: string, percent: number): string; // if colorShade receives a string as an argument: return a strung

colorShade(color: RGB, percent: number): RGB; // if colorShade receives an RGB object as an argument: return an RGB object

function colorSHade(color: RGB | string, percent: number): RGB | string {
  ...
}
```
## Notes
When creating overloads you list the declarations from the most specific to the most general case

This is a really simple case from [this](https://engineering.datorama.com/demystifying-function-overloading-in-typescript-eb9f8ca6b87d) article. more examples [here](https://dev.to/krzysztofzuraw/typescript-function-overloads-1iff), and [here](https://medium.com/@kevinkreuzer/typescript-method-overloading-c256dd63245a)

[overloads in TypeScript docs](https://www.typescriptlang.org/docs/handbook/functions.html)