<div align=center><h1>Creating repository</h1></div>

## On your computer:
> First, make sure you've already installed Git on your machine. [Click here to go to the download page.](https://git-scm.com/install/)

### Mandatory initial settings:
After installation, and placing Git in the `$PATH` environment variable, type the following commands one by one
- Just change `myemail@github.com` to your GitHub email, and `MyGitHubUsername` to your actual GitHub @Username):

```sh
$ git config --global user.email "myemail@gmail.com"
$ git config --global user.name "MyGitHubUsername"
$ git config --global credential.helper store
```

The `credential.helper store` configuration is **optional**, but makes your life easier by not having to type in your username and token every time you upload your code to GitHub.
> [!CAUTION]
> But be careful: The Token is stored in clear text, which can be a security risk. So, if you trust your machine, don't worry, but, again, be careful!

</details>

### Initial local commands

```sh
$ git init new-repository
$ cd new-repository & echo hi > Readme.md
$ git add .
$ git commit -m “chore: first commit”
$ git branch -M main
```

---

## On your GitHub account
1. Create a GitHub account, if you don't have one.
2. Create a repository, or copy the URL of an existing one
3. Copy the URL of your new repository, if you have created.

---

## Coming back to your computer:

## Remote commands (link computer project to the GitHub repository)
> Note: Remove "https://github.com/Philliaezer/..." for that URL copied
```sh
$ git remote add origin https://github.com/Philliaezer/git-for-learners.git
$ git push -u origin main
    → Enter your GitHub/Gitlab/Other username
    → Enter your token
```
> [!WARNING]
> Don't use your GitHub password, but your Token (create one in your user settings)

### How to create a token?
<details><summary>Click here</summary>


1. On github.com, click on your profile picture (top-right), then click "Settings"

2. In the left sidebar, scroll down and click Developer settings

3. Click Personal access tokens, then Tokens (classic)

4. Click Generate new token → Generate new token (classic)

6. Fill in the token info:
    1. Note: Give your token a name (e.g., “My Git Token”)
    2. Expiration: Choose how long it will be valid (e.g., 30 days)
    3. Scopes (permissions): Check at least the checkbox `repo` to get full access to your repositories
10. Click Generate token
11. Copy the token and save it!


**Note:** You will only see it once. If you lose it, you’ll need to create another one.

### Caution!
*Never share your token. Do not upload it to public code.*

To use it with Git, paste it when Git asks for your password during git push, git pull, etc.
</div>
</details>
