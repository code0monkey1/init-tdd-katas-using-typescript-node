## Initial Project Setup

1. Create a new directory for your project and navigate to it in the terminal.

1. Initialize a new Node.js project by running the following command: 
`npm init -y`

1. Install the necessary dependencies by running the following command: 
`npm install --save-dev jest typescript ts-jest @types/jest`

1. jest is the testing framework we will be using.
typescript is the programming language we will be using`ts-jest`is a package that allows Jest to work with TypeScript.

1. `@types/jest`
 provides TypeScript type definitions for Jest.

1. Create a `tsconfig.json`
 file in the root directory of your project with the following configuration:
 
      ```json
      
         {
           "compilerOptions": {
             "target": "es6",
             "module": "commonjs",
             "esModuleInterop": true,
             "outDir": "dist",
             "sourceMap": true
           },
           "include": ["src/**/*"],
           "exclude": ["node_modules", "**/*.spec.ts"]
         }
      ```
      +  `target` :
          specifies the version of ECMAScript to target.  
      + `module`:
          specifies the module system to use.
      + `esModuleInterop` :
          allows for interoperability between CommonJS and ES modules.
      + `outDir` :
          specifies the output directory for compiled TypeScript files.
      + `sourceMap` :
          generates source maps for debugging.

1. Create a 
`jest.config.js` 
 file in the root directory of your project with the following configuration:

    ```json
     
       module.exports = {
         preset: 'ts-jest',
         testEnvironment: 'node',
         testMatch: ['**/*.spec.ts'],
         moduleNameMapper: {
           '^@/(.*)$': '<rootDir>/src/$1'
         }
       }
    ```

      + `preset`:
       specifies the Jest preset to use.
      + `testEnvironment`:
       specifies the environment in which to run tests.
      + `testMatch`:
       specifies the pattern for test files.
      +`moduleNameMapper`:
       maps module names to file paths.

1. Create a src
 directory in the root directory of your project.

    >Create a 
    >src/index.ts
    >file with the following code:
    
    ```javascript
       export const add = (a: number, b: number): number => {
         return a + b
       }
    ```
    > Create a src/index.spec.ts file with the following code:
    
    ```
    javascript
       import { add } from '@/index'
    
       describe('add', () => {
         it('adds two numbers', () => {
           expect(add(1, 2)).toBe(3)
         })
       })
    
    ```
1. Add the following scripts to the 
      ```json
        package.json
         file:
           "scripts": {
             "test": "jest"
           }
      ```
1. Run the tests by running the following command: `npm test`
   
1. That's it! You now have a Node.js project with Jest and TypeScript support. The add function in `src/index.ts` can be used in other parts of your project, and you can add more tests to `src/index.spec.ts`
 as needed.