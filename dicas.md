# Comandos Git importantes
## Imprescindíveis:
`git clone https://github.com/Maria/repo` - baixa o repositório “repo” do usuário “Maria”

`git status` - status do repositório

`git help core-tutorial` - tutorial do próprio Git

`git log` - mostra todos os commits da branch atual
<details>
<summary>Outros comandos</summary>

`git commit --allow-empty -m 'your message'⁠` - faz commit sem alterações.

`git for-each-repo --config=repo <comando>` - roda comando git para uma lista de repositórios

`git branch` - Para ver todas as branches (a branch atual está com um * no inicio do nome)

</details>

## Configurações iniciais obrigatórias:
```sh
git config --global user.email "meuemail@gmail.com"
git config --global user.name "MeuUsuarioDoGitHub"
git config --global credential.helper store
```

> [!CAUTION]
> A configuração `credential.helper store` torna mais fácil sua vida, ao não precisar digitaro usuário e o Token toda vez.
>
> Mas atenção: O Token é armazenado em texto sem criptografia, o que pode ser um risco de segurança. Então, se tiver confiança na sua máquina, não se preocupe, mas tome cuidado!

## Comandos locais iniciais

```sh
git init novo-repositorio
cd novo-repositorio & echo oi > Readme.md
git add . & git status
git commit -m “chore: first commit”
git branch -M main
```

## Comandos remotos
```sh
git remote add origin https://github.com/Philliaezer/git-for-learners.git
git push -u origin main
    → digite seu username do GitHub/gitlab/Outro
    → Digite seu token
```
> [!WARNING]
> Não use a sua senha do GitHub, mas o seu Token (crie um nas configurações do seu usuário

## Como criar um token?
> A criar

## Para fazer pull request
1. Faça um fork do projeto a ser contribuído
2. `git clone https://github.com/Philliaezer/git-for-learners.git`
3. `git branch contribuindo` - para contribuir
4. `git checkout contribuindo` - para mudar para a branc
    - Ou git checkout -m contribuindo
5. `git add . & git commit -m “feat: Minha contribuição!”`
6. `git push origin contribuindo`
7. No GitHub, vá em “Compare & Pull Request”, faça as alterações, dê uma descrição e pronto!

**Nota:** Você só pode fazer 1 pull request por branch. 
Para criar um novo Pull Request, crie uma nova branch e faça git push  através dela

**Dica:** você pode fazer pull Request no seu próprio repositório pelo Git!

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
