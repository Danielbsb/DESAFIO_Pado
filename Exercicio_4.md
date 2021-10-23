# Desafio Pado
## Tarefa 4:
Realizar análise crítica dos pontos positivos e negativos do layout abaixo:
![image](https://user-images.githubusercontent.com/26283606/138555034-b34618b5-6911-4d94-894d-f2ce57d8a823.png)

O layout acima possui alguns pontos a serem melhorados, que são destacados a seguir:
### Melhor posicionamento dos componentes.
 O Componente gerador de clock está posicionado muito próximo à fonte chaveada, que gera grandes transientes de correntes e pode ocasionar diferenças de potencial no plano de terra próximo ao oscilador. Essa diferença pode causar distorções na forma de onda do clock, provocando problemas como o jitter.
### Comprimentos das linhas de Clock.
Outro ponto que pode ser melhorado é o comprimento dos sinais de clock, que devem ser do mesmo tamanho (ou o mais próximo possível) para evitar diferenças de fase entre os componentes, gerando problemas de sincronização (dependendo da frequência).
### Plano de Terra.
Muito embora existam recomendações distintas e controvérsias a esse respeito, dependendo da referência utilizada, a divisão entre os planos de terra digitais e analógicos pode ser otimizada se considerar o gerador de clock dentro do plano de terra analógico, isto é, próximo ao conversor ADC/DAC. Também não é recomendado utilizar componentes discretos para realizar o acoplamento entre os planos de terra. Ao invés disso, recomenda-se utilizar conexão física entre os planos de terra, em um único ponto, geralmente próximo à fonte de alimentação. 
### Capacitores de desacoplamento.
Quanto aos capacitores de desacoplamento, é possível observar que alguns estão muito distantes do componente e apresentam traços longos antes de conectar ao plano de terra. Recomenda-se posicioná-los o mais próximo possível do pino de alimentação correspondente, e utilizar o mínimo de comprimento de trilha possível na via que conecta ao plano de terra. Caso o posicionamento na camada de baixo seja possível, muitas vezes é melhor posicionar os capacitores na camada inferior, e utilizar vias conectando o pino de alimentação correspondente.
### Placement.
Observa-se também alguns sinais estão com conexões/trilhas muito longas, o que poderia ser evitado apenas invertendo o posicionamento dos Cis de sinais mistos.

Quanto aos pontos positivos, destaca-se a divisão entre os planos de terra analógicos e digitais, o posicionamento dos conectores de entrada e saída digitais/analógicos. 
