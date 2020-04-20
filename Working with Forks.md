# Git - Fetching from Remote repository

1) Fork  remote repository(R) to local using github fork.,
2) Clone the Forked repository(FR) to local repository(LR) using

```
git clone "forked repository URL"
```
3) Set the Git upstream of the FR to LR This is done to ensure that the LR is always in sync with R

```
git remote add upstream "remote Repository URL"
```

4)Verify the new upstream repository you've specified for your fork.

```
git remote -v
> origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
> origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
> upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)
```
## In case of changes to remote repository
1) Fetch the branches and their respective commits from the upstream repository. Commits to `master` will be stored in a local branch, `upstream/master`.
```
git fetch upstream
```
2)



<!--stackedit_data:
eyJoaXN0b3J5IjpbNTA3NzY3OTEzLDQyMTg4NTldfQ==
-->