---
description: >-
  This page will outline the steps required to get TypeScript and Unit testing
  working in Repl.it.
---

# TypeScript in Repl

TypeScript is supported out of the box in Repl. The challenge is to get Unit testing working. I believe that Unit testing is a really strong way of setting tasks which demand an understanding of how algorithms work, without having to actually code the algorithms. It also exposes students to the concept of unit testing, which should be useful for their projects and certainly useful for any career in software engineering. To summarise, unit testing

* Forms a good basis for tasks
* Builds good habits as a software engineer

To get a Repl working there are a few things we need to do.

1. Create TypeScript Repl
2. Install various packages required by the testing framework (Jest)
3. Setup Scripts in package.json
4. Create various JSON and JavaScript configuration files
5. Create a simple module that we can test
6. Create a unit test using Jest
7. Configure Repl to run the Unit test when the user clicks 'Run'

The documentation for Jest can be found here

{% embed url="https://jestjs.io" %}

## 1. Create a TypeScript Repl

Supported by Repl out of the box, this step is very easy.

![](<../.gitbook/assets/image (83).png>)

## 2. Install the npm packages

Use the package manager to add dependencies to our project.

* @babel/core
* @babel/preset-env
* @babel/preset-typescript
* @types/jest
* babel-jest
* jest
* ts-jest
* typescript

![](<../.gitbook/assets/image (85).png>)

At the time of writing, these were the precise version numbers that worked together.

```
"@babel/core": "^7.16.7",
"@babel/preset-env": "^7.16.8",
"@babel/preset-typescript": "^7.16.7",
"@types/jest": "^27.4.0",
"babel-jest": "^27.4.6",
"comp-sci-maths-lib": "^10.2.0",
"jest": "^27.4.7",
"ts-jest": "^27.1.3",
"typescript": "^4.5.4"
```

Search for each package, then click on the + button, it will start the installation process. After a while it will have downloaded the package and it will show the green status message.

![](<../.gitbook/assets/image (84).png>) ![](<../.gitbook/assets/image (82).png>) ![](<../.gitbook/assets/image (88).png>)

## 3. Setup Package Scripts

A node.js project contains a `package.json` file. This lists all the meta-data about the project, including the commands which can be run.

By default the scripts section looks like this.

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

Replace it with the following

```json
  "scripts": {
    "prebuild": "tslint -c tslint.json -p tsconfig.json --fix",
    "build": "tsc",
    "prestart": "npm run build",
    "start": "node dist/index.js",
    "test": "jest"
  },
```

## 4. Jest Configuration Files

Add the following files to the repl (literally just copy/paste the contents)

### `babel.config.js`

```
module.exports = {
    presets: [
      [
        '@babel/preset-env',
        {
          targets: {
            node: 'current',
          },
        },
        '@babel/preset-typescript',
      ],
    ],
  };
```

### `jest.config.js`

```
/** @type {import('ts-jest/dist/types').InitialOptionsTsJest} */
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
};
```

### `tslint.json`

```
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:recommended"
    ],
    "jsRules": {},
    "rules": {},
    "rulesDirectory": []
}
```

### `tsconfig.json`

There will already be a file with this name, replace it's contents with the following

```
{
  "compilerOptions": {
    /* Visit https://aka.ms/tsconfig.json to read more about this file */
    /* Basic Options */
    // "incremental": true,                   /* Enable incremental compilation */
    "target": "es5", /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019', 'ES2020', or 'ESNEXT'. */
    "module": "commonjs", /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', 'es2020', or 'ESNext'. */
    // "allowSyntheticDefaultImports": true,  /* Allow default imports from modules with no default export. This does not affect code emit, just typechecking. */
    "esModuleInterop": true, /* Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'. */
    /* Advanced Options */
    "skipLibCheck": true, /* Skip type checking of declaration files. */
    "forceConsistentCasingInFileNames": true /* Disallow inconsistently-cased references to the same file. */
  }
}
```

## 5. Write Simple Module to Test

Let us create a simple module, I will create it in it's own named file (rather than use index) to more accurately reflect a larger project.

`simpleMaths.ts`

```typescript
export const highestCommonFactor = (a: number, b: number): number => {
  while (a !== b && a > 1 && b > 1) {
    if (a > b) {
      a -= b;
    } else {
      b -= a;
    }
  }

  return a;
}

```

## 6. Create a Unit Test

The `describe` function allows you to group a series of tests. The `test` function can be used for specific tests within that. You can nest calls to `describe` although I don't tend to.

Jest will pickup any files that end with `test.ts`, so I usually just make a test for each module, which has the same name but a `.test.ts` extension.

`simpleMath.test.ts`

```typescript
import { highestCommonFactor } from './simpleMaths';

describe("Simple Maths", () => {
  test("Highest Common Factor", () => {
    const resulta = highestCommonFactor(9, 6);
    expect(resulta).toBe(3);

    const resultb = highestCommonFactor(12, 15);
    expect(resultb).toBe(3);

    const resultc = highestCommonFactor(77, 49);
    expect(resultc).toBe(7);
  });
})
```

## 7. Configure Repl Run

Add a file called \`.replit\` to the Repl project with the following contents.

### `.replit`

```
run = ["npm", "test"]
```

When the user clicks on the Run button it will run the tests, try this now. They can take a while to run (5 or 6 seconds even for simple test). Programming natively this is much quicker.

If all goes well, you should be looking at something like this.

![](<../.gitbook/assets/image (87).png>)

If it doesn't go well, you will have to check if the error is a test failing, or some form of configuration error.

## Most Common Errors

### js vs json

I often create .json files instead of .js files (and vice versa) when copying from an existing project.
