# Important Git Commands
## Essentials:
`git clone https://github.com/Maria/repo` - download the repository “repo” from the user “Maria”

`git status` - repository status

`git help core-tutorial` - Git's official tutorial

`git log` - show all commits of the current branch
<details>
<summary>Other commands</summary>

`git commit --allow-empty -m 'your message'⁠` - commits without changes.

`git for-each-repo --config=repo <comando>` - run git command for a list of repositories

`git branch` - To see all branches (the current branch has an * at the beginning of its name)

</details>

## Mandatory initial settings:
```sh
git config --global user.email "myemail@gmail.com"
git config --global user.name "MyGitHubUsernamr"
git config --global credential.helper store
```

The `credential.helper store` configuration makes your life easier by not having to type in your username and token every time you upload your code to GitHub.
> [!CAUTION]
> But be careful: The Token is stored in clear text, which can be a security risk. So, if you trust your machine, don't worry, but, again, be careful!

</details>

## Initial local commands

```sh
git init new-repository
cd new-repository & echo oi > Readme.md
git add . & git status
git commit -m “chore: first commit”
git branch -M main
```

## Remote commands
```sh
git remote add origin https://github.com/Philliaezer/git-for-learners.git
git push -u origin main
    → Enter your GitHub/Gitlab/Other username
    → Enter your token
```
> [!WARNING]
> Don't use your GitHub password, but your Token (create one in your user settings)

## How to create a token?
> Todo: Create this section

## To make a pull request
1. Fork the project to be contributed to
2. `git clone https://github.com/Philliaezer/git-for-learners.git`
3. `git branch contributing` - to contribute
4. `git checkout contributing` - to switch to the branch
    - Or git checkout -m contributing
5. `git add . & git commit -m “feat: My contribution!”`
6. `git push origin contributinh`
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
Or
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

```sh
nano ~/gitconfig
[aliases]
  save = commit -m
```

Then just use:

```sh
git save "my commit"
```

## How to delete a bad commit:

`git reset HEAD~1`

## Delete 5 bad commits

`git reset HEAD~5 `

## Delete the commit on GitHub as well
Attention: ⁠Do not Git push normally!

`git push origin +mybranch --force`

Or:

`git push -f origin HEAD^:master`

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
<summary>Enviar repositório por CD/Email/Bluetooth</summary>

**To pack/bundle:**

`git bundle create repo.bundle master` -> Bundle the repository into a file. Useful for sending the repository via Bluetooth 

**To unbundle:**

`git clone repo.bundle <new directory>` -> actually, it's this one, Unpack the repository from a file.
</details>

