# git stuff
- Stuff I rarely use but have to look up every time when I do
- Stuff I spent a lot of time explaining to other people


# Forking someone else's repo
- fork the repo via the Github GUI
- get the clone URL from the fork in your personal account and clone the repo
- `git remote add upstream git@github.com: ACCOUNT/REPO` where
  - `ACCOUNT` is the account that owns the canonical repo
  - `REPO` is the name of the repo at `ACCOUNT`


# git-rebase flow
- assumes the canonical repo is called `upstream` and that you are
working on a fork called `origin`

```
# Work on code:
git checkout -b <branch>
# change some stuff
# git commit

# Ready to get PR:
git push
# then open a PR through the GUI

# PR approved - merge the change
git checkout master
# get a lock on the repo
git pull upstream master
git checkout <branch>
git rebase -i master
# go thru the rebase process; squash all into one commit
git checkout master
git merge --ff-only <branch>
# look things over after the merge
git diff upstream master
git log upstream/master..
# git commit --amend to fix the commit message if necessary
git push # updates personal repo
git push upstream master # updates canonical master (if permitted; otherwise a maintainer will do it)

```
