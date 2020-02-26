# NPM / YARN

## CLI
- npm intall
  - yarn
- npm install --save package
  - yarn add package
- npm install package --save-dev
  - yarn add package --dev
- npm update --save
  - yarn upgrade
- npm install package -g
  - yarn global add package
- npm uninstall -g <packageName>

## package.json version
- version format: <symbol>x.x.x
  - 1st number: major
  - 2nd number: minor
  - 3rd number: patch 
- symbols
  - ^: last two numbers can change
  - ~: only the last number can change

## reference
- https://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json/25861938#25861938