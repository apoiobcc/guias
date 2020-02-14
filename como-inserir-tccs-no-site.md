# Inserção de TCCs no Site

Nos posts crie um arquivo `.md` do ano do TCC conforme os outros anos. Adicionar as infos dos alunos seguindo a listagem entregue pela professora Nina.

Entre em cada link salve em pastas no seu pc todos os arquivos html e pdf de cada aluno. Crie uma pasta pra cada aluno, e nomeie a pasta com o mesmo nome que usar no link do arquivo .md. Se algum dos links estiver quebrado entre em contato com a Nina e peça os emails dos alunos para entrar em contato com eles.

Depois de ter salvado tudo no seu pc e ter feito todo arquivo .md, você deve entrar na máquina do apoio por ssh. Dê cd .. até a pasta raiz. A partir dai entre em /var/www/tccs. Crie o diretório pro ano a ser inserido. Entre no diretório. Dentro dele você vai copiar todas as pastas com os tccs do seu pc para esse diretório da máquina do apoio. 

Para copiar os arquivos use o comando scp no ssh. 
Na pasta do seu pc vc digita:

```bash
scp -r diretorio isis@143.107.44.20:/home/isis/tccs/2017/
```

Esse ip vc consegue estando logado por ssh e digitando:

```bash
curl ifconfig.me
```

Após transferir tudo pro seu usuário, vc no ssh vai entrar no root:

```bash
sudo su
```

E mover tudo pra pasta raiz dos tccs do site do apoio:

```bash
mv diretorio /var/www/tccs/ano/
```

Feito isso teste na sua máquina se o novo arquivo .md está funcionando e depois suba pro apoio também. Confira se está tudo ok.