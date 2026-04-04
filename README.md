# 📡 Laboratório de Sinais e Sistemas

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

Bem-vindo ao **Laboratório de Sinais e Sistemas**, uma aplicação web interativa, visual e educacional desenvolvida para facilitar o ensino e a aprendizagem da teoria de Sinais e Sistemas Lineares.

Este simulador roda inteiramente no navegador e permite a criação, análise, transformação e convolução de sinais em tempo real, além do estudo de propriedades de sistemas e diagramas de blocos. Ideal para estudantes de Engenharia Elétrica, Computação, Controle e Automação e áreas afins.

---

## ✨ Funcionalidades Principais

O simulador é dividido em 4 módulos principais, além de ferramentas globais de produtividade.

### 1. 📈 Análise de Sinais
- **Domínio Contínuo e Discreto:** Alterne instantaneamente entre o tempo contínuo $x(t)$ e o tempo discreto $x[n]$ com adaptação automática de eixos e variáveis.
- **Construtor de Sinais:** Adicione múltiplos sinais através de equações matemáticas.
- **Injeção de Parâmetros Dinâmica:** Sliders inteligentes (Amplitude, Período, Fase) que só aparecem se o sinal possuir essas variáveis. Botão mágico para "injetar" parâmetros em sinais estáticos (ex: transformar `rect(t)` em `A * rect((2*pi/T0)*t - phase)`).
- **Construtor por Partes (Piecewise):** Uma interface visual (🧩) para montar sinais condicionais de forma fácil (Ex: vale `sin(t)` se `t > 0`, caso contrário `0`).
- **Análise Instantânea:**
  - Decomposição em componentes **Par e Ímpar**.
  - Visualização do Sinal Resultante (Soma de todos os sinais ativos).
  - Cálculo de **Energia Total (**$E$**)** e **Potência Média (**$P$**)** numéricas na janela visível.
  - Grade de **Múltiplos Períodos** detectada automaticamente para sinais periódicos.

### 2. 🔄 Transformações
Aplica operações na variável independente (tempo) e dependente (amplitude) visualizando o antes e o depois de um sinal base estático.
- **Escalonamento no Tempo (**$a$**):** Compressão, expansão e reversão temporal.
- **Deslocamento no Tempo (**$t_0$**):** Atraso e adiantamento.
- **Ganho (**$C$**) e Nível DC / Offset (**$D$**).**
- **Diagnóstico em Tempo Real:** O sistema descreve o efeito atual (ex: *"Sinal Comprimido e Atrasado"*).
- Permite salvar a função transformada resultante $y(t)$ como um novo sinal independente na aba de análise.

### 3. 🔀 Convolução Dinâmica e Analítica
Um motor avançado para visualização da Integral de Convolução $(f * g)(t)$.
- **Animação Interativa:** Visualize o sinal $f(\tau)$ fixo e a resposta ao impulso $g(t-\tau)$ invertida e deslizando no tempo, com o gráfico da área de intersecção preenchida.
- **Controle de Reprodução:** Dê play, pause, altere a velocidade ou arraste a barra de tempo manualmente com extrema fluidez.
- **Estudo Analítico de Intervalos Críticos:** O algoritmo rastreia o suporte dos sinais e calcula os pontos de quebra matemáticos exatos ($t_1, t_2, t_3...$).
  - Informa textualmente o estado da convolução: *Pré-overlap, Entrando, Transição, Saindo, Pós-overlap*.
  - Exibe botões com os limites de integração na tela que te permitem "pular" exatamente para as fronteiras críticas da equação.

### 4. ⚙️ Sistemas Lineares e Topologias
- **Diagrama de Blocos em Árvore (AST):** Conecte múltiplos sinais em **Série** (Cascata / Multiplicação) ou **Paralelo** (Soma). O sistema desenha automaticamente o diagrama de blocos visual na tela obedecendo a ordem de precedência matemática.
- **Cálculo de $h_{eq}(t)$:** Calcule a resposta ao impulso equivalente da malha inteira e plote o resultado instantaneamente, podendo salvá-lo como um novo sinal para reuso.
- **Sistemas Notáveis e Propriedades:** Passe um sinal $x(t)$ por sistemas clássicos (Amplificador, Quadrador, Atraso, Integrador, Derivador, etc.) e receba um diagnóstico automático das propriedades daquele sistema:
  - Com ou Sem Memória.
  - Linear ou Não Linear.
  - Variante ou Invariante no Tempo (SLIT).
  - Causal ou Não Causal.

---

## 🛠 Ferramentas Globais e UX

Pensado para máxima produtividade na resolução de listas de exercícios:

- **Inspetor de Coordenadas (Hover):** Pressione `Alt + C` ou clique no alvo (🎯) para transformar o cursor em uma mira de precisão, revelando os valores de $(x, y)$ exatos no gráfico.
- **Motor Gráfico Customizado:** Gráficos renderizados via HTML5 Canvas ultra-rápido, suportando arrastar para navegar (Pan), rolar o scroll do mouse para Zoom e gestos de pinça em dispositivos móveis.
- **Tela Cheia Responsiva:** Gráficos se expandem via `ResizeObserver` com clique nativo para tela cheia e retração via `Esc`.
- **Painel Redimensionável:** Arraste a borda lateral da área de controles para redimensionar a seu gosto, ou dê duplo clique para restaurar o tamanho original. Oculte o painel totalmente para foco apenas nos gráficos.
- **Máquina do Tempo (Undo/Redo):** Errou uma fórmula ou excluiu um sinal? O sistema armazena um histórico completo. Restaure tudo com atalhos de teclado.
- **Importação/Exportação:** Salve sua sessão inteira (sinais ativos, configurações de convolução, blocos de diagrama) como um arquivo `.json` local e carregue depois para continuar seus estudos.
- **Guia Teórico Integrado:** Um manual rápido (📖) focado em provas universitárias, listando funções e propriedades, acessível a um clique.

---

## ⌨️ Atalhos de Teclado

Navegue e modifique sinais rapidamente utilizando o teclado:

| **Comando** | **Ação** |
| :--- | :--- |
| <kbd>Ctrl</kbd> + <kbd>Z</kbd> | Desfazer Ação |
| <kbd>Ctrl</kbd> + <kbd>Y</kbd> | Refazer Ação |
| <kbd>Alt</kbd> + <kbd>S</kbd> | Exportar Sinais (.json) |
| <kbd>Alt</kbd> + <kbd>I</kbd> | Importar Sinais (.json) |
| <kbd>Alt</kbd> + <kbd>N</kbd> | Adicionar Novo Sinal |
| <kbd>Alt</kbd> + <kbd>C</kbd> | Alternar Inspeção de Coordenadas (Mira) |
| <kbd>Alt</kbd> + <kbd>V</kbd> | Mostrar/Ocultar o Sinal Ativo no Gráfico |
| <kbd>+</kbd> ou <kbd>-</kbd> | Aplicar Zoom In / Zoom Out |
| <kbd>0</kbd> (Zero) | Centralizar e Restaurar Escala do Gráfico |
| <kbd>Esc</kbd> | Sair da Tela Cheia ou Fechar Modais Abertos |

---

## 🧮 Funções Matemáticas Suportadas

O interpretador de equações entende a sintaxe matemática padrão da biblioteca `math.js` (ex: potências usam `^`, funções trigonométricas usam `sin(t)`, `cos(t)`, `exp(t)`).

**Funções Especiais Embutidas para Engenharia:**
* `rect(t)` : Pulso Quadrado Unitário (largura 1, centrado em 0).
* `tri(t)` : Pulso Triangular Unitário (base 2, centrado em 0).
* `sinc(t)` : Seno Cardinal $\frac{\sin(\pi t)}{\pi t}$.
* `u(t)` : Degrau Unitário de Heaviside.
* `dirac(t)` : Impulso de Dirac $\delta(t)$ (Aproximação visual gráfica para cálculo).
* `dublet(t)` : Função Dupleto (Derivada do impulso de Dirac).
* `ramp(t)` : Função Rampa ($t \cdot u(t)$).
* `pulse(t, a, b)` : Pulso unitário personalizado com início em $a$ e fim em $b$.

---

## 🚀 Como Executar

Este laboratório foi construído com a filosofia **Zero-Build** (Single File App). Nenhuma dependência pesada de servidor (como Node.js) ou instalação é exigida.

1. Baixe o arquivo `index.html`.
2. Dê um duplo clique para abri-lo em qualquer navegador web moderno (Google Chrome, Firefox, Edge, Safari).
3. Pronto! Todas as dependências externas são resolvidas via CDN.

> **💡 Dica:** Se precisar usar offline, basta fazer o download das bibliotecas referenciadas no `<head>` (`math.js` e `tailwindcss.js`) e mapeá-las localmente no HTML.

---

## 💻 Tecnologias Utilizadas

* **HTML5 & CSS3:** Semântica e estrutura base.
* **JavaScript Puro (Vanilla JS):** Toda a lógica matemática, de estado e interatividade de interface.
* **HTML5 Canvas API:** Motor de plotagem matemática próprio, ultraleve e construído do zero.
* **Tailwind CSS (via CDN):** Estilização utilitária rápida com modo dark nativo, Glassmorphism e alta responsividade.
* **Math.js:** Motor de avaliação sintática e cálculo numérico para as equações matemáticas.

---
*Feito com ☕ para descomplicar Sinais e Sistemas.*
