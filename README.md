# Git

## basic
git clone a // bring down repository from github

$git status

$git add .

$git commit -m "some text"

$git push // send your changes to github

$git pull // get updates from github

$git checkout -b // create branch and switch to it

$git checkout b // switch to branch b

$git branch // list branches

$ gith branch -D b // delete branch b

$ git log // shows commits

# github branches

// If github has a branch test and you want to bring it down localy

$git fetch origin // update local repo

$git switch -c test origin/test // get the github branch (look in github for the branch name)

// Now you can push/pull normally

// Delete the branch in github and then locally

$git push --set-upstream origin b // push local branch b to github
// Only need to do this once, then your can use normal $git push and $git pull

# Merge

$git checkout a // checkout branch a. This is where you want to merge you code into

$git merge b // this will merge branch b into branch a

// rebase is an alternative

# rolling back code

// revert rolls code back by adding a commit (keeps history) safer

// rest re-writes history so it disapears

$ git reset --hard sha

// where sha is found via $git log and is the commit you want to go back to

ex.

123 commit 1

|

456 commit 2

|

789 commit 3

then git rest --hard 456 will take you to the state you were in for "456 commit 2"
