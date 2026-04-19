# TP1_analise_jogo_monogame
**Descrição do Jogo:**

É um jogo de luta entre dois jogadores como dois ataques que os jogadores podem utilizar sendo o ataque1 e o ataque2 sendo o ataque1 sendo um golpe de curto alquance que aleija o outro jogador e o outro um ataque aonde faz com que o jogador de um dash que empura o adversario.

O objetivo é derrotar o outro jogador.

**Mecanicas:**
1. Permite a alteração dos controles
2. O jogador pode andar para a direita e esquerda, dar um dash para todas as direções, pode atacar e dar um ataque que da um dash e empurar o inimigo.
3. O jogador quando cai perde uma das vidas, e quando perde as 3 vidas é game over.

**Analise dos Ficheiros:**

São muito bem organizados, separando partes do codigo cada função necessaria para o jogo, como por exemplo tendo um arquivo de codigo so para o ataque outro para o dash e por ai vai mas em contra partida podendo fazer o jogo perder otimização, como também tendo as imagens e soms bem separados, separando as imagens do jogados em diversas pastas como estando parado, correndo e atacando, também tendo as imagens de background, efeitos e universais separados em pastas diferentes, os soms tem duas pastas aonde uma contem as musicas e a outra os efeitos sonoros.<3

**Analise do Codigo:**

**Singleton:**
Esta linha e feita a utilização dos singletons o qual é uma forma de facilitar o acesso de objetos a qual existem apenas uma instancia.
Linha (138 screem gameplays):
```
Screen_Settings settings = (Screen_Settings)Game1.self.screenManager.GetScreen(ScreenManager.GameState.Settings);
```
Aqui é feita a declaração do singletons.
Linha (24 - 28, Game1.cs):
```
public static Game1 self;
public Game1()
{
    self = this; 
    // ...
}
```

**Alterações que fariamos no codigo:**
O que alteravamos no jogo é um problema que ele tem é quando o jogador esta no ar e ele realiza um dash para baixo ele não para a animação e continua mesmo quando o jogador morre so parando quando o realiza um ataque. Para isso achamos mais eficiente que fosse alterado para depender do A_timer (timer de ataque), isso garantiria que ao realizar o dash para baixo o A_timer seja iniciado, também seria melhor zerar o A_animator_timer e attack quando o A_timer terminar, fazendo a animação acabar.

**MUuuuhdanças que faziamos em relação ao jogo:**
1. Diminuiamos o couldown dos ataques como também dividiamos o ataque1 e o ataque2 como ataques diferentes. 
2. Fariamos com que em vez de ter sprites de direita e esquerda, fariamos que so tivesse sprite de so um lado e usavamos codigo para alterar o lado da sprite.
3. Muuuuhdariamos o layout dos controles para combinar mais com a estetica do jogo.

**Trabalho de Pesquisa feito por:**
34978 Ana Beatriz Barcelar
34975 Rafaela Campos
29488 Henrique Correia

ablubluble
