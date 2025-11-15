# Remove (undo) the last commit from git

	git reset HEAD^

# Modify/amend/edit commit that is not most recent

	git rebase -i COMMIT~1

Then follow directions git gives.

If you have already modified the working directory, commit changes, then run
the rebase command above and squash your new commit onto the COMMIT you want
to modify. To squash your new commit onto COMMIT, simply find the line with
your new commit ID, change 'pick' to 'squash', cut that line and paste it
directly underneath the COMMIT you want to modify. Then save and close the
editor.

Example:

	pick 133a3e6 # Add feature A
	pick d3e5486 # Add feature B
	pick d3e5486 # Change something else
	pick 5890e52 # Opps, fix typo in feature A before push

-->

	pick 133a3e6 # Add feature A
	squash 5890e52 # Opps, fix typo in feature A before push
	pick d3e5486 # Add feature B
	pick d3e5486 # Change something else

# Exclude some paths from commit

	git add . OR git add -u
	git reset -- PATH
	git commit -m "**MESSAGE**"

# Identify large files in git repo history

	"This shell script displays all blob objects in the repository, sorted from smallest to largest."

	git rev-list --objects --all \
	| git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' \
	| sed -n 's/^blob //p' \
	| sort --numeric-sort --key=2 \
	| cut -c 1-12,41- \
	| $(command -v gnumfmt || echo numfmt) --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest

	source: https://stackoverflow.com/a/42544963/1635116

# Show history of (view all changes for) a single file

	git log -p -- path/to/file

# See what has changed since the commit before the latest

	git diff HEAD^

# Include staged file(s) in diff

	git diff --cached

# Backup repo

	git bundle create /backup/path/filename --all

# Remove file from git repo (including all commits in history)

	git filter-branch --tree-filter 'rm -f <FILE_PATH_TO_ERASE>' HEAD

# List file changes for each commit in log

	git log --name-status

# Commit changes to another (existing) branch

	git stash
	git checkout BRANCH_NAME
	git stash apply
	git add .
	git commit -m "MESSAGE"

# Merge all changes from another branch as single commit

TODO

	git checkout master
	git merge --squash WIP
	git commit -m "Merged WIP"
	#https://stackoverflow.com/questions/3697178/merge-with-squash-all-changes-from-another-branch-as-a-single-commit

# "Merge" file(s) from another branch

	# TODO verify this works
	git checkout  OTHER_BRANCH  FILEPATH...
	git add FILEPATH...
	git commit -m MSG

# Selectively "merge" lines from file from another branch

	git checkout --patch  OTHER_BRANCH  FILEPATH
	git commit -m MSG

# Swap order (the two and from files) in diff

	git diff -R  A  B

# Diff list filenames only

	git diff --name-status  A  B

# Unstage/unadd all files

	git reset .

# List (ls) another branch

	git ls-tree OTHER_BRANCH

# Search file contents in another branch

	git grep  REGEX  OTHER_BRANCH

# Show commit ID of HEAD

	git rev-parse HEAD

# Squash last 3 commits on current branch:

	git reset --soft HEAD~3
	git commit -m MSG

# Find which commit last modified a given line

	git blame FILE

# Selectively stage/add file for commit

	git add -p FILE

# Search all git commits (file content) history

	git rev-list --all | xargs git grep QUERY
