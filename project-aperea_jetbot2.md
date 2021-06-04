---
layout: page
title: Project-APEREA
subtitle: Jetbot 2
---
Era uma tarde de férias de 1984, na televisão era transmitido o filme O Império Contra-Ataca, na época era o segundo filme da série Star Wars. Então me encontrei com Luke e o sinistro Darth Vader num mundo fascinante e altamente fora da realidade. Um filme do futuro (um ponto importante eu ainda não havia assistido o primeiro filme), mas o que mais me fascinou 

![sw-2](https://takodana.files.wordpress.com/2016/01/star-wars-empire-strikes-back-poster.jpg?w=1024&h=1448)


### Uma visão particular

Muitos associam a tecnologia a uma imagem crua e cinza do alumínio, a solidez e a resistência do aço, ao formato padronizado do plástico, a submissão a um aplicativo central… levando nos a um pensamento de frieza e de pouca maleabilidade. Além disso somos levados a crer que dominamos a tecnologia ou que a desenvolvemos para o nossos benefícios porém sabemos que pouco a pouco somos levados a depender cada vez mais dela. Nos submetemos dia-a-dia ao domínio perverso das conversas de chats, aos posts desatualizados que precisam ser atualizados.

Passamos a ser dominados e não dominantes.

Passamos a marchar conforme o compasso dos aplicativos. A entender a ótica do computador.

E o que era para ser um meio…se torna um fim.

É hora de repensarmos a maneira como fazemos da tecnologia nossa aliada.

É hora de fazermos dos aplicativos, tintas para as telas da tecnologia que os pincéis descreverão numa paisagem futurística.

É preciso pensar a tecnologia como uma arte. E a arte é algo mutável, sem limites, sem donos.


### Short bio

Marco Reis nasceu em 15 de março de 1971 na cidade de Três Lagoas – MS, na época Mato Grosso era um único estado. Marco saiu do estado “The Walking Dead” em 20 de abril de 2003. Tem experiência em gestão de projetos industriais, incluindo a implantação de duas fábricas de automóveis no Brasil (Renault em Curitiba e Ford em Camaçari) assim como passagens na indústria siderúrgica, geração de energia e automação & robótica, especialmente na ABB. Marco desenvolveu projetos nas áreas de ferramentas robóticas e manipuladores, veículos autônomos, gerenciamento de ativos, RCM, TPM, confiabilidade e manutenção em equipamentos críticos, e avaliação na aplicação de FMEA.

Em 2005 Deus empurra-o a ação, e entra em um retiro espiritual aprendendo profundamente Rm5:1-5. O restabelecimento total à vida normal chega em 2008 e em 2010 escuta a voz do coração, toma a decisão de se dedicar a pesquisa científica. Aquilo que era uma lembrança nos sonhos de uma criança de 13 anos, passa a ser sua obstinação, passa a ser a sua busca incessante. Fazer robótica, e “O império contra ataca” tem um papel crucial em tudo isso: despertando logo cedo o brilho pelas coisas impossíveis.

Atualmente segue o interesse do seu coração realizando pesquisa na área de robótica, coordena dois projetos no Senai Cimatec e lidera o grupo do Instituto Brasileiro de Robótica (BIR) em parceria com o Instituto Alemão de Inteligência Artificial (DFKI).

Marco é formado em engenharia elétrica pela UFPR e mestrado em engenharia de produção pela UFSC, atualmente é doutorando no curso de pós-graduação em Mecatrônica da UFBA.

Aloooha!!!


# Desafio de Robótica
                            
Este repositório contém os arquivos necessários para a realização da simulação do desafio referente ao Laboratório de Robótica e Sistemas Autônomos para atuação como estagiário ou bolsista no SENAI CIMATEC.


# Objetivo
O robô deverá chegar na região de uma luminária de chão que está ao lado de uma placa STOP em no máximo 2 minutos, partindo do ponto inicial próximo a placa INÍCIO.
# Resolução
As funções implementadas estão apresentadas abaixo:

### ![image](https://user-images.githubusercontent.com/21108858/110886799-fb3b4380-82c7-11eb-9172-e573956c4599.png)
                                            
_**Init System**_: Inicializa a comunicação entre o controlador e o Webots e armazena o tempo de simulação e os IDs das rodas, leds e sensores. Configura as rodas e habilita os sensores. Configura o estado forward (em frente) como default da máquina de estados da direção do robô.

_**Avoid Obstacle**_: Verifica se há obstáculos próximos através da distância calculada a partir dos valores obtidos pelos sensores. Se houver um obstáculo, é calculado um modificador que ajusta os parâmetros das rodas, através do qual é atualizada a direção do robô na máquina de estados. 

_**Stop Position**_: O robô identifica o local em que ele deve parar através da análise da intensidade de luminosidade obtidas pelos sensores de luminosidade. Nesta função é obtida a média dos valores de saída dos sensores.

_**Direction State Machine**_: Gerencia a direção do robô: forward (em frente), left (esquerda) e right (direita).

_**Set Motor Speed**_: Ajusta a velocidade das rodas possibilitando que o robô modifique sua direção ao encontrar um obstáculo ou pare ao identificar o ponto de parada.

_**Robot Cleanup**_: Encerra a comunicação entre o controlador e o Webots.

## Principais ajustes
Para que o robô se tornasse capaz de cumprir a missão foi feita uma correção no cálculo da distância, corrigindo o valor do parâmetro da distância máxima (Max_distance) na função:
###### _distance = Max_distance * (1.0 - (sensor_value / MAX_SENSOR_VALUE))_
                   
A distância máxima de detecção dos sensores do Pioneer 3-DX , conforme indicado na lookup table, é igual 5m.

Por fim, foram adicionados três sensores de luz para a identificação do ponto de parada através da intensidade da luminosidade do local.
# Resultado
O robô é capaz de chegar ao ponto de parada, evitando os obstáculos, em um tempo de execução de 1 min 16 s.
# Referência 
1. Cyberbotics. **Lightsensor.** Acesso em: 8 de Março de 2021 [https://cyberbotics.com/doc/reference/lightsensor].
2. Cyberbotics. **Pioneer 3-DX.** Acesso em: 8 de Março de 2021 [https://cyberbotics.com/doc/guide/pioneer-3dx].
3. Cyberbotics. **Distance Sensor.** Acesso em: 8 de Março de 2021 [https://cyberbotics.com/doc/reference/distancesensor].