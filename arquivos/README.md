# ENGENHARIA DE REQUISITOS - O ÚLTIMO COVEIRO

* **Versão:** 1.0
* **Data:** 12/11/2026
* **Equipe:** 4 pessoas (2 programadores, 2 modeladores)
* **Engine:** Unity
* **Estilo:** Zelda OOT + Souls + BOTW - *Low Poly Dark Fantasy*

---

## 1. VISÃO GERAL DO PRODUTO

* **1.1. Objetivo:** Criar um jogo de ação-aventura 3D em terceira pessoa, com mundo semi-aberto, puzzles, combate com lock-on e progressão por itens, onde o jogador enterra os corações de 4 deuses mortos para purificar o mundo.
* **1.2. Público-alvo:** Jogadores que gostam de *Zelda*, *Dark Souls* e *Elden Ring*. Classificação indicativa: **14+** (violência fantasiosa, temas pesados).
* **1.3. Premissa da História:** O mundo era bonito e sustentado por 4 deuses gigantes no horizonte: **Terra**, **Raio**, **Lua** e **Sol**. O avô do protagonista prevê a queda deles, sequestra o neto e o coloca em uma cápsula em um bunker. 30 anos depois, o protagonista acorda. Os deuses caíram, seus corpos apodreceram a terra, o mundo ficou escuro e surgiram os *Podres*. O protagonista se torna o novo Coveiro e deve enterrar os corações dos deuses.

---

## 2. ATORES

* **AT-01:** Jogador (Protagonista / Coveiro)
* **AT-02:** NPC Velha (Guia emocional)
* **AT-03:** NPC Ferreiro (Loja / Reparo)
* **AT-04:** NPC Padre (Dá a missão principal)
* **AT-05:** NPC Criança (Side Quest)
* **AT-06:** Inimigo Podre (Inimigo comum)
* **AT-07:** Boss de cada Deus (4 bosses)

---

## 3. REQUISITOS FUNCIONAIS

### [RF-01] MOVIMENTAÇÃO
O sistema deve permitir o jogador andar, correr, pular, agachar e interagir.
* **RF-01.1:** Andar com `WASD`.
* **RF-01.2:** Correr com `Shift` (consome stamina).
* **RF-01.3:** Pular com `Espaço`.
* **RF-01.4:** Agachar com `Ctrl` (modo stealth, reduz barulho e velocidade).
* **RF-01.5:** Interagir com `E` (pegar item, falar com NPC, abrir baú).

### [RF-02] CÂMERA
* **RF-02.1:** Câmera livre controlada pelo mouse.
* **RF-02.2:** *Lock-on*: Ao apertar o botão direito do mouse, a câmera trava no inimigo mais próximo.
* **RF-02.3:** Ao soltar o *lock-on*, a câmera volta a ser livre.
* **RF-02.4:** A câmera deve colidir com paredes para não atravessar.

### [RF-03] COMBATE
* **RF-03.1:** Ataque leve com clique esquerdo do mouse.
* **RF-03.2:** Defesa com botão direito segurado (com escudo).
* **RF-03.3:** *Parry*: Se defender no momento exato do ataque inimigo, o inimigo fica atordoado por 2 segundos.
* **RF-03.4:** Esquiva / Rolamento com `Shift + Direção` durante o combate.
* **RF-03.5:** O jogador deve ter barra de Vida e barra de Stamina.

### [RF-04] SISTEMA DE ARMAS (ESTILO BOTW)
* **RF-04.1:** O jogador pode carregar até 3 armas ao mesmo tempo.
* **RF-04.2:** Armas disponíveis: Porrete, Faca, Machado, Lança, Arco.
* **RF-04.3:** Toda arma tem durabilidade. Cada *hit* reduz 1 de durabilidade.
* **RF-04.4:** Quando a durabilidade chega a `0`, a arma quebra e some.
* **RF-04.5:** O jogador pode trocar de arma com as teclas `1`, `2`, `3`.
* **RF-04.6:** O jogador pode pegar armas do chão.

### [RF-05] INVENTÁRIO E PROGRESSÃO
* **RF-05.1:** O sistema deve salvar o inventário entre as *Scenes* através do `GameManager` (`DontDestroyOnLoad`).
* **RF-05.2:** Itens-chave de progressão:
  * **Bota de Ferro:** permite andar em espinhos (Terra).
  * **Bota de Borracha:** permite andar em água com raio (Raio).
  * **Lanterna da Lua:** revela inimigos invisíveis no escuro (Lua).
* **RF-05.3:** O jogador só pode entrar na área do Deus do Raio se tiver a **Bota de Ferro**.
* **RF-05.4:** O jogador só pode entrar na área da Deusa da Lua se tiver a **Bota de Borracha**.
* **RF-05.5:** O jogador só pode entrar na área do Deus do Sol se tiver todos os 3 itens anteriores.

### [RF-06] STEALTH
* **RF-06.1:** Inimigos têm campo de visão em cone.
* **RF-06.2:** Se o jogador estiver agachado e andando devagar, ele não é detectado.
* **RF-06.3:** Se o jogador correr ou atacar, ele faz barulho e atrai inimigos próximos.

### [RF-07] INIMIGOS
* **RF-07.1:** **Podre Comum:** Anda devagar, bate fraco, vida baixa.
* **RF-07.2:** **Podre Cão:** Corre rápido, bate forte, vida média.
* **RF-07.3:** Cada inimigo tem vida, dano e velocidade configuráveis via `ScriptableObject`.
* **RF-07.4:** Ao morrer, o inimigo pode dropar item (ferro, arma).

### [RF-08] BOSSES
* **RF-08.1:** Cada Deus tem 1 Boss.
* **RF-08.2:** **Boss da Terra:** Rainha Espinho.
* **RF-08.3:** **Boss do Raio:** Coração do Raio.
* **RF-08.4:** **Boss da Lua:** O Sonho Dela.
* **RF-08.5:** **Boss do Sol:** O Sol Morto (Boss Final).
* **RF-08.6:** Ao derrotar o Boss, o jogador recebe o item-chave daquela área e a área é purificada.

### [RF-09] PUZZLES
* **RF-09.1:** **Puzzle Terra:** Empurrar pedra para o botão para abrir a porta.
* **RF-09.2:** **Puzzle Raio:** Desligar 3 torres de raio na ordem certa.
* **RF-09.3:** **Puzzle Lua:** Refletir luz em espelhos para abrir portas.
* **RF-09.4:** **Puzzle Sol:** Sacrificar parte da vida para abrir a porta final.

### [RF-10] QUESTS
* **RF-10.1:** **Quest Principal:** Enterrar os 4 corações.
* **RF-10.2:** **Quest Tutorial 1:** Salvar o gato da senhora.
* **RF-10.3:** **Quest Tutorial 2:** Levar a cesta para a casa da senhora.
* **RF-10.4:** **Side Quest 1:** Achar o gato de novo (esqueleto).
* **RF-10.5:** **Side Quest 2:** Ferreiro pede 3 ferros de Podre.
* **RF-10.6:** **Side Quest 3:** Criança pede Flor da Lua.
* **RF-10.7:** **Side Quest 4:** Arrumar o sino da igreja.
* **RF-10.8:** **Side Quest 5:** Achar 3 pedaços do bilhete do vô.

### [RF-11] HUB - IGREJA (LUGAR SEGURO)
* **RF-11.1:** Dentro da Igreja, inimigos não podem atacar.
* **RF-11.2:** Na Igreja, o jogador pode falar com os 4 NPCs.
* **RF-11.3:** Na Igreja, o jogador pode se curar (dormir na cama).
* **RF-11.4:** Na Igreja, o Ferreiro conserta e vende armas.

### [RF-12] MUNDO ABERTO
* **RF-12.1:** O mapa é semi-aberto: Igreja no centro + 1 campo central + 4 caminhos para os deuses.
* **RF-12.2:** O jogador pode andar livremente entre as áreas já desbloqueadas.
* **RF-12.3:** Eventos aleatórios no campo:
  * **Chuva de Cinza:** visão reduzida, inimigos mais rápidos.
  * **Podre Perdido:** inimigo surge do nada.
  * **Fogo-fátuo:** luz azul leva a um baú.

### [RF-13] CENAS (SCENES)
* **RF-13.1:** `SC-01` Menu
* **RF-13.2:** `SC-02` Vila Bonita (Ato 1)
* **RF-13.3:** `SC-03` Bunker (Ato 2)
* **RF-13.4:** `SC-04` Igreja (Hub)
* **RF-13.5:** `SC-05` Campo Aberto
* **RF-13.6:** `SC-06` Terra
* **RF-13.7:** `SC-07` Raio
* **RF-13.8:** `SC-08` Lua
* **RF-13.9:** `SC-09` Sol (Final)

### [RF-14] CUTSCENES
* **RF-14.1:** **Cutscene Intro:** Vô sequestra o jogador (30 seg).
* **RF-14.2:** **Cutscene Meio:** Jogador sai do bunker e vê o mundo destruído (15 seg).
* **RF-14.3:** **Cutscene Final:** Deus do Sol fala com o jogador.
* **RF-14.4:** Cutscenes devem ser feitas com *Timeline*, não com código.

### [RF-15] DIÁLOGOS
* **RF-15.1:** Diálogo por caixa de texto, tecla `E` para avançar.
* **RF-15.2:** Bilhetes do vô são itens coletáveis que abrem texto.

### [RF-16] SAVE / LOAD
* **RF-16.1:** O jogo salva automaticamente ao entrar na Igreja.
* **RF-16.2:** O save deve guardar: vida, armas, itens-chave, deuses já enterrados, quests completas.

---

## 4. REQUISITOS NÃO FUNCIONAIS

* **[RNF-01] PERFORMANCE:** O jogo deve rodar a 60 FPS em PC médio, com gráficos *Low Poly*. Sem texturas pesadas.
* **[RNF-02] USABILIDADE:** O jogador deve aprender os controles sem tutorial escrito longo. O aprendizado deve ser por gameplay (quest do gato, stealth no bunker).
* **[RNF-03] COMPATIBILIDADE:** Plataforma alvo: PC Windows. Controles: Teclado + Mouse.
* **[RNF-04] MANUTENIBILIDADE:**
  * Nenhum número de balanceamento (vida, dano, velocidade) pode estar dentro do código. Todos devem estar em `ScriptableObjects`.
  * Cada script deve ter uma única responsabilidade.
  * Todo modelo 3D deve ser um *Prefab*.
* **[RNF-05] ESCOPO:** O jogo **NÃO** terá: multiplayer, mundo aberto gigante, cavalo, 50 armas, 100 inimigos, crafting complexo.
* **[RNF-06] ARTE:** Estilo *Low Poly*, cores escuras após a queda, cores claras e saturadas antes da queda (Vila Bonita).

---

## 5. REGRAS DE NEGÓCIO

* **RN-01:** Arma com durabilidade `0` quebra e desaparece.
* **RN-02:** Se a vida do jogador chegar a `0`, ele volta para a última vez que dormiu na Igreja.
* **RN-03:** O jogador não pode enfrentar o Deus do Sol sem ter enterrado os outros 3 deuses.
* **RN-04:** Dentro da Igreja, o jogador não pode atacar nem ser atacado.
* **RN-05:** O Ferreiro só conserta arma se o jogador tiver ferro.

---

## 6. DIVISÃO DA EQUIPE

### Programador 1 (Você) - Sistemas Principais
* `PlayerMovement`, `Camera`, `Lock-on`, `Combate`, `Parry`, `Esquiva`
* `GameManager`, `Inventário`, `Troca de Scene`, `Puzzles`

### Programador 2 - Balanceamento e IA
* `EnemyAI`, `BossAI`, `Stats` (`ScriptableObjects`)
* Vida, Dano, Velocidade, Durabilidade das armas, UI

### Modelador 1 e 2 - Ambiente e Props
* **Fase 1:** Parede, Chão, Árvore, Baú, Pedra, Tocha
* **Fase 2:** Cápsula, Escada, Porrete, Faca, Bilhete, Sino
* > **Nota:** **NÃO** modelar personagem nem deus (usar Mixamo / Asset Store).

---

## 7. ORDEM DE DESENVOLVIMENTO (PRIORIDADE)

1. **Passo 1: Protótipo com cubos** — Cubo anda, câmera com mouse, *lock-on* em cubo vermelho, empurrar pedra abre porta.
2. **Passo 2: Bunker jogável** — Stealth + porrete.
3. **Passo 3: Igreja + NPCs** — Diálogo simples.
4. **Passo 4: Campo + 1 Deus (Terra)** — Ciclo completo da área.
5. **Passo 5: Replicar mecânicas** — Expandir para Raio, Lua e Sol.
6. **Passo 6: Conteúdo secundário** — Side Quests e Eventos Aleatórios.
7. **Passo 7: Finalização** — Cutscenes e Polimento.
