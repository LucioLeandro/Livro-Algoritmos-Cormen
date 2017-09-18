<h1>Capítulo 1</h1>

<h2>A função dos algoritmos na computação<h2/>

<h3>Resumo :</h3>

Algoritmos são estruturas bem definidas de sequencia de instruções que recebe um dado ou dados,
 o trata e retorna uma saída esperada.

 Com isso, podemos solucionar problemas ou uma instância de problema (uma instância de problema consiste na entrada
 que satisfaz a quaisquer restrições impostas pelo enunciada do problema, que é necessário para o cálculo
 da solução do problema) .

 Muitos problemas são resolvidos através de algoritmos, um exemplo bem expressivo para isso,
 é o Projeto Genoma Humano, considerada uma das maiores façanhas da humanidade.
 Um projeto iniciado em 1990 com o principal objetivo de determinar a sequencia de todas as
 bases do DNA humano, mapeá-los e armazená-los em banco e desenvolver meios para o estudo da biologia
 e medicina, abrindo portas também para estudo de outros organismos vivos.

 A lista de problemas que podem ser solucionados através de algoritmos é extensa e inesgotável.

 Existe também os chamados "Problemas difíceis", que são problemas os quais não se conhece nenhuma
 solução eficiente, porém é possível desenvolver boas soluções ainda que não a melhor, mas bem próxima.
 Um subconjunto dos Problemas difíceis é o NP-completo.


<h3>EXERCÍCIO :</h3>

 **1.1-1 FORNEÇA UM EXEMPLO REAL NO QUAL APAREÇA UM DOS PROBLEMAS COMPUTACIONAIS A SEGUIR : ORDENAÇÃO; DETERMINAÇÃO DA MELHOR ORDEM DE MULTIPLICAÇÃO DE MATRIZES OU LOCALIZAÇÃO DA ENVOLTÓRIA CONVEXA.**

<b>RESPOSTA :</b> Atualmente costumo a jogar um jogo mobile de estratégia chamado clash Royale,  onde no jogo se possui cartas e cada carta tem como propriedades : raridade e quantidade de elixir, e na interface do jogo se tem a opção de ordenar as cartas por raridade ou por quantidade de elixir, onde com certeza foi usado um algoritmo de ordenação para a solução desse problema.



 **1.1-2 ALÉM DA VELOCIDADE, QUE OUTRAS MEDIDAS DE EFICIÊNCIA PODERIAM SER USADAS EM UMA CONFIGURAÇÃO REAL?**

<b>RESPOSTA :</b> - Espaço de memória utilizado pelo algoritmo.<br>
           - A exponencialidade do algoritmo de acordo com a taxa sua taxa de   crescimento

 **1.1-3 SELECIONE UMA ESTRUTURA DE DADOS QUE VOCÊ JA TENHA VISTO ANTES E DISCUTA SEUS PONTOS FORTES e SUAS LIMITAÇÕES.**

**RESPOSTA :** Para fazer esta análise escolhi a estrutura *Lista ligada*.
Sendo bem direto, um vetor simples, é rápido para recuperarmos determinado dado quando sabemos onde queremos buscá-lo, ou seja, basta sabermos a posição em que o dado está armazenada e passar como indexador, porém, para inserirmos dados em um vetor de maneira não sequencial é uma atividade custosa, pois temos que : <br>

<ul>
  <li>Verificar se o vetor ainda tem capacidade disponível para armazenar o novo dado.</li>
  <li>Caso o vetor ainda possua capacidade :
  <ul>
    <li>Armazenar o novo dado na primeira posição livre, se for de maneira sequencial</li>
    <li>Se for no meio, temos que rearrumar o vetor empurrando para uma posição a frente, todos os dados a partir da posição onde queremos armazenar o novo dado.</li>
   </ul>
  </li>
  <li> Caso não haja mais capacidade :
  <ul>
  <li>Criar um novo vetor com maior capacidade que o atual.</li>
  <li>copiar todos os dados do vetor atual para o vetor novo.</li>
  <li>Inserir o novo dado na primeira posição livre, se for de maneira sequencial</li>
  <li>Se não for sequencial, rearrumar o vetor empurrando para uma posição a frente, todos os dados a partir da posição onde queremos armazenar o novo dado.</li>
  <li>E por ultimo, tornar o vetor novo, o atual.</li>
</ul>

*pequeno exemplo de código de vetor em Java, no paradigma orientado a objetos*<br><br>

```
// O método abaixo é responsável por garantir que o vetor tenha espaço para armazenar o novo dado,
 já que em Java não é possível fazer realocação de vetor,
  então cria-se um novo vetor, com maior capacidade(nesse caso, dobro a capacidade)

private void garanteEspaco() {
   if(totalDeDados == dados.length) {
       Dado[] novoArray = new Dado[dados.length*2];
       for(int i = 0; i < dados.length; i++) {
           novoArray[i] = dado[i];
       }
       this.dados= novoArray;
   }

   // o método abaixo adiciona um novo dado na posição desejada.

   public void adiciona(int posicao, Dado dado) {
       this.garanteEspaco();
       if(!posicaoValida(posicao)) {
           throw new IllegalArgumentException("posicao invalida");
       }
       for(int i = totalDeDados - 1; i >= posicao; i-=1) {
           dados[i+1] = dados[i];
       }
       dados[posicao] = dado;
       totalDeDados++;
   }
}
```

Para resolver esse problema, existe a *Lista ligada*.<br><br>

Resumidamente, diferente de um vetor, a lista ligada armazena os dados em lugares diferentes da memória, porém um dado aponta para o outro, indicando qual o próximo elemento.<br>

*pequeno exemplo de código de vetor em Java, no paradigma orientado a objetos*<br><br>


```
package estuturadedados.listaligada;

Public Class Dado {
  private Object dado;
  private Dado proximo;
}
```

<h5>Ponto forte</h5>

Isso permite a facilidade de adicionar um novo elemento em qualquer posição da lista de maneira eficiente e rápida.

<h5>Ponto fraco</h5>

A depender de alguns fatores, como por exemplo, o tamanho da lista, a operação de recuperar um elemento da lista em posição aleatória pode levar tempo linear, pois é preciso navegar pelas referências até que o dado desejado seja encontrado.

 **1.1-4 EM QUE ASPECTOS OS PROBLEMAS DO CAMINHO MAIS CURTO E DO CAIXEIRO VIAJANTE ANTERIORES SÃO SEMELHANTES ? EM QUE ASPECTOS SÃO DIFERENTES ?**

**RESPOSTA :** Ambos os problemas se assemelham em questão de ter como solução a menor distância entre pontos, Porém são algoritmos distintos.<br>
a solução do problema menor caminho, é o menor caminho entre um nó inicial e um nó final, já a solução do problema caixeiro viajante é a menor rota entre todos os nós existentes. Sendo que existem algoritmos eficientes para solucionar o problema de menor caminho, já para solucionar o problema do caixeiro viajante que é um problema *problema difícil - NP-completo*, ainda não há algoritmos eficientes conhecidos, contudo, há algoritmos que em determinadas hipóteses nos retorna uma menor distância não muito acima da menor distância possível.

 **1.1-5 MOSTRE UM PROBLEMA REAL NO QUAL APENAS A MELHOR SOLUÇÃO SERVIRÁ. EM SEGUIDA, APRESENTE UM PROBLEMA EM QUE BASTE UMA SOLUÇÃO QUE SEJA "APROXIMADAMENTE" A MELHOR.**

**RESPOSTA :** Se apenas a melhor solução servirá, nada melhor do que exemplificar com dinheiro. As instituições bancárias lucram com o que chamamos de *Spread bancário*, que nada mais é que, a diferença entre os juros que a instituição cobra ao emprestar dinheiro aos clientes, e os rendimentos  pagos a ele por seus investimentos.

<h6>Exemplo caso 1:</h6><br>

Imagine a seguinte hipótese : Lúcio aplica R$ 100,00 na poupança, cuja taxa de rendimento é de 6%. O banco pega esses R$ 100,00 e faz um empréstimo a Leandro, e cobra juros de 15% ao mês ao mesmo.<br>
Um mês depois Leandro precisa pagar R$ 115,00 para saldar sua dívida com a instituição.<br>
Desses R$ 115,00, o banco devolve o dinheiro de Lúcio com 6% a mais (R$ 106), e fica com R$ 9,00 de lucro.<br><br>

Tendo isso em mente, é necessário que o algoritmo responsável por todos esses cálculos, que também leva em consideração outros fatores não citados aqui, seja eficiente, pois a instituição não pode perder dinheiro, e também não pode pagar os rendimentos corretos aos seus clientes.

<h6>Exemplo caso 2:</h6><br>

...
