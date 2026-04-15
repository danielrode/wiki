# Remove (undo) the last commit from git

	git reset HEAD^

Then, if you want to clear (reset) the staging area as well, run:

	git reset --hard HEAD

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

# Diff both staged and unstaged changes, and view with delta, ignoring whitespace

	git diff HEAD -w | delta

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

# Selective/partial merge another branch

Just switch to branch B (the branch you want to merge), `checkout --patch
branchA` (the branch you want to merge into), commit these changes to
branchB, then merge branchB into branchA.

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

# Squash last 3 commits on current branch

	git reset --soft HEAD~3
	git commit -m MSG

# Find which commit last modified a given line

	git blame FILE

# Selectively stage/add file for commit

	git add -p FILE

# Search all git commits (file content) history

	git rev-list --all | xargs git grep QUERY

# Show commit message and commit date for a list of commit IDs/hashs

	NEWLINE_SEP_COMMITS | xargs -d \n git show --no-patch --oneline --pretty=format:'%C(blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an [%GK %G?]%C(reset)%C(bold yellow)%d%C(reset)'

# Dump/show contents of a file at from a specific commit

	git show COMMIT:FILE

# Maintain local patches while still contributing and receving from upstream

This is useful when you need to keep up to day with upstream (and keep that
code checked out) while also maintaining a set of local patches that you also
always need checked out. I will use my ~/code repo, master (the shared branch),
and patches (master plus local-patches branch) in my examples below.

To pull changes from upstraem to machine with local patches branch, run:

	cd ~/code
	git checkout patches
	git fetch origin master:master
	git rebase master

To update local master branch with non-patch changes made to patches branch
(since the patches branch is always checked out on the machine that has it,
changes are usually made there that need to be upstreamed), run (in fish):
NOTE: This assumes the patches branch has only had *one* non-patch commit since
the patches one (its log should look like COMMIT_IN_COMMON_WITH_MASTER_BRANCH >
PATCHES_COMMIT > CHANGES_TO_UPSTREAM_COMMIT).
NOTE: This also assumes you only have one commit (in the whole repo) with the
name "local patches".

	cd ~/code
	git checkout patches
	set td (mktemp -d)
	git worktree add "$td" master
	git -C "$td" cherry-pick "$(git rev-parse HEAD)"
	git worktree remove "$td"  # Removes tmp dir and git links to it
	set td2 (mktemp -d)
	git branch patches-tmp master
	git worktree add "$td2" patches-tmp
	set gcid (git log --all --grep='^local patches$' --format=%H | head -1)
	git -C "$td2" cherry-pick "$gcid"
	git worktree remove "$td2"
	git switch patches-tmp
	git branch -D patches
	git branch -m patches-tmp patches
