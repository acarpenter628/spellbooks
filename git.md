Undo:
   Undo the last commit and discard the changes completely:
      git reset --hard HEAD~1
   Undo the last commit (remove it from your history), but keep the changes from that commit in the working copy
      git reset HEAD~1 
   History preserving, undo a previous commit
      git revert -n <sha>

Look into a merge without commit so I can review first and keep mac/linux commits separate withotu using PRs


Diff:
   See the diffs in a commit:
      git show <sha>
   git diff --staged
      diff staged vs repo
   git diff stash@{1}
      diff stash vs working copy
   different branch/sha:
      diff [branch/sha] -- file
   Ignore whitespace
      git diff -w
   exclude certain filetypes / folders
      git diff -- ':!*.out' ':!*/folder/*'


Merging:
   git merge --squash <branchname>
      pull branch into staging area
      does stage, but doesn't commit
   git merge --no-commit <branchname>
      Merge without committing.
   Cherry pick without committing :
      git cherry-pick -n <HASH>
   Pull changes if you're alrady mid merge (in conflicted state):
      git checkout --theirs .
      or git checkout --ours .

Stash:
   restore stashed modification but do not remove from stash list
      git stash apply n	
         (n specifies stash number, default is 0 which is most recent stash)
   remove stashed state from stash list but don't apply
      git stash drop n	
   clear stash list
      git stash clear	


Remove unversioned files:  
   git clean -fd
      -n for dry run
      -i for interactive
         Not 100% sure how this works, I thought i was creating a list to clean, but maybe it was to save?

Remove from repo without deleting:
   File:  git rm -f --cached  folder/derp.txt
   Folder:  git rm -f -r --cached  folder/subfolder/


Branch with sorting: (I think I put one of these in my gitconfig?)
   git branch -v --sort=-committerdate  # DESC
   git branch -v --sort=committerdate  # ASC
