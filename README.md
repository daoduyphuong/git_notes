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

## get log of unpushed git commit
```
git log origin/$branch_name..$branch_name
```
$branch_name: your branch name, ex: master
You can add '--oneline' to view short log
