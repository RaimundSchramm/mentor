####Deleting Remote Branches

```
git push remote-name-of-destination-repo :remote-branch-you-want-to-delete
```
The local version of this branch still exists in your local repository until deletion.

####Creating a Patch

Checkout a branch.

```
git checkout -b branch-for-issue
```

Commit your work.

```
git add .
git commit -m 'solves issue'
```

Create the patch.

```
git format-patch master --stdout > path_to_your_patch_file.patch
```

see for example
* (http://ariejan.net/2009/10/26/how-to-create-and-apply-a-patch-with-git/)
* (http://www.ralfebert.de/git/patches/)
