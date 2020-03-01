# git

## cli
- init git: git init
- stage files: git add
- commit files: git commit
- push files: git push (gp)
- status check: git status (gst)
- pull file: 
	- git pull = git fetch + git merge
	- git pull –rebase = git fetch + git rebase (gup)

## workflow
- pull remote changes & then push all locally changed files
	```sh
	git pull -r --autostash # get latest code (while reserve current change)
	if conflict
		git rebase --continue
	git add .
	git commit -m
	npm test
	git push
	```
- ammend a commit (that is not pushed yet) with new message
	```
	git commit --amend -m 'a new message'
	```
- ammend a commit (that is not pushed yet) with new changes
	```sh
	git add newly_changed_file.md
	git commit --amend
	git push
	```

## commit message convention
- commit message standard: angular convention
  - reference: https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit
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

- commit message standard: tw standard
  - [name][story number] <What/Why you did>
  - example:
    ```js
    [Ze][#596] feat: added some crazy new feature
    ```