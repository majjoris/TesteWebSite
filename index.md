<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script> <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Algoritimo PSO

Inicialmente proposto por James Kennedy e Russell Elberthart em 1995 o PSO (_Particle Swarm Optimization-PSO_) é um algoritmo evolutivo baseado em inteligência de enxames que busca simular o comportamento de pássaros voando juntos em busca de um local ideal, cada desse pássaros também chamados de partícula possuem duas propriedades principais que são a sua posição e sua velocidade segundo Iraj Koohi e Voicu Z. Groza. Usando esses parâmetros buscam em um espaços já designado através de equações matemáticas a posição ideal, enquanto elas se movem cada partícula (armazena ou memoriza) sua melhor posição chamada de (pbest) e como a população é formada por mais de um indivíduo é possível obter o melhor entre os indivíduos chamado de (gbest), como isso as partículas conseguem ajustar suas posições no espaço de busca ficando cada vez mais próximas da melhor posição. A posição (x) e a velocidade (v) são modificadas com base na equação (1) e (2).

$$(1) v_{ji}(t+1)=wv_{ji}+c_1r_1(pB_{ij}(t)-x_{ij}(t))+c_2r_2(gB_{ij}(t)-x_{ij}(t)) $$

$$(2) x_{ij}(t+1)=x_{ij}(t)+v_{ij} $$

Onde:
- $$ v_{ji}(t+1) $$-é a velocidade da partícula i na iteração j. 

- $$ x_{ij}(t+1) $$-é a posição da partícula i na iteração j.
- $$ w $$-é o coeficiente de inércia.

- $$ c_1 $$-é o fator de aprendizado cognitivo.
- $$ c_2 $$-é o fator social de aprendizagem.
- $$r1 e r2$$-são números aleatórios em entre 0 e 1. 
  

  Os valores de v podem ser fixados em uma faixa quem são [vmin, vmax]  para que a partícula são saía do espaço de busca. O algoritmo PSO termina com gerações máximas ou a melhor posição de partícula do enxame, que não pode ser melhorado depois de uma quantidade suficientemente grande número de gerações.O funcionamento do algoritmo PSO está logo abaixo:
``` python
    Inicio Algoritmo
        Para i - 0 até n faça
            Para j de 1 a d faça
                x:-rand(min, max)
                v:-rand(0, vmax)
            Fim Para
            p:-x
            pbest - f(pi)
            Se pbest < vbest então
                gbest:= pbest
            Fim Se
        Fim Para
        Para i= 0 até n faça
            Para j = 0 até m faça
                v := w*v + c1*rand()*(pbest-x) + c2*rand()*(gbest-x)
                x:= v + x
            Fim Para
            fitness := f(x)
            Se fitness < pbest então
                pbest := fitness
                Se fitness < vbest então
                    gbest[i]:= fitness
                Fim Se
            Fim Se
        Fim Para
    Fim Algoritmo
```

