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
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbNDIxODg1OV19
-->