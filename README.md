# README DO BOTZILLA
## Introdução
<p>Este arquivo contém informações sobre como manusear o Bot do discord Botzilla inteiramente feito com a linguagem Python.</p>
<p>Um resumo bem curto do bot é, ele tem as permissões de administrador e interage de acordo com os comandos do usuário, demarcados com "!"</p>
<p>Ressalto que, caso use o código do repositório, leir este arquivo com muita atenção é essencial pois este arquivo de manuseio contém as funções do bot e como usá-las.</p>
<p>Espero que tenha uma boa leitura e que use este bot com sabedoria.<p>


## Arquivos e Pastas
1. comandos
    1. games.py
    2. moderacao.py
    3. xp_level.py
2. databases.py
3. main.py

---
### games.py
<p>
O arquivo games.py contém funções para entreter os usuários e contém dois jogos:<br>
1. Forca; <br>
2. Quiz.
</p>

---
#### Forca
<p>A forca começa quando ativamos o comando "!forca começar (idioma que a palavra deve estar)".</p>
<p>Quando começa, o bot escolhe uma palavra aleatória com a ajuda de Inteligência Artificial e conta as letras para posicionar os espaços. 
O usuário tem 6 tentativas para acertar a palavra, caso acerte ganha pontos, caso não, o usuário não ganha pontos
</p>
<p>Depois disso, o usuário vai ter 30 segundos para chutar uma letra com o comando "!letra (letra escolhida)", caso haja essa letra, o bot informará e posicionará automaticamente, caso não haja, o bot informará também e tirará uma tentativa. Quando as tentativas acabarem, o bot revelará a palavra e informará que o usuário perdeu</p>
<p>Vale ressaltar que há variantes caso aconteça algo com o jogador, se o jogador, ao invés de digitar o comando "!forca começar (idioma)" digitar "!forca parar", o jogo será interrompido caso esteja ocorrendo.</p>
<p>No código, há 3 comandos relacionados ao jogo da forca:</p>

1. Formatar letra;
2. Forca;
3. Letra.

<p>O comando formatar_letra(parâmetros) é um comando auxiliar e não é capaz de ser executado no Discord em si</p>
<p>O comando Forca já foi explicado, assim como o comando Letra</p>

---
#### Quiz
<p>O quiz também é integrado a Inteligência Artificial, que escolhe uma pergunta no formato:</p>

**PERGUNTA**
A. Alternativa A
B. Alternativa B
C. Alternativa C
D. Alternativa D

<p>O usuário terá 30 segundos para responder com o comando "!responder (alternativa)". Caso haja a resposta errada, o bot informa que a resposta está incorreta, caso esteja correta, o bot informará.</p>
<p>O comando "!quiz" ativa o quiz</p>
<p>No código, há 3 comandos(incluindo o principal) que compõem o comando principal:</p>

1. Gerar Pergunta;
2. Quiz;
3. Responder.

<p>O comando gerar_pergunta(parâmetros) é o "cérebro" do comando principal, ele que pensa qual pergunta vai usar.</p>
<p>Tanto o comando Quiz quanto o comando Responder já foram explicados acima.</p>
<p>Com isso, terminamos a parte do arquivo "games.py"</p>

---
### moderacao.py
<p>O arquivo "moderacao.py" contém comandos que auxiliam no bom andamento do servidor que se encontra, evitando brigas e desrespeito com o uso de warns(avisos) que ajudam caso o usuário fale algum palavrão,e contém 12 funções sendo 5 comandos, 2 eventos e 5 funções auxiliares.</p>
<p>Entre os comandos temos:</p>

1. Reset Members;
2. List Members;
3. Delete Warn;
4. View Warns;
5. Lista Warns.

---
#### Reset Members
<p>O comando "!reset_members" só pode ser executado por administradores do servidor. Isso acontece pelo fato de que esse comando tem papel crucial para o bom funcionamento do bot pois se conecta com um banco de dados que contém tabelas com informações dos usuários e dos servers que o bot participa.</p>
<p>Esse comando faz o bot entrar no banco de dados, pegar os membros do server específico e deleta todos os dados que há nesse server.</p>
<p>Isso foi utilizado e será utilizado para casos de testes do bot.</p>

---
#### List Members
<p>O comando "!list_members" também pode ser executado apenas por administradores. Isso acontece pelo motivo do comando ter conexão com banco de dados.</p>
<p>O comando dito faz basicamente o oposto do comando dito anteriormente, ao invés de deletar os membros do banco de dados, ele mapeia os usuários e os coloca no banco de dados tendo como base o código de identificação do usuário(user id) e o código de identificação do servidor(server id ou guild id)</p>

---
#### Delete Warn
<p>Sendo também utilizado apenas por administradores, o comando "!delete_warn @Usuário" tem conexão com o banco de dados no qual segue o seguinte algoritmo:</p>

1. Faz a conexão com o banco de dados;
2. Seleciona os warns do usuário @Usuário;
3. Zera a quantidade de warns;
4. Atualiza o banco de dados.
---
#### View Warns

<p>O comando "!view_warns @Usuário" pode ser executado por qualquer pessoa. Esse comando tem conexão com banco de dados, porém não permite a edição dos dados. Além de que segue o seguinte algoritmo:</p>

1. Faz a conexão com banco de dados;
2. Seleciona os warns do usuário @Usuário;
3. Armazena os dados em uma variável;
4. Manipula a variável para ter o padrão que conhecemos de dados numéricos;
5. Mostra a variável no chat.
---
#### Lista Warns 
<p>O comando "!lista_warns" só pode ser executado por administradores pelo fato de preservar a integridade dos usuários que não se dispõem a revelar informações, ainda que fictícias, importantes para moderar o servidor.</p>
<p>O comando funciona da seguinte forma: <p>

1. Realiza a conexão com banco de dados;
2. Seleciona os warns de todos os usuários que estão no servidor que foi digitado o comando;
3. Armazena em uma lista;
4. Organiza a lista para o bom entendimento;
5. Mostra a lista de forma organizada no chat que foi digitado o comando.

<p>Agora, entre os eventos temos:</p>

1. On Member Join
2. On Message

---
#### On Member Join

<p>O evento on_member_join analisa e monitora o servidor para quando um usuário se juntar ao servidor, o bot dá uma mensagem de boas vindas em um canal específico caso exista esse canal, caso contrário, ele coloca no canal "geral" que é gerado na criação do servidor</p>

---

#### On Message

<p>O evento on_message faz o seguinte algoritmo:</p>

1. Analisa cada mensagem do servidor com Inteligência Artificial;
2. Se houver palavrão na mensagem, o bot informa um warn ao autor da mensagem, caso não, o bot concede xp ao autor;
3. Caso seja o quinto warn do usuário, ele bane o usuário automaticamente.

<p>Por último, porém não menos importante, temos as funções auxiliares:</p>

1. Add XP;
2. Adicionar User;
3. Log Moderação;
4. Verifica Palavrão;
5. Criar e Salvar Warn.
---
#### Add XP
<p>A função add_xp(parâmetros) é importante pois nela há todo o cérebro por trás da tabela que armazena o xp do usuário em um banco de dados.</p>
<p>Esta função segue o seguinte algoritmo:</p>

1. Realiza a conexão com o banco de dados;
2. Seleciona a tabela que contém o xp dos usuários; 
3. Atualiza o xp do usuário caso ele mande mensagem;
4. Atualiza e fecha o banco de dados.
---
#### Adicionar User

<p>A função adicionar_user(parâmetros) é usada para adicionar novos usuários de um servidor na tabela que contém os usuários e o id de seus servidores</p>
<p>O algoritmo desta função funciona da seguinte maneira:</p>

1. Faz a conexão com o banco de dados;
2. Seleciona a tabela que contém os usuários do servidor em que o usuário mandou mensagem;
3. Verifica se o usuário já está no banco de dados, caso esteja, o bot passa e fecha o banco de dados;
4. Caso não esteja, o bot adiciona com o id do usuário e do servidor.
---
#### Log Moderação

<p>A função log_moderacao(parâmetros) é usada para enviar comandos em um canal específico quando alguém leva um warn ou é banido do servidor</p>

---
#### Verifica Palavrão

<p>A função verifica_palavrao(parâmetros) é usada para verificar se uma frase contém palavras de baixo calão funciona da seguinte forma:<p>

1. Cada palavra da frase é analisada por uma Inteligência Artificial;
2. Se houver palavrão, será retornado True, se não houver, será retornado False.
---
#### Criar e Salvar Warn

<p>A função criar_salvar_warn(parâmetros) é usada para dar um warn ao usuário na parte do banco de dados.</p>
<p>Funciona da seguinte forma:</p>

1. O bot faz a conexão com o banco de dados e seleciona a tabela de warns de um usuário;
2. Adiciona um à quantidade de warns;
3. Salva e fecha a tabela e o banco de dados.
---
### xp_level.py

<p>O arquivo "xp_level.py" contém funções que estão relacionadas com o sistema de xp e nível. Existem 2 comandos e uma função auxiliar que são:</p>

1. Zerar XP e Level
2. Ranking
3. Add XP
---
#### Zerar XP e Level

<p>Essa função é usada apenas por administradores para não haver brechas para "brincadeiras de mal gosto"</p>
<p>A função "!zerar_xp_level @Usuário" tem o seguinte algoritmo:</p>

1. O bot faz a conexão com o banco de dados e seleciona a tabela que contém os xp e níveis dos usuários;
2. Procura o xp e nível de @Usuário;
3. Se houver dados, o bot zera o xp e o nível de @Usuário, caso não haja, o bot adiciona @Usuário nos bancos de dados.
---
#### Ranking
<p>Podendo ser executado por qualquer usuário, o comando "!ranking" mostra os 10 primeiros que têm mais xp e level usando o seguinte algoritmo:</p>

1. O bot faz a conexão com o banco de dados;
2. Seleciona a tabela que contém o xp dos usuários de um servidor específico;
3. Lista em ordem decrescente de xp e level os 10 usuários;
4. Organiza e coloca no chat em que o comando foi invocado. 
---
#### Comando Adicionar XP
Esta função já foi explicada em >Adicionar XP

---
### databases.py

<p>Nessa parte, é de suma importância a atenção do leitor, pois o código pode apresentar mal funcionamento caso não seja feito da maneira correta.</p>

<p>O código serve para criar o banco de dados e criar as tabelas que garantem o bom funcionamento do código e funciona com o seguinte algoritmo: </p>

1. O banco de dados é criado
2. A tabela que identifica de qual servidor um usuário pertence é criada
3. A tabela que armazena o xp e nível de cada usuário
4. A tabela que armazena os warns de cada usuário
5. A tabela que armazena os servidores em que o bot está cadastrado
6. A tabela que armazena os administradores de cada servidor em que o bot está cadastrado


##### Atenção
É de suma importância executar esse arquivo primeiro para depois começar a executar o próximo arquivo citado pois, sem isso, o código mostrará um erro.

---
### main.py

<p>Este arquivo é o arquivo principal que contém comandos importantes e eventos identificadores de funcionamento. São 8 comandos, 1 evento e 1 função auxiliar. </p>
<p>Os comandos são:</p>

1. Olá;
2. Piada; 
3. Curiosidade;
4. Adivinhe;
5. Soma;
6. Subtração;
7. Multiplicação;
8. Divisão.

---

#### Olá
<p>O comando "!ola" é uma função básica em que o bot responde "Olá @Usuário"</p>
<p>O comando foi criado com o intuito de testar as funcionalidades do bot

---
#### Piada

<p>O comando "!piada" funciona com o auxílio de Inteligência Artificial em que há um prompt pronto que pede à IA que conte uma piada.</p>

---
#### Curiosidade
<p>O comando "!curiosidade" também funciona com ajuda de Inteligência Artificial, em que também há um prompt pronto que pede à IA que conte uma curiosidade interessante.</p>

---
#### Adivinhe
<p>O comando "!adivinhe" faz o bot escolher um número aleatório entre 1 e 10 e o usuário tem que adivinhar. Caso o usuário acerte ou erre, o bot informará.</p>
<p>Caso o usuário demore mais que 10 segundos, o bot encerrará o comando.</p>

---

#### Soma
<p>O comando "!soma n1 n2 ..." soma os números, ainda que tenham partes fracionárias, que foram especificados.</p>

---

#### Subtração
<p>O comando "!sub n1 n2" subtrai n2 de n1, ainda que n1 e/ou n2 tenham partes fracionárias.</p>

---

#### Multiplicação
<p>O comando "!mult n1 n2 n3 ..." multiplica entre si os números especificados.</p>

---

#### Divisão
<p>O comando "!div n1 n2" divide n1 por n2 ainda que com parte fracionária.</p>

---

<p>Agora, temos o evento on ready</p>

---

#### On ready
<p>O evento "on_ready" serve para quando o bot é ativado, aparecer uma mensagem no console.</p>

---

<p>Agora temos a última parte dos arquivos e pastas, que é a função auxiliar carregar_comandos(), que é basicamente uma função para carregar as funções dos outros arquivos criados.</p>

---

## Conclusão

Se o leitor chegou até aqui, você concluiu o manual de como usar o Botzilla. 
Quero agradecer por toda esta jornada e espero que use o bot com sabedoria.

Que o leitor possa ter sucesso em sua carreira e em seus sonhos pessoais.


Copyright (C) 2025 by João Henrique
