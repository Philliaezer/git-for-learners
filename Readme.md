<div align="center">

#  <img src=https://git-scm.com/images/logo@2x.png height="70" align="center"> &nbsp;for Learners
## Wanna learn GIT? Then follow this quick guide

**Note:** This repo is available in Portuguese too! [Click Here](https://github.com/Philliaezer/git-for-learners/blob/main/dicas.md)

For more tips, see in the repository [Git Flight Rules](https://github.com/k88hudson/git-flight-rules).

And if you have ideas or just want to ask for fixes, please open an _issue_ here, on this repository.
</div>

---

# Important Git Commands
## Essentials:
`git clone https://github.com/Maria/repo` - download the repository “repo” from the user “Maria”

`git status` - repository status

`git help core-tutorial` - Git's official tutorial

<details>
<summary>Other commands</summary>

`git branch` - To see all branches (the current branch has an * at the beginning of its name)

`git log` - show all commits of the current branch

Specials:

`git commit --allow-empty -m 'your message'⁠` - commits without changes.

`git for-each-repo --config=repo <command>` - run git command for a list of repositories

</details>

## Mandatory initial settings:
```sh
$ git config --global user.email "myemail@gmail.com"
$ git config --global user.name "MyGitHubUsername"
$ git config --global credential.helper store
```

The `credential.helper store` configuration makes your life easier by not having to type in your username and token every time you upload your code to GitHub.
> [!CAUTION]
> But be careful: The Token is stored in clear text, which can be a security risk. So, if you trust your machine, don't worry, but, again, be careful!

</details>

## Initial local commands

```sh
git init new-repository
cd new-repository & echo hi > Readme.md
git add . & git status
git commit -m “chore: first commit”
git branch -M main
```

## Remote commands
```sh
$ git remote add origin https://github.com/Philliaezer/git-for-learners.git
$ git push -u origin main
    → Enter your GitHub/Gitlab/Other username
    → Enter your token
```
> [!WARNING]
> Don't use your GitHub password, but your Token (create one in your user settings)

## How to create a token?
<details><summary>Click here</summary>


1. Go to github.com
 and log in.
2. Click on your profile picture (top-right) → Settings

3. In the left sidebar, scroll down and click Developer settings

4. Click Personal access tokens, then Tokens (classic)

5. Click Generate new token → Generate new token (classic)

6. Fill in the token info:

7. Note: Give your token a name (e.g., “My Git Token”)

8. Expiration: Choose how long it will be valid (e.g., 30 days)

9. Scopes (permissions): Check at least:

    - repo → Full access to your repositories

    - read:org → Read access to organizations (optional)

    - workflow → If you use GitHub Actions

    - Others only if you need them

10. Click Generate token

11. Copy the token and save it!



**Note:** You will only see it once. If you lose it, you’ll need to create another one.

**Caution:** Never share your token. Do not upload it to public code.

To use it with Git, paste it when Git asks for your password during git push, git pull, etc.
</div>
</details>

## To make a pull request
1. Fork the project to be contributed to
2. `git clone https://github.com/Philliaezer/git-for-learners.git`
3. `git branch contributing` - to contribute
4. `git checkout contributing` - to switch to the branch
    - Or git checkout -m contributing
5. `git add . & git commit -m “feat: My contribution!”`
6. `git push origin contributing`
7. On GitHub, go to “Compare & Pull Request”, make the changes, give a description and that's it!

> [!NOTE]
> You can only make 1 pull request per branch. 
> 
> To create a new Pull Request, create a new branch and `git push` it.

**Tip:** You can make a pull request to your own repository via Git!

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
