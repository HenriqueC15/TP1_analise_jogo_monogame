# TP1_analise_jogo_monogame
**Descrição do Jogo:**

Magical Flying Snow Warriors é um jogo de luta entre dois jogadores (pvp local), onde o objetivo e "matar" o outro jogador, sendo isso feito atravez do dano do ataque (ataque1: golpe de curto alcance) ou empurrando o adeversário para fora da plataforma (ataque2: golpe de longo alcance com dash).


**Mecanicas:**

1. O jogo permite a alteração das keybinds dos controles.
2. O jogador pode movimentar-se para a direita e para a esquerda, dar um dash para todas as direções (cima, baixo, esquerda e direita) e pode atacar com dash empurando assim o inimigo.
3. O jogador quando cai para fora da plataforma e perde uma das vidas, a perca de 3 vidas resulta na perca do jogo.


**Analise dos Ficheiros:**

Os ficheiros deste jogo são bem divididos e organizados, separando o codigo por cada função necessaria para o jogo, tendo por exemplo um arquivo de codigo apenas para o ataque, outro para o dash e por ai vai; mas em contra partida num jogo de maior escala isso poderia afetar a otimização do mesmo. O jogo separa tambem as imagens e os sons em pastas baseadas ao que elas se aplicam (ex: a imagem gameover.jpeg encontra-se na pasta "background").


**Analise do Codigo:**

Em geral o código deste jogo aparenta ser relativamente simples, sendo esta parte a que achamos mais interesssante de mencionar:

**Singleton:**
Nesta linha de código são utilizados os singletons, para os quais existe apenas uma instancia, sendo esta uma forma de facilitar o acesso aos objetos.
Linha (138 screem gameplays):
```
Screen_Settings settings = (Screen_Settings)Game1.self.screenManager.GetScreen(ScreenManager.GameState.Settings);
```
Aqui é feita a declaração dos singletons.
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

Ao analisar o jogo reparamos num bug relativo a uma animação que continuava em loop quando não devia, isto é, ao dar ataque dash para baixo (estando o player no ar) a animação do ataque perssistia, até mesmo se o player morre-se, até este dar um outro ataque. Para isso achamos mais eficiente que fosse alterado para depender do A_timer (timer de ataque), assim garantindo que ao realizar o dash para baixo o A_timer seja iniciado; seria tambem melhor zerar o A_animator_timer e attack quando o A_timer terminar, fazendo a animação acabar.

**Linhas de codigo que alterariamos e como:**
Linha 172 – 182:
```
if (A_timer > 0)
{
A_timer -= 1;
A_wait = (float)A_timer / (float)A_timer_length;
if (A_timer == 0)
{
A_pressed = false;
A_animation_timer = 1;
attack = null;
}
}
```

Linha 188 :
```
A_timer = 30;
A_timer_length = A_timer;
A_pressed = true;
```
Linha 241:
```
if (A_timer > 0)
{
// ...
}
```
Linha 254:
```
if (A_animation_timer >= 9) A_animation_timer = 1;
{
// ...
}
```
Linha 258:
```
else if (!is_in_jump && (state.IsKeyDown(right) || state.IsKeyDown(left)))
{
// ...
}
```

**Mudanças que faziamos em relação ao jogo:**

1. Diminuiamos o couldown dos ataques como também dividiamos o ataque1 e o ataque2 em ataques diferentes(colldowns e keybinds proprios). 
2. Fariamos com que em vez de ter sprites de direita e esquerda, só existisse sprite de so um lado e usavamos codigo para alterar o lado da sprite (tendo em conta que o personagem tem uma aprencia indentica de ambas as prespectivas).
3. Mudariamos o layout dos controles para combinar mais com a estetica do jogo.


**Trabalho de Pesquisa feito por:**

34978 Ana Beatriz Barcelar
34975 Rafaela Campos
29488 Henrique Correia

ablubluble
