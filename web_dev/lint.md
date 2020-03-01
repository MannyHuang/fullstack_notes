# Linting: automatic code style check and format

## why
- make sure code follows convention and avoid pitfalls

## linters
- lint typescript: tslint
	- standard config: tslint:recommended
- lint scss: stylelint
	- standard config: stylelint-config-standard

## code formatter
- prettier

## add format command in package.json 
- change package.json
  ```json
  // package.json
  {
    "scripts": {
      "format": "npm run prettier && npm run lint:ts && npm run lint:style",
      "prettier": "prettier --config ./.prettierrc --write 'src/**/!(polyfills).{ts,scss}'",
      "lint:ts": "tslint -c tslint.json 'src/app/**/!(demo|testing)/!(polyfills).ts' --fix",
      "lint:style": "stylelint \"src/app/**/*.scss\" --fix",
    }
  }
  ```
- run cli command to format && lint
  - npm run format


## add precomit check
- lint staged: run shell commands before commit
  - ensure other linters are setup first
  - specify a lint or format command for each filename pattern
  - cmd will be run against staged file
  - npx mrm lint-staged
- husky: simplify git hooks
  - allows configuring pre-commit & pre-push git hooks
- example config
    ```json
    // package.json
    {
      "lint-staged": {
        "src/app/**/!(demo|testing)/!(polyfills).{ts,scss}": [
          "prettier --config ./.prettierrc --write"
        ],
        "src/app/**/!(demo|testing)/!(polyfills).ts": [
          "tslint -c tslint.json --fix"
        ],
        "src/app/**/*.scss": [
          "stylelint \"src/**/*.scss\" --fix"
        ]
      },
      "husky": {
        "hooks": {
          "pre-commit": "lint-staged",
        }
      },
    }
    ```

## commit message 
- commit message standard: angular convention
  - https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit
- commit template
  ```js
  <type>(<scope>): <subject>
  <BLANK LINE>
  <body>
  <BLANK LINE>
  <footer>
  ```
- commit messages exmaples
  ```js
  fix(release): need to depend on latest rxjs and zone.js

  The version in our package.json gets copied to the one we publish, and users need the latest of these.
  ```

  ```js
  feat(bazel): enable ivy template type-checking in g3
  ```
- more examples
  - https://github.com/angular/angular/commits/master