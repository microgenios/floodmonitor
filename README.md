# floodmonitor
Documentação do projeto Floodmonitor

A Tabela X apresenta o glossário das variáveis registradas pelo sistema Flood Monitor. Além das medições de nível de água obtidas pelo sensor ultrassônico (value), são registrados parâmetros de comunicação LoRaWAN, como RSSI, SNR, frequência de operação, fator de espalhamento (Spreading Factor) e taxa de codificação (Coding Rate), permitindo avaliar simultaneamente o desempenho da rede de comunicação e as condições hidrológicas monitoradas. Também são armazenadas informações de geolocalização e estado energético do dispositivo, possibilitando análises espaciais e gerenciamento remoto da infraestrutura de monitoramento.

| Campo               | Significado                        | Descrição                                                                                                                       |
| ------------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Datasource Name** | Nome da Fonte de Dados             | O campo Datasource Name identifica a fonte de dados cadastrada na plataforma de monitoramento. Esse parâmetro é utilizado para organizar os dados provenientes de diferentes projetos, localidades ou grupos de sensores.                                                     |
| **Variable Name**   | Nome da Variável                   | Nome do Sensor. Exemplo> FloodMonitor1, Sensordealagamento, SensorA, etc.                                                                              |
| **Value**           | Valor                              | O campo Value corresponde a medida real medida pelo sensor ultrasonico, em milimetros. Exemplo: Quantidade de milimetros de chuva (Valor = 10), corresponde a 10 milimetros de água |                                                                              |
| **Unit**            | Unidade                            | Unidade de medida associada ao valor registrado.                                                                                |
| **Date**            | Data/Hora                          | Data e horário do registro da medição.                                                                                          |
| **Description**     | Descrição                          | Descrição textual da variável monitorada.                                                                                       |
| **id**              | Identificador                      | Identificador único do registro armazenado na plataforma.                                                                       |
| **dev_eui**         | Device Extended Unique Identifier  | Identificador único do dispositivo LoRaWAN, utilizado para autenticação e rastreamento do sensor na rede.                       |
| **bat**             | Battery Level                      | Nível de carga da bateria do dispositivo, geralmente expresso em porcentagem (%) ou tensão (V).                                 |
| **dis**             | Distance                           | Distância medida pelo sensor ultrassônico entre o sensor e a superfície da água. Normalmente expressa em milímetros (mm).       |
| **err**             | Error Flag                         | Indicador de erro do sensor. Valor 0 indica operação normal; outros valores podem indicar falhas de leitura ou comunicação.     |
| **gw**              | Gateway ID                         | Identificador do gateway LoRaWAN responsável por receber o pacote transmitido pelo sensor.                                      |
| **rssi**            | Received Signal Strength Indicator | Indicador da intensidade do sinal recebido pelo gateway, expresso em dBm.                                                       |
| **snr**             | Signal-to-Noise Ratio              | Relação sinal-ruído da comunicação sem fio, expressa em dB. Valores maiores indicam melhor qualidade de comunicação.            |
| **frq**             | Frequency                          | Frequência de transmissão utilizada pelo dispositivo LoRaWAN, expressa em Hz ou MHz.                                            |
| **bwd**             | Bandwidth                          | Largura de banda do canal LoRa utilizado na transmissão, normalmente expressa em kHz.                                           |
| **sf**              | Spreading Factor                   | Fator de espalhamento LoRa. Controla a taxa de transmissão, alcance e consumo energético. Valores típicos variam de SF7 a SF12. |
| **cr**              | Coding Rate                        | Taxa de codificação utilizada pelo mecanismo de correção de erros do protocolo LoRa. Exemplo: 4/5, 4/6, 4/7 ou 4/8.             |
| **air**             | Time on Air                        | Tempo necessário para transmitir um pacote LoRaWAN, geralmente expresso em segundos ou milissegundos.                           |
| **lat**             | Latitude                           | Coordenada geográfica de latitude do local de instalação do sensor.                                                             |
| **lon**             | Longitude                          | Coordenada geográfica de longitude do local de instalação do sensor.                                                            |
| **alt**             | Altitude                           | Altitude do local do sensor em relação ao nível médio do mar, expressa em metros (m).                                           |

