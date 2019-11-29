## git

* git init
* git add
* git commit 
* git status
* git pull = git fetch + git merge
* git pull –rebase = git fetch + git rebase


[name][story/defect number] <What/Why you did>
[Ze][#OR-596] feat: Check empty fields on front-end


# simple workflow
```
git pull -r --autostash // get latest code (while reserve current change)
if conflict
	git rebase --continue
git commit -m
npm test
git push

```