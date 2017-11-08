# Notes about git command
Some note useful when working with git

## Duplicate repository without forking
Create bare clone of source repository
```
git clone --bare https://github.com/exampleuser/old-repository.git
```
Mirror-push to the target repository.
```
cd old-repository.git
git push --mirror https://github.com/exampleuser/new-repository.git
```
Remove the temporary local repository you created in step 1.
```
cd ..
rm -rf old-repository.git
```

## Nested git command (worked on windows)
Export all modified files to diff.zip
```
git archive -o patch.zip HEAD $(git ls-files -m)
```

Export all commited files to diff.zip
```
git archive -o diff.zip HEAD $(git diff --name-only HEAD^ --diff-filter=ACMRTU)
```
Above command use option '--diff-filter=ACMRTU' to NOT get Deleted files, Unknown files, Broken Files
## Get log of unpushed git commit
```
git log origin/$branch_name..$branch_name
```
$branch_name: your branch name, ex: master
You can add '--oneline' to view short log

### Get list unpushed git commited files
```
git diff --name-only HEAD^
```
Above command will show list of all changed that commited, include Added (A), Copied (C), Deleted (D), Modified (M), Renamed (R), have their type (i.e. regular file, symlink, submodule, …​) changed (T), are Unmerged (U), are Unknown (X), or have had their pairing Broken (B).
If you want to show certain type, just use --diff-filter. For example:
```
git diff --name-only HEAD^ --diff-filter=ACMRTU          // get list file Added, Copied, Modified, Renamed, changed, Unmerged
```

### Set username and email
## Global
```
git config --global user.name "your name"
git config --global user.email "your email"
```

## Repository
```
git config user.name "your name"
git config user.email "your email"
```

