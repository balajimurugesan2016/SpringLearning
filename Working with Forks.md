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
1) Fetch the branches and their respective commits from the upstream repository. Commits to `master` will be stored in a LR branch, `upstream/master`.
```
git fetch upstream
```
2) Check out your fork's LR `master` branch.
```shell
git checkout master
```
3) Merge the changes from `upstream/master` into your local `master` branch. This brings your fork's `master` branch into sync with the upstream repository, without losing your local changes.
```shell
$ git merge upstream/master
> Updating a422352..5fdff0f
> Fast-forward
>  README                    |    9 -------
>  README.md                 |    7 ++++++
>  2 files changed, 7 insertions(+), 9 deletions(-)
>  delete mode 100644 README
>  create mode 100644 README.md
```
4)




<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNjkyMzk2Niw0MjE4ODU5XX0=
-->