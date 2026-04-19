# TP1_analise_jogo_monogame
**Descrição do Jogo:**

Magical Flying Snow Warriors é um jogo de luta entre dois jogadores (pvp local), onde o objetivo e "matar" o outro jogador, sendo isso feito atravez do dano do ataque (ataque1: golpe de curto alcance) ou empurrando o adeversário para fora da plataforma (ataque2: golpe de longo alcance com dash).


**Mecanicas:**

1. O jogo permite a alteração das keybinds dos controles.
2. O jogador pode movimentar-se para a direita e para a esquerda, dar um dash para todas as direções (cima, baixo, esquerda e direita) e pode atacar com dash empurando assim o inimigo.
3. O jogador quando cai para forma da plataforma perde uma das vidas, a perca de 3 vidas resulta na perca do jogo.


**Analise dos Ficheiros:**

Os ficheiros deste jogo são bem divididos e organizados, separando por partes o codigo para cada função necessaria para o jogo, tendo por exemplo um arquivo de codigo apenas para o ataque, outro para o dash e por ai vai; mas em contra partida num jogo de maior escala isso poderia afetar a otimização do mesmo. O jogo separa tambem as imagens e os sons em pastas baseado no que elas se aplicam (ex: a imagem gameover.jpeg encontra-se na pasta "background").


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

Ao analisar o jogo reparamos num bug relativo a uma animação que continuava em loop quando não devia, isto é, ao dar ataque dash para baixo (estando o mesmo no ar) a animação do ataque precistia, até mesmo se o player morre-se, até este dar um outro ataque. Para isso achamos mais eficiente que fosse alterado para depender do A_timer (timer de ataque), assim garantindo que ao realizar o dash para baixo o A_timer seja iniciado; seria tambem melhor zerar o A_animator_timer e attack quando o A_timer terminar, fazendo a animação acabar.


**Mudanças que faziamos em relação ao jogo:**

1. Diminuiamos o couldown dos ataques como também dividiamos o ataque1 e o ataque2 como ataques diferentes. 
2. Fariamos com que em vez de ter sprites de direita e esquerda, só tivesse sprite de so um lado e usavamos codigo para alterar o lado da sprite (tendo em conta que o personagem tem uma aprencia indentica de ambas as prespectivas).
3. Mudariamos o layout dos controles para combinar mais com a estetica do jogo.


**Trabalho de Pesquisa feito por:**

34978 Ana Beatriz Barcelar
34975 Rafaela Campos
29488 Henrique Correia

ablubluble
