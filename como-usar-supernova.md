# Gerar Relatórios no supernova

No site do supernova, em datafile: subir o arquivo txt.
Obs: Só fazer isso uma vez, pois sobrescreve o arquivo somando no final (dobrando, triplicando...o arquivo).

Verificar no BD se foi inserido:

```console
ssh <seu-user>@bcc.ime.usp.br
```

Entrar na pasta do supernova (home). Entrar no banco:

```console
sudo mysql supernova
use supernova (para poder acessar)
show tables;
select * from datafile;
```

Gerar os relatórios em generator, no site do supernova. Para isso só selecionar de 5 em 5. Em paralelo, no terminal, acessar por ssh a máquina do bcc e rodar htop. Controlar o uso de memória não deixando ela estourar.

Copiar os relatórios para sua máquina:

```console
> cd supernova/public/relatorios/disciplinas
> cp **/*2019s1* /home/isis (manda para pasta os arquivos)
> scp – r <seu-user>@bcc.ime.usp.br:~/reports./ (baixa para o seu pc os arquivos – criar essa pasta reports no seu pc)
```

Entre nessa pasta reports no seu pc e nela zip os arquivos:

```console
zip -r nomeDoZip nomeDaPasta
```

# Para erros aleatórios no Supernova

Na pasta do supernova:

```console
ls -a
vim .django.settings.py (mudar debbug para true ou deixar false e adicionar um e-mail para visualizar os logs - cuidado com a sintaxe pra não faltar vírgulas, isso trava o supernova).
apache2ctl graceful (reseta o supernova – reinicia sem chutar quem está usando)
chmod 777 #nomeDaPasta (altera permissão, péssima prática, só use em caso de desespero).
```

# Supernova - Criar folha ótica

Entre no BD do supernova para criar um novo semestre:

```console
ssh <seu-user>@bcc.ime.usp.br
```

Entrar na pasta do supernova (home). Entrar no banco:

```console
sudo mysql supernova
use supernova (para poder acessar)
show tables;
select * from timePeriod;
insert into timePeriod(length, year, session) values(1, 2019, 2);
```

Obs: Os valores aqui: o 1 significa que é semestral, 2019 é o ano atual e o 2 é o semestre.

No site do Supernova:

Crawler:
Primeiro puxaremos o crawler. Entre em interface e depois em crawler. Seleciona o BCC, o semestre e roda. Aqui só pode clicar uma vez. Vai demorar um pouco, em torno de 10 min. Seja paciente xP!

OfferList:
Em interface, entre em offer list. Selecione as opções do semestre e imprima o pdf. Confira se as matérias que ele puxou batem com o do semestre ofertado.

No BD do Supernova:

Olhar na tabela encoding se foi inserido o arquivo com a lista de matérias. Aproveite para conferir o padrão do nome.

```console
select * from encoding;
```

No site do Supernova:

Filtrar lista:
Em Encoder, selecionar o semestre e inserir nova codificação. Puxando do BD com o nome (bcc-ano-semestre).
Ele abre pra você selecionar o ano das matérias e filtrar a lista. Aqui selecionar as matérias que tem gente do bcc fazendo. Em caso de dúvida consulte o jupiterweb e veja o número de inscritos. Depois de selecionado, rode. Vai gerar uma lista do lado com o número de matérias que você filtrou. Essa lista do lado tem que ser gerada!!! Se isso não aconteceu deu algum erro e não vai funcionar gerar a folha ótica. Lembre que só pode ter até 100 matérias nessa lista.

Optical sheet:
Em optical sheet, vamos montar a folha ótica de verdade. Selecione os semestres todos. Inclusive a folha do encoding. Puxe as perguntas do semestre anterior e altere se necessário. Inclua a ordem das respostas que as pessoas devem dar pras perguntas no topo. Do lado direito extremo você pode optar por gerar em PDF ou Tex. Depois de tudo feito gere a folha e o arquivo AMC. 
***** Aperta a porra do store no fim!!!!!!

Confira se gerou certo os arquivos. Confira com os rcs se a lista de matérias está ok. Depois de tudo isso mande os arquivos Tex pro Coelho imprimir :)!!!

# Supernova - Criar usuário

No terminal:

```console
ssh <seu-user>@bcc.ime.usp.br
sudo su
cd /supernova/aeSupernova
python manage py Shell
from django contrib auth models import User
import datetime
user = User.objects.create_user('nome', 'email', 'senha', last_login = datetime.datetime(ano, mês, dia))
user.save()
```