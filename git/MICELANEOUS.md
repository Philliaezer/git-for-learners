# Micelaneous

## How to copy commits from one branch to another:
(In this case, from the primary-branch to the target-branch)

```sh
git checkout target-branch
git log primary-branch
Get the hash (that bunch of letters and numbers) of the commit to be copied
git cherry-pick commit-hash
```
Or
```sh
git cherry-pick commit-hash 1 commit-hash2
git add .
git cherry-pick --continue
```

## Merge two repositories (not just branches)

```sh
cd path/to/project-a
git checkout some-branch
cd path/to/project-b
git remote add project-a /path/to/project-a
git fetch project-a --tags
git merge --allow-unrelated-histories project-a/some-branch
git remote remove project-a
```

## How to create aliases (nicknames for commands:

Type in your terminal:
```sh
$ nano ~/gitconfig
```

Then paste something like:
```sh
[aliases]
  save = commit -m
```

Then, you can just use:

```sh
git save "my commit"
```

## How to delete a bad commit:

`git reset HEAD~1`

## Delete the last 5 bad commits

`git reset HEAD~5 `

## Delete the commit on GitHub as well
Attention: ⁠Do not Git push normally!

And be careful if there are contributors in your project, as they may have problems while trying to push changes

`git push origin +mybranch --force`

Or:

`git push -f origin HEAD^:master`

## Delete an whole branch
`git branch -d branch-name`

## Deleted on the origin (GitHub/gitlab...) repository 
`git push origin --delete branch-name`

## How to recover an deleted commit
> If you commited a deleted branch, you can recover that too!

```sh
git reflog --no-abbrev
```

>> See the SHA-1 hash (that bunch of numbers and some letters) of the commit you wanna recover, and then

`git checkout <type here the SHA-1 hash>`

## Others:

<details>
<summary>View the size of a repository </summary>


https://api.github.com/repos/usuario/name-of-repository

Example:

https://api.github.com/repos/Philliaezer/git-for-learners

>If you own the repository, you can find the exact size by opening your Account Settings → Repositories (https://github.com/settings/repositories), and the repository size is displayed next to its designation.
>
> **If you do not own the repository, you can fork it and then check the in the same place.**
</details>

<details>
<summary>Search for bad commits</summary>
git-bisect - Use binary search to find the commit that introduced a bug

SYNOPSIS

`git bisect <subcommand> <options>`
</details>

<details>
<summary>Send repository via CD/Email/Bluetooth</summary>

**To pack/bundle:**

`git bundle create repo.bundle master` -> Bundle the repository into a file. Useful for sending the repository via Bluetooth 

**To unbundle:**

`git clone repo.bundle <new directory>` -> Unpack the repository from a file.
</details>

<details><summary>Bring files/folders from one branch to another</summary>

**To remove on the branch main**

First, checkout on the branch you want to remove those files or folders

```sh
$ git checkout main
```

And then remove the folders normally, and then commit the changes
```sh
$ git rm -r folder folder2 file.txt

$ git commit -m "Remove folders and files that will be moved to dev"
```

**To add on the branch dev**

Switch to dev branch, and there just restore that deleted commit

```sh
$ git checkout dev

$ git checkout main~1 -- folder folder2 file.txt
```

and then push both branches

```sh
$ git add .

$ git commit -m "Add folders and files that was removed from main"

$ git push origin dev

$ git checkout main

$ git push origin main
```

</details>