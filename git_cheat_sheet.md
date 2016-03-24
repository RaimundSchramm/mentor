#### Contents
- [Adding Remote Branches](#adding-remote-branches)
- [Deleting Remote Branches](#deleting-remote-branches)
- [Creating a Patch](#creating-a-patch)
- [Creating a Tag](#creating-a-tag)

-

#### Adding Remote Branches

`git push name_of_repository name_of_branch`

TODO: setup for creator of remote branch

--

#### Deleting Remote Branches

```
git push remote-name-of-destination-repo :remote-branch-you-want-to-delete
```
The local version of this branch still exists in your local repository until deletion.

---

#### Creating a Patch

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

-----

#### Creating a Tag

To create an annotated tag run
```
git tag -a 'name of your tag' -m 'short info about this tag'
```

for example

```
git tag -a v0.0.0.1 -m 'alpha - initial working app on Rails 4.2.0'
```

These tags are local. To push them to a remote use

```
git push origin --tags
```

useful resources:
- [Pro Git](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

------
