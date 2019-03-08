# How to Integrate Eslint and Prettier in React

---

## What is Eslint and Prettier

**Eslint** is a static tool that points out differences in styles. You can preset styles via config files and when running command it will show errors on what doesn't match specific rules.

**Prettier** is basically the same tool but dynamic. It actively formats your code (if you set autoformat save to true). You have to make sure you set up prettier to not intefere with the rules in place be eslint.

**Husky** is used to run linting before a commit/push (you can configure accordingly).

_All of these tools are npm packages._

## Create React App

Simple enough, just go through normal steps

```sh
$npm install -g create-react-app
$create-react-app <projectName>
```

Make sure you navigate into the project directory

```sh
cd <projectName>
```

## Install

Install ESLint and its configuration by Airbnb

```sh
$npm i -D eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react
```

Install Prettier and its config to avoid conflict with Eslint

```sh
$npm i -D prettier eslint-config-prettier eslint-plugin-prettier
```

Install Husky to prevent users committing 💩

```sh
$npm i -D husky lint-staged pretty-quick
```

**husky**: Will run npm script before the committing the code.

**lint-staged**: Will run custom script on the filtered files by the extensions like .js or .jsx

**pretty-quick**: Will prettify your code.

## Add scripts into Package.json

In the scripts section attach on:

```
"precommit": "NODE_ENV=production lint-staged"
```

This runs before the commit and runs custom scripts called lint-staged

```
"lint-staged": {
  "*.{js,jsx}": [
    "pretty-quick --staged",
    "eslint src/ --fix",
    "git add"
  ]
}
```

This will use pretty quick to format code

If something does not resolve, then eslint checks the code agains the eslint rules and give errors if not solvede and stop the commit

## Set the Config Rules

### Eslint

Create .eslintrc config file in the root of your project and add this into that file

```json
{
    "extends": ["airbnb", "prettier", "prettier/react"],
    "plugins": ["prettier"],
    "rules": {
        "react/jsx-filename-extension": [
            1,
            {
                "extensions": [".js", ".jsx"]
            }
        ],
        "react/prop-types": 0,
        "no-underscore-dangle": 0,
        "import/imports-first": ["error", "absolute-first"],
        "import/newline-after-import": "error"
    },
    "globals": {
        "window": true,
        "document": true,
        "localStorage": true,
        "FormData": true,
        "FileReader": true,
        "Blob": true,
        "navigator": true
    },
    "parser": "babel-eslint"
}
```

### Prettier

Create .prettierrc config filr in the root of your project add add this into that file

```json
{
    "singleQuote": true
}
```

## Extras

Make sure to add in plugins to your IDE to support eslint and prettier

Keep in mind I need to review all these steps BUT if prettier is not functioning install it globally

```sh
$npm install -g prettier
```
