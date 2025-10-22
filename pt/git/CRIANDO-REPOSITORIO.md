<div align=center><h1>Criando repositório</h1></div>

## No seu computador:
> Primeiro, certifique-se de que você já instalou o Git na sua máquina. [Clique aqui para ir para a página de download.](https://git-scm.com/install/)

### Configurações iniciais obrigatórias:
Após a instalação e colocando o Git na variável de ambiente `$PATH`, digite os seguintes comandos um por um
- Só altera o `meuemail@github.com` para seu e-mail do GitHub e `MeuUsernameDoGitHub` para seu @Username real do GitHub):

```sh
$ git config --global user.email "meuemail@gmail.com"
$ git config --global user.name "MeuUsernameDoGitHub"
$ git config --global credential.helper store
```

A configuração `credential.helper store` é **opcional**, mas facilita sua vida, pois não será necessário digitar seu nome de usuário e token toda vez que você subir seu código para o GitHub.
> [!CAUTION]
> Mas atenção: o Token é armazenado em texto simples, o que pode representar um risco à segurança. Portanto, se você confia na sua máquina, não se preocupe, mas, de novo, tenha cuidado!

</details>

### Comandos locais iniciais

```sh
$ git init novo-repositorio
$ cd novo-repositorio & echo oi > Readme.md
$ git add .
$ git commit -m “chore: primeiro commit”
$ git branch -M main
```

---

## Na sua conta do GitHub
1. Crie uma conta no GitHub, caso ainda não tenha uma.
2. Crie um repositório ou copie a URL de um existente.
3. Copie a URL do seu novo repositório, caso tenha criado.

---

## Voltando ao seu computador:

## Comandos remotos (vincular projeto de computador ao repositório GitHub)
> Nota: Remova "https://github.com/Philliaezer/..." para o URL copiado
```sh
$ git remote add origin https://github.com/Philliaezer/git-for-learners.git
$ git push -u origin main
    → Digite seu nome de usuário do GitHub/Gitlab/Outro, e dê enter
    → Agora, digite seu token
```
> [!WARNING]
> Não use sua senha do GitHub, mas sim seu Token (crie um nas configurações do usuário)

### Como criar um token?
<details><summary>Clique aqui</summary>

1. Acesse github.com
e faça login.
2. Clique na sua foto de perfil (canto superior direito) → Configurações

3. Na barra lateral esquerda, role para baixo e clique em Configurações do desenvolvedor

4. Clique em Tokens de acesso pessoal e, em seguida, em Tokens (clássico).

5. Clique em Gerar novo token → Gerar novo token (clássico).

6. Preencha as informações do token:

7. Observação: dê um nome ao seu token (por exemplo, "Meu Token Git").

8. Expiração: escolha por quanto tempo será válido (por exemplo, 30 dias)

9. Escopos (permissões): Verifique, pelo menos:

    - repo → Acesso total aos seus repositórios

    - read:org → Acesso de leitura para organizações 
10. Clique em Gerar token

11. Copie o token e salve-o!


**Nota:** Você só verá esse token uma vez. Se você perdê-lo, precisará criar outro.

**Cuidado:** Nunca compartilhe seu token. Não o coloque em nenhum código público.

Para usá-lo com o Git, cole-o quando o Git solicitar sua senha durante o `git push`, `git pull`, etc.
</div>
</details>