![desafio](https://user-images.githubusercontent.com/49800445/159580137-2b8042a1-ed51-4229-9ce2-f212534d32bd.png)

___
- Autor: Marcos Luiz Cliton Bezerra
+ https://github.com/marcos-bezerra/Desafio_DataH
---
<h3>Desafio</h3>
Um famoso cassino de repente enfrenta um grande declínio de sua receita. Então eles decidem oferecer uma versão online do jogo de Poker. Pode ajudá-los escrevendo um algoritmo para ranquear as mãos de Poker?

<h3>Objetivo</h3>
1. Crie um programa em python que represente uma mão de Poker chamada "PokerHand" e crie os métodos/classes nele para compar uma mão de Poker com outra e definir a vencedora.

+ Esse programa PokerHand deverá ter um construtor que aceite uma String contendo 5 cartas.
+ Um espaço será usado como separador de cada carta.
+ Cada carta consiste em dois caracteres como informados anteriormente. Exemplo de utilização.
+ poker_hand_1 = PokerHand("KS 2H 5C JD TD") poker_hand_2 = PokerHand("9C 9H 5C 5H AC")
+ result = poker_hand_1.compare_with(poker_hand_2)
+ O resultado deve ser um enumerado com os resultados: WIN ou LOSS.

<h3>Testes Unitários</h3>
2. O funcionamento da solução deve ser garantida através de testes unitários. A seguir encontra-se um trecho de código com as comparações e seus respectivos resultados.
Essas são as comparações mínimas que devem ser feitas para garantir o funcionamento do seu programa. Utilize esse código como base da sua implementação dos testes unitários.

<h3>Sequência do maior para menor valor de cada carta</h3>

- 2, 3, 4, 5 ,6 ,7 , 8, 9, 10 T, 11 J (Valete), 12 Q (Rainha), 13 K (Rei), 14 A (Ace)

<h3>Naipes</h3>

- S (Espadas)
- H (Copas)
- D (Ouros)
- C (Paus)

![handpoker](https://user-images.githubusercontent.com/49800445/159580031-9fe7e21a-295e-40a2-bd6d-e48e45709790.png)

Links de referência sobre o jogo de Poker:
+ https://www.partypoker.com/pt-br/how-to-play/hand-rankings
+ https://pokerdicas.com/regras/regras-de-desempate-no-texas-holdem/
+ https://starspoker.com.br/mao-de-forca/

<h3>Desenvolvimento</h3>

O desafio consiste em verificar qual mão de poker é mais alta. Conforme informado para os testes não teremos jogadas com empate. Para os valores das cartas foi criado uma sequência numérica que representa a ordem inversa de grandeza para cada tipo de jogada existente no poker. 

<h3>Tipos de jogadas no Poker</h3>

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

A informação com as cartas de cada jogador é recebida em forma de string ("TC TH 5C 5H KH"). Que é transformada em uma lista com o comando split, contendo cada posição das cartas da mão recebida ['TS','JS','QS','KS','AS']. Dentre as validações existentes, inicialmente é feito uma verificação se a quantidade de cartas recebidas é igual a cinco.

![qtd_invalida](https://user-images.githubusercontent.com/49800445/159579870-d424eeda-3b78-41b8-b246-cfc84ad3dc8c.png)

É utilizado um dicionário onde os valores que estão no formado string são transformados para tipo numérico e as letras transformadas em números.

values_ = {'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9,'T':10,'J':11,'Q':12,'K':13,'A':14}

Nesta fase já estamos com a mão de cartas nos formatos abaixo.
+ cartas de uma mão: [[13, 'H'], [10, 'H'], [10, 'C'], [5, 'H'], [5, 'C']]
+ valores das cartas: [13, 10, 10, 5, 5]
+ naipes das cartas: ['H', 'H', 'C', 'H', 'C']



![valor_carta_errado](https://user-images.githubusercontent.com/49800445/159579771-93e1b67f-f888-4e89-bab0-158920c1b051.png)
