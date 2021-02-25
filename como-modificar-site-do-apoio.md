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

## Como atualizar o site com a integração direta

A integração direta irá utilizar o Travis, um sistema que irá checar as mudanças automaticamente e atualizar o site caso não
tenha problemas nas mudanças feitas. Para que ele atue, é preciso fazer um Pull Request, e para isso:

Faça um Fork do repositório clicando no botão que está no canto superior direito na página do repositório nomeado "FORK",
clone o repositório do Fork, crie um branch e adicione o repositório original como upstream do branch com os seguintes comandos:

```bash
git clone https://github.com/<SeuUserName>/demo
git checkout -b <nomedobranch>
git remote add upstream https://github.com/apoiobcc/apoiobcc
```
Com isso, para subir todas as mudanças no github, faça:

```bash
git status (para checar todos os arquivos que foram alterados)
git add -A
git commit -m "mensagem dizendo oq foi feito"
git push -u origin <nomedobranch> (sobe as mudanças)
```

> dentro do `git commit -m` digite algo simples e breve sobre o que feito, por exemplo: `git commit -m "adicionando tccs 2017"`
> provavelmente, apos digitar `git push`, você tera que enseirir seu usuario e senha do github

Pronto, agora as mudanças foram subidas para o git em sua branch, para fazer o Pull Request basta ir na página inicial do 
repositório e clicar no botão "Compare & Pull Request" que aparecerá.

Feito isso, basta comentar as mudanças e confirmar o Pull Request, o Travis iniciará sua análise e irá atualizar o site se 
estiver tudo certo. Se a análise der errado, é provável que as mudanças estejam erradas.

>Caso ele fique amarelo por mais de 10 minutos, é provável que tenha algo de errado com o sistema, logo pode ser necessário
>atualizar o site na mão utilizando a máquina virtual do BCC, como descrito na seção à seguir.

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
