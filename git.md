## git

- 
- init git: git init
- stage files: git add
- commit files: git 
- git status
- git pull = git fetch + git merge
- git pull –rebase = git fetch + git rebase



## git shortcuts
- gp: git push
- gst: git 
- gup: git pull --rebase

[name][story/defect number] <What/Why you did>
[Ze][#or-596] feat: Check empty fields on front-end

# simple workflow

```
git pull -r --autostash // get latest code (while reserve current change)
if conflict
	git rebase --continue
git commit -m
npm test
git push

```
