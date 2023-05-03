# Relatorio Trabalho de Grupo

---

### Autores

Ismael Tenda - 25964

Jose Ferreira - 25958

Rui Costa - 25959

---

### indice

1. Introdução

2. Analise do Codigo
   
   1. Program.cs
   
   2. ScoreManager.cs
   
   3. Score.cs
   
   4. GameState.cs
   
   5. Button.cs
   
   6. Game1.cs

3. Colclusão

4. Bibliografia

---

### Introdução

    No ambito da disciplina de Técnicas de Desenvolvimento de Vídeojogos este projeto tem como objetivo o estudo e a analise de um jogo desenvolvido em monogame

---

### Analise do Codigo

#### Program.cs

    A classe Program.cs cria uma variavel **game** que é do tipo **Game1**, de seguida começa o jogo.



#### ScoreManager.cs

    Cria um ficheiro xml, chamado **score.xml**, para guardar as pontuações dos jogadores em ficheiro.

    Cria tambem uma lista de scores e highscores, que sempre que é adicionado um novo score a lista atualiza os 5 melhores scores por ordem decrescente.

    E ainda carrega os scores anteriormente guardados em **score.xml** para dentro do jogo.



#### Score.cs

    Define a classe **Score**, sendo ela um conjunto dos valores **Value** e **Rounds**. 



#### GameState.cs

    Define um *enum* **gameState** que contem as opções menu, score, play, pause e quit.



#### Button.cs

    Define os parametros da classe **Button** (**_texture**, **_position** e **buttonBox**), tal como o construtor para a mesma, para além disso cria funções para verificar se esta a ser clicado, para identificar a posição do botão e para de desenhar o sprite.

 

#### Game1.cs

    Define variaveis para as fontes de texto, os botões, as texturas, os inputs do teclado e do rato, a origem dos vetores, as rondas, os timers, a musica de fundo, as dimensões do ecrã e o score manager.



##### public Game1

    Define a classe **Game1**, que consiste na altura e na largura da janel e cria uma lista de **soundEfects**, um novo **Random**. 



##### protected override void LoadContent()

    Esta função carrega todas as texturas relativas ao fundo (backgrounds), às fontes de texto e aos diversos botões. Carrega também as posições dos botões, e dois sound effects à lista soundEffects: o som de um acerto no inimigo, e o soundtrack, que foi programado para repetir assim que acaba.



##### private void MediaPlayer_MediaStateChanged(object sender, EventsArgs e)

    Faz com que o volume diminua.



##### protected override void Update(GameTime gameTime)

    Define um switch para todos os **gameState**.

        -Caso **gameState** seja menu e o botão de play for clicado o **gameState** passa a ser play, se o botão for clicado o **gameState** passa a ser quit e se o botão score for clicado a **gameState** passa a ser score.

        -Caso **gameState** seja play e a tecla "p" for clicada o **gameState** passa a ser pause, se a tecla "espace" for clicada a variavel **hasStarted** passa a ser true.

        -Gerencia o tempo das rodadas e entre as rodadas.

         Se a rodada for um multiplo de 5 a rodada tera nela um "Boss", se não a rodada sera uma rodada normal e sem um inimigo "boss".

         Por fim da update a todos os sprites. 

        -Caso **gameState**  seja paused e a tecla P for pressionada o jogo deixa de estar pausado e se a tecla ESC for pressionada o jogo volta para o menu.

        -Caso **gameState** seja score define um botão para voltar ao menu.

        -Caso **gameState** seja lose e o botão de play for pressionado, o jogo começa de novo e se o ESC for pressionado, volta ao menulose.

        -Caso **gameState** seja quit o jogo fecha.

    Deteta a posição do rato.

    Define a tecla "M" como uma maneira de dar mute e unmute ao jogo.



##### protected override void Draw(GameTime gameTime)

    Define a cor do background como azul, antes de começar o programa.
    Adiciona um background diferente dependendo do gamestate, e botões onde são necessários.
    Caso o jogo esteja no estado de scores, cria também um título para as pontuações.



##### private void Restart()

    Carrega a textura do player e do chinelo.
    Retorna o valor das roundas, score, pontos de vida e timers aos valores iniciais.
    Define a variável **hasStarted** como sendo falsa, dando opurtunidade ao player de começar o jogo usando a tecla de espaço quando ele quiser.



##### private void BossMove()

    Define a direção de **Enemy** de acordo com a posição de **Player**, de modo a estarem sempre a segui-lo.
    Normaliza a direção do movimento para ser menos angular.
    Define a posição de **Enemy** a partir da direção do seu movimento e da sua velocidade.



##### private void enemyMove()

     Define a direção de **Boss** de acordo com a posição de **Player**, de modo a estarem sempre a segui-lo.
    Normaliza a direção do movimento para ser menos angular.
    Define a posição de **Boss** a partir da direção do seu movimento e da sua velocidade.



##### private void KillBoss()

    Verifica se **Boss** esta em contacto com **Weapon** e se sim retira vida ao inimigo e apaga **Weapon** da tela.



##### private void KillEnemy()

    Verifica se **Enemy** esta em contacto com **Weapon** e se sim retira vida ao inimigo e apaga **Weapon** da tela.



##### private void PostUpdate()

    Esta função serve para remover sprites da tela.
    Se o sprite for um player, o seu score é guardado no score manager e o estado de jogo é alterado para Lose.



##### private void GameStateDraw()

    Se o boss estiver presente na tela, é criado um elemento do HUD que apresenta os seus pontos de vida.
    Cria também um outro elemento de HUD para a vida do player, outro para o seu score, outro para a ronda atual e ainda outro para o tempo que resta para acabar a ronda.

---

### Conclusão

    Durante este trabalho nós deparamo-nos com alguns problemas e obstáculos, um dos foi que o jogo não iniciava, apresentando muitos erros, sendo que apenas um (Bernardo) conseguiu ter o jogo operacional, fazendo com que dependêssemos de um elemento para podermos explorar e analisar o código. Apesar de não ficarmos totalmente dependentes aprendemos, também, que tudo tem uma finalidade, exemplo foi uma função que não tinha nada nela mas que se a apagássemos o jogo não iniciava.

---

### Bibliografia

github.com/raquel4112002/Jogo-Saitama


