# Micelânea

## Como copiar commits de uma branch pra outra:
(Nesse caso, da branch-primaria para a branch-alvo)

```sh
git checkout branch-alvo
git log branch-primaria
Pegue o hash (aquele monte de letras e números) do commit a ser copiado
git cherry-pick commit-hash
Ou
git cherry-pick commit-hash 1 commit-hash2
git add .
git cherry-pick --continue
```

## Mergear dois repositórios (não apenas branches)

```sh
cd path/to/project-a
git checkout some-branch
cd path/to/project-b
git remote add project-a /path/to/project-a
git fetch project-a --tags
git merge --allow-unrelated-histories project-a/some-branch
git remote remove project-a
```

## Como criar aliases (apelidos para comandos:

```sh
nano ~/gitconfig
[aliases]
  save = commit -m
```

Daí é só usar:

```sh
git save "meu commit"
```

## Como apagar um commit errado:

`git reset HEAD~1`

## Apagar 5 commits errados

`git reset HEAD~5 `

## Apagar o commit também no GitHub
Atenção: ⁠Não dar Git push normalmente!

`git push origin +minhabranch --force`

Ou:

`git push -f origin HEAD^:master`

## Outros:

<details>
<summary>Ver o tamanho de um repositório </summary>


https://api.github.com/repos/usuario/nome-do-repositorio

Exemplo:

https://api.github.com/repos/Philliaezer/git-for-learners

>If you own the repository, you can find the exact size by opening your Account Settings → Repositories (https://github.com/settings/repositories), and the repository size is displayed next to its designation.
>
> **If you do not own the repository, you can fork it and then check the in the same place.**
</details>

<details>
<summary>Pesquisar maus commits</summary>
git-bisect - Use binary search to find the commit that introduced a bug

SYNOPSIS

`git bisect <subcommand> <options>`
</details>

<details>
<summary>Enviar repositório por CD/Email/Bluetooth</summary>

**Para empacotar:**

`git bundle create repo.bundle master` -> Empacota o respositorio em um arquivo. Util para mandar o repositório via bluetooth 

**Para desempacotar:**

`git clone repo.bundle <new directory>` -> na verdade, é esse, Desempacota o repositório de um arquivo.
</details>