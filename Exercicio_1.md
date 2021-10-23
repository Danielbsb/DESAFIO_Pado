# Desafio Pado
## Resolução do Exercício 1 
Primeiro passo é definir as condições de contorno do problema, listando os principais requisitos, são eles:
Nome do Requisito | Descrição
------------------|-----------
Req 1| A saída deve ser na forma de uma onda quadrada
Req 2 | O circuito deve tratar pulsos de luz entre 10kHz a 100kHz;
Req 3 | Deve permitir um ajuste da tensão de limiar

Premissas:
1.	Como não foi definida a faixa do comprimento de onda da luz, considera-se que compreende à faixa infravermelho curta (Near Infrared - NIR) – de 750nm a 1000nm;
2.	O Duty-cycle dos pulsos de 10kHz a 100kHz é de 50%;
3.	Não tem restrição de espaço/área consumida do circuito;

Dentre as opções mais comuns de detectores, destacam-se os LDR, fotodiodos e os foto transistores. A opção mais barata são os LDR, que geralmente são formados por sulfeto de cádmio (CdS). Mas a resposta desse tipo de sensor é lenta e não contempla os requisitos de frequência de pulsação da luz. Resta então os fotodiodos e os foto transistores. Em termos de desempenho, tanto os foto transistores, quanto os fotodiodos atendem aos requisitos de projeto, muito embora seja possível observar que os fotodiodos apresentam respostas mais lineares e consomem menos corrente (por trabalharem na polarização reversa) e apesar de serem ligeiramente mais caros do que os foto transistores, apresentam-se como o melhor custo-benefício.
O Sensor selecionado foi o (VEMD10940F), que apresenta uma resposta em frequência boa e um range dinâmico razoável. Atuando-se como uma fonte de corrente controlada, os fotodiodos podem ser condicionados por meio de amplificadores de trans impedância, que são comumente feitos com amplificadores operacionais. Para projetar o circuito de condicionamento, um modelo simplificado do fotodiodo foi utilizado, considerando somente a capacitância interna, que é o que mais impacta na frequência de operação do receptor. O modelo utilizado está destacado abaixo:
<p align="center">
  <img src="https://user-images.githubusercontent.com/26283606/138553867-67c0e2a0-64f9-40bb-92b2-fa930aafc961.png" />
</p>
<p align="center">
Fig. 1 - Modelo simplificado utilizado para projetar o circuito de condicionamento.
</p>
A topologia escolhida para condicionar o sinal do fotodiodo é destacada na figura abaixo, que é baseada no documento TIDU535, da Texas Instruments. O amplificador operacional foi escolhido com base na sua largura de banda, *slew-rate*, e faixa dinâmica de saída, além de ter 2 unidades no mesmo encapsulamento. Com o objetivo de limitar a banda do amplificador de transimpedância, além de otimizar a estabilidade, aumentando a margem de fase, um capacitor é utilizado em paralelo ao resistor de realimentação. O divisor resistivo constituído de R3 e R2 tem a função de evitar a saturação do amplificador operacional, evitando problemas relacionados à resposta em frequência. Para realizar o ajuste de sensibilidade, utilizou-se a segunda unidade do amplificador operacional escolhido na configuração comparador.  O capacitor C4 atua como filtro passa baixas para evitar ruídos devido ao potenciômetro de ajuste, assim como o capacitor C3. 

<p align="center">
<img src="https://user-images.githubusercontent.com/26283606/138554368-8316ba30-aa63-43b9-86d7-e26ed2b98d0a.png"/>
</p>

A análise AC do ponto VF1 está destacada na figura abaixo, onde é possível observar uma boa resposta em frequência.
<p align="center">
  <img src="https://user-images.githubusercontent.com/26283606/138554412-c9d34671-ddee-42b9-a14e-29c4db7d1431.png"/>
</p>
A saída do amplificador de trans impedância possui um range dinâmico de aproximadamente 3,0V (traço marrom) e a saída do circuito (traço verde) apresenta uma forma de onda "quadrada" com T_r≈ 100ns, conforme ilustra a Figura abaixo.
<p align="center">
  <img src="https://user-images.githubusercontent.com/26283606/138554427-f0553479-45ec-45a8-a59d-036793092234.png"/>
</p>
A figura abaixo ilustra a resposta transiente dos pontos VF1 e Vout, para uma entrada de 100kHz (Configurada com Tr e Tf dados pelo datasheet do fotodiodo). O traço verde indica a saída Vout e a curva em marrom indica o sinal no ponto VF1.
<p align="center">
  <img src="https://user-images.githubusercontent.com/26283606/138554709-0b445e88-c4f1-4f04-a15a-1b2741b59ae0.png"/>
</p>

*OBS: Os circuitos foram simulados com o software TINA - Texas Instruments.*
