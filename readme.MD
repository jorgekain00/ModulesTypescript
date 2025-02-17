# this feature uses module

run the command to run the project
```
npx nodemon --require esm ./dist/index.js
```


## basic setup

1. at tsconfig change target to new modern js
2. remove module option ints config
3. add module option at package json

#learning typescript

## commands

### init project
```
npm init
```

previous create package.json
 

### instal typescript

```
npm install typescript --save-dev
```
#### install globally with selected version
```
npm install --global typescript@5.7.2
```

### Generate tsconfig.json

```
npx tsc --init
npx tsc --init --sourceMap
```

### TypeScript definitions

```
npm install --save-dev @types/node
```

### JSOC
```
npm install --save-dev jsdoc
```

### create launch file for debug purposes

1. Create launch file (Run and Debug Section)
2. Select Node.js

This will create the following file. Update "program" node with output dir (dist) and the main javascript file.

```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [

        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "skipFiles": [
                "<node_internals>/**"
            ],
            "program": "${workspaceFolder}\\dist\\CheckingProp.js",
            "outFiles": [
                "${workspaceFolder}/**/*.js"
            ]
        }
    ]
}
```
3. Compile
4. Debug with F5

### run compiller

```
npx tsc
tsc main.ts // Compile a specific file (main.ts) to JavaScript
tsc src/*.ts // Compile any .ts files under the 'src' folder to JavaScript
tsc app.ts util.ts --outfile index.js // Compile two TypeScript files (app.ts and util.ts) into a single JavaScript file (index.js)
```

### tsc watch
```
tsc --watch
```
This command starts a TypeScript compile with --watch parameter, with the ability to automaticalle recompile TypeScript files whenever ther are modified.


### automatic compilation, on success run the script
```
npx tsc-watch --onsuccess "node dist/index.js"

npx tsc-watch --onsuccess "\`"node dist\index.js\`""   // in case powershell raise a warning
```
Requirement:  add tsc-watch  to package "tsc-watch "

### hot reload

 
 1. Ctrl + P and select Tasks:"Configure Default Build Task"
 2. Select tsc:watch - tsconfig.json

 This Will create tasks.json:

 ```
 {
	"version": "2.0.0",
	"tasks": [
		{
			"type": "typescript",
			"tsconfig": "tsconfig.json",
			"option": "watch",
			"problemMatcher": [
				"$tsc-watch"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"label": "tsc: watch - tsconfig.json"
		}
	]
 }
 ```
 
 3. Ctrl + P and select Tasks:Run Build Task


## Starting the Compiler Using NPM

inside package.json:
```
{
  "name": "tools",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "tsc-watch --onsuccess \"node dist/index.js\""
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "tsc-watch": "^4.2.9",
    "typescript": "^4.2.2"
  }
}
```


run the following command:

```
npm start
```

 ## Useful NPM Commands
| Command                              | Description                                                                       |
|:-------------------------------------| :---------------------------------------------------------------------------------|
|npm install                           | This command performs a local install of the packages specified in the package.json file. |
|npm install package@version           | This command performs a local install of a specific version of a package and updates the package.json file to add the package to the dependencies section.|
|npm install --save-dev package@version |This command performs a local install of a specific version of a package and updates the package.json file to add the package to the devDependencies section, which is used to add packages to the project that are required for development but are not part of the application.|
|npm install --global package@version |This command will perform a global install of a specific version of a package.|
|npm list           |This command will list all the local packages and their dependencies.|
|npm run            |This command will execute one of the scripts defined in the package.json file.|
|npx package        |This command runs the code contained in a package.|

### lib Compiler Option

tsconfig

```
{
    "compilerOptions": {
        "target": "es5",
        "outDir": "./dist",
        "rootDir": "./src",
        "noEmitOnError": true,
        "lib": ["es5", "dom", "es2015.collection"]
    }
}
```