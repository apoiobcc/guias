# Modificações no site do Apoio

## Como ter o site localmente no seu computador

No terminal, caso ja não tenho clonado o repositorio anteriormente, digite:

```bash
git clone https://github.com/ahhul/apoiobcc
```

Isso vai criar uma pasta chamada `apoio bcc` no diretorio de onde você abriu o terminal. Caso você ja tenha essa pasta, abra o terminal a partir dela e digite:

```bash
git pull
```

Isso vai baixar as atualizações do repositorio na sua maquina.

## Como fazer alterações locais no site

Fazer as alterações necessárias no site nas páginas no seu pc.

Quando terminar, compile com o comando e teste no seu pc se está tudo certo. Para compilar, dentro da pasta do repositório no seu pc, digite:

```bash
rvmsudo bundle exec jekyll serve
```

No navegador entrar em `localhost:4000` para testar.

Após testar, para subir todas no github, faça

```bash
git status (para checar todos os arquivos que foram alterados)
git add -A
git commit -m "mensagem dizendo oq foi feito"
git push (sobe as mudanças)
```

> dentro do `git commit -m` digite algo simples e breve sobre o que feito, por exemplo: `git commit -m "adicionando tccs 2017"`
> provavelmente, apos digitar `git push`, você tera que enseirir seu usuario e senha do github

Pronto, agora as mudanças foram feitas no repositorio do github.

## Como colocar as mudanças feitas no ar

Entrar na máquina do bcc:

```bash
ssh <seu-user>@bcc.ime.usp.br
```

Entrar na sua pasta e atualizar o repositorio nela

```bash
git clone https://github.com/ahhul/apoiobcc
git pull (depois que ja tiver clonado sempre use esse pra atualizar)
rvmsudo bundle exec jekyll build (para rodar o site na máquina)
```

Olhar na internet se atualizou certo.