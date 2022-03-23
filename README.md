
![desafio](https://user-images.githubusercontent.com/49800445/159580137-2b8042a1-ed51-4229-9ce2-f212534d32bd.png)
___
- Autor: Marcos Luiz Cliton Bezerra
+ https://www.linkedin.com/in/marcos-bezerra-252375197
---

### Sumário
1. [Entendendo as regras do Desafio](#section1)<br>
  1.1 [Desafio](#section2)<br>
  1.2 [Objetivo](#section3)<br>
2. [Preparação dos Dados](#section4)<br>
  2.1 [Desenvolvimento](#section5)<br>
  2.2 [Tipos de Jogadas no Poker](#section6)<br>
  2.3 [Transformando em uma Lista](#section7)<br>
  2.4 [Validação da quantidade de cartas](#section8)<br>
3. [Modelagem da codificação que interpreta o valor das cartas](#section9)<br>
  3.1 [Estrutura criada para interpretação das cartas](#section10)<br>
  3.1 [Verificando um empate](#section11)<br>
4. [Evaluation Algoritmo e Métricas](#section12)<br>
  4.1 [Metodologia para os testes](#section13)<br>
  4.1 [Execução dos testes](#section14)<br>

<a id='section1'></a>
<h3>Entendendo as regras do Desafio</h3>

<a id='section2'></a>
<h3>Desafio</h3>
Um famoso cassino de repente enfrenta um grande declínio de sua receita. Então eles decidem oferecer uma versão online do jogo de Poker. Pode ajudá-los escrevendo um algoritmo para ranquear as mãos de Poker?

<a id='section3'></a>
<h3>Objetivo</h3>
Crie um programa em python que represente uma mão de Poker chamada "PokerHand" e crie os métodos/classes para comparar uma mão de Poker com outra e definir a vencedora.

+ Esse programa PokerHand deverá ter um construtor que aceite uma String contendo 5 cartas.
+ Um espaço será usado como separador de cada carta.
+ Cada carta consiste em dois caracteres como informados anteriormente. Exemplo de utilização.
+ poker_hand_1 = PokerHand("KS 2H 5C JD TD") poker_hand_2 = PokerHand("9C 9H 5C 5H AC")
+ result = poker_hand_1.compare_with(poker_hand_2)
+ O resultado deve ser um enumerado com os resultados: WIN ou LOSS.

<h3>Testes Unitários</h3>
O funcionamento da solução deve ser garantida através de testes unitários. A seguir encontra-se um trecho de código com as comparações e seus respectivos resultados.
Essas são as comparações mínimas que devem ser feitas para garantir o funcionamento do seu programa. Utilize esse código como base da sua implementação dos testes unitários.

<h3>Sequência do maior para o menor valor de cada carta</h3>

- 2, 3, 4, 5 ,6 ,7 , 8, 9, 10 T, 11 J (Valete), 12 Q (Rainha), 13 K (Rei), 14 A (Ace)

<h3>Naipes</h3>

- S (Espadas), H (Copas), D (Ouros), C (Paus)

![handpoker](https://user-images.githubusercontent.com/49800445/159580031-9fe7e21a-295e-40a2-bd6d-e48e45709790.png)

Links de referência sobre o jogo de Poker:
+ https://www.partypoker.com/pt-br/how-to-play/hand-rankings
+ https://pokerdicas.com/regras/regras-de-desempate-no-texas-holdem/
+ https://starspoker.com.br/mao-de-forca/

<a id='section4'></a>
<h3>Preparação dos Dados</h3>

<a id='section5'></a>
<h3>Desenvolvimento</h3>
O desafio consiste em verificar qual mão de poker é mais alta. Conforme informado para os testes não teremos jogadas com empate. Para os valores das cartas foi criado uma sequência numérica que representa a ordem inversa de grandeza para cada tipo de jogada existente no poker.

<a id='section6'></a>
<h3>Tipos de Jogadas no Poker</h3>
Tipos de jogadas no Poker em ordem decrescente de maior valor

- 1º  ***ROYAL STRAIGHT FLUSH*** é uma sequência, de 10-J-Q-K-A, do mesmo naipe.
- 2º  ***STRAIGHT FLUSH*** => cinco cartas em sequência do mesmo naipe 
- 3º  ***FOUR OF A KIND*** => quatro cartas de mesmo valor
- 4º  ***FULL HOUSE*** => trinca + par, 3 cartas de um valor e um par de outro valor
- 5º  ***FLUSH*** => cinco cartas em qualquer sequência do mesmo naipe        
- 6º  ***STRAIGHT*** => Cinco cartas em sequência.
- 7º  ***THREE OF A KIND*** => Três cartas de mesmo valor.
- 8º  ***TWO PAIR*** => duas cartas de um valor e outras duas cartas de outro valor.
- 9º  ***ONE PAIR*** => um par de cartas independente do naipe
- 10º ***HIGH CARD*** => carta de maior valor

<a id='section7'></a>
<h3>Transformando em uma Lista</h3>
A informação com as cartas de cada jogador é recebida em forma de string ("TC TH 5C 5H KH"). Que é transformada em uma lista, contendo cada posição das cartas ['TS','JS','QS','KS','AS']. Dentre as validações existentes, inicialmente é feito uma verificação se a quantidade de cartas recebidas é igual a cinco.

![qtd_invalida](https://user-images.githubusercontent.com/49800445/159579870-d424eeda-3b78-41b8-b246-cfc84ad3dc8c.png)

É utilizado um dicionário onde os valores que estão no formado string são transformados para tipo numérico e as letras transformadas em números.

values_ = {'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9,'T':10,'J':11,'Q':12,'K':13,'A':14}

Nesta fase já estamos com as cartas nos seguintes formatos:
+ lista das cartas: [[13, 'H'], [10, 'H'], [10, 'C'], [5, 'H'], [5, 'C']]
+ valores das cartas: [13, 10, 10, 5, 5]
+ naipes das cartas: ['H', 'H', 'C', 'H', 'C']

<a id='section8'></a>
<h3>Validação da quantidade de cartas</h3>
Na formatação da lista de cartas é realizado uma validação se todos os valores e naipes que foram informados estão corretos. Se houver qualquer divergência é criado uma except de erro.

No exemplo de erro temos no log que um dos jogadores recebeu uma carta que não existe no jogo com o valor 'B' ("BS TD KC JC 7C").
![valor_carta_errado](https://user-images.githubusercontent.com/49800445/159579771-93e1b67f-f888-4e89-bab0-158920c1b051.png)

<a id='section9'></a>
<h3>Modelagem da codificação que interpreta o valor das cartas</h3>

<a id='section10'></a>
<h3>Estrutura criada para interpretação das cartas</h3>
Na função best_hand, a primeira validação é feita para a sequência de cartas que possui o maior tipo de jogada.

Hand_1: (8, [10, 5], [13])
+ 8      . o valor 8 representa o jogo Dois Pares
+ [10,5] . que temos Dois Pares das cartas 10 e 5
+ [13]   . esta carta é o kicker, que é utilizada para o desempate

Hand_2: (9, [7],[11,5,4])

No caso acima temos uma mão com o valor 8 que representa TWO PAIR e a outra com o valor 9 que equivale a ONE PAIR. A primeira mão ganha por ser mais forte, e isto é validado pelo valor numérico atribuido para cada tipo de jogada. O valor 8 representa que é mais forte que o 9, ou TWO PAIR ganha de ONE PAIR. 

<a id='section11'></a>
<h3>Verificando um empate</h3>
No caso de haver um empate as cartas estão separadas de forma que nos possibilitam fazer o uso do maior valor para o menor. Desta forma nesta estrutura criada é possível identificar qual o tipo de jogada, as cartas que fazem parte do tipo de jogo e as cartas que serão utilizadas para desempate.

Para o desempate existe duas listas que foram criadas. O que diferencia é a característica de terem cinco cartas em sequência (também incluído o FULL HOUSE) ou naipes na jogada.

list_jogos=[1,2,4,5,6]
- 1º  ***ROYAL STRAIGHT FLUSH*** é uma sequência, de 10-J-Q-K-A, do mesmo naipe.
- 2º  ***STRAIGHT FLUSH*** => cinco cartas em sequência do mesmo naipe 
- 4º  ***FULL HOUSE*** => trinca + par, 3 cartas de um valor e um par de outro valor
- 5º  ***FLUSH*** => cinco cartas em qualquer sequência do mesmo naipe        
- 6º  ***STRAIGHT*** => Cinco cartas em sequência.

list_kicker=[3,7,8,9,10]
- 3º  ***FOUR OF A KIND*** => quatro cartas de mesmo valor
- 7º  ***THREE OF A KIND*** => Três cartas de mesmo valor.
- 8º  ***TWO PAIR*** => duas cartas de um valor e outras duas cartas de outro valor.
- 9º  ***ONE PAIR*** => um par de cartas independente do naipe
- 10º ***HIGH CARD*** => carta de maior valor

<a id='section12'></a>
<h3>Evaluation Algoritmo e Métricas</h3>

<a id='section13'></a>
<h3>Metodologia para os testes</h3>
Esta separação facilita devido ao tipo de desempate que acontece pelas cartas que compõe a jogada e pelo kicker.
O retorno após a comparação de cartas para determinar qual a maior jogada são 'WIN' e 'LOSS'.
A realização dos testes é feita utilizando a lib unittest, o retorno é validado "assertTrue( expr , msg = Nenhum )" se o resultado é igual ou não ao predito.

![Captura de Tela 2022-03-22 às 22 57 27](https://user-images.githubusercontent.com/49800445/159606668-f08a9828-e52a-44d6-8ce4-b3c4c399b5c7.png)

<a id='section14'></a>
<h3>Execução dos testes</h3>
Se houver algum teste em que o resultado seja diferente do predito o programa para de executar e apresenta uma mensagem de erro. Sendo todos os casos executados no teste sem erro, é apresentado uma mensagem de Ok.

![Captura de Tela 2022-03-22 às 23 04 46](https://user-images.githubusercontent.com/49800445/159608375-3e3b4eb0-61f9-413d-9fbe-3b157527fdfc.png)

