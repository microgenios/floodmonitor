# Flood Monitor

Documentação do Projeto Flood Monitor.

A Tabela a seguir apresenta o glossário das variáveis registradas pelo sistema Flood Monitor. Além das medições de nível de água obtidas pelo sensor ultrassônico (`value`), são registrados parâmetros de comunicação LoRaWAN, como RSSI, SNR, frequência de operação, fator de espalhamento (*Spreading Factor*) e taxa de codificação (*Coding Rate*), permitindo avaliar simultaneamente o desempenho da rede de comunicação e as condições hidrológicas monitoradas. Também são armazenadas informações de geolocalização e estado energético do dispositivo, possibilitando análises espaciais e gerenciamento remoto da infraestrutura de monitoramento.

| Campo | Significado | Descrição |
|---------|---------|---------|
| **Datasource Name** | Nome da Fonte de Dados | Identifica a origem dos dados cadastrada na plataforma Flood Monitor. É utilizado para organizar informações provenientes de diferentes projetos, localidades ou grupos de sensores. |
| **Variable Name** | Nome da Variável | Nome atribuído ao sensor ou à variável monitorada. Exemplos: `FloodMonitor1`, `SensorDeAlagamento`, `SensorA`, `Ponte01`. |
| **Value** | Valor | Corresponde ao valor processado disponibilizado pela plataforma. Para sensores de alagamento, normalmente representa a altura da lâmina d'água em milímetros (mm), calculada a partir da medição ultrassônica e da calibração do sensor. Exemplo: `Value = 100` indica uma lâmina d'água de 100 mm. |
| **Unit** | Unidade | Unidade de medida associada ao campo Value. Normalmente expressa em milímetros (mm), mas pode ser configurada durante o cadastro da variável na plataforma. |
| **Date** | Data/Hora | Data e horário em que o pacote de dados foi recebido pelo servidor LoRaWAN e processado pela plataforma Flood Monitor. Permite análises históricas e séries temporais. |
| **Description** | Descrição | Informações detalhadas do pacote de dados recebido, incluindo observações adicionais relacionadas ao sensor ou ao processamento realizado. |
| **id** | Identificador | Identificador único atribuído ao registro armazenado no banco de dados. Permite rastreabilidade individual de cada medição. |
| **dev_eui** | Device Extended Unique Identifier | Identificador único global do dispositivo LoRaWAN. Utilizado durante a autenticação na rede e para associar corretamente os dados ao sensor correspondente. |
| **bat** | Battery Level | Nível de carga da bateria do dispositivo. Normalmente expresso em Volts (V). Para baterias Li-Ion, a faixa típica varia entre 4,2 V (carga total) e 3,2 V (limite de descarga). |
| **dis** | Distance | Distância medida pelo sensor ultrassônico entre o transdutor e a superfície da água. Expressa em milímetros (mm). Esta medida não representa diretamente a altura da enchente. O campo `Value` contém o nível de água calculado após a calibração. |
| **err** | Error Flag | Indicador de erro do sensor. Valor `0` indica operação normal. Valores diferentes de zero podem indicar falhas de leitura, comunicação ou funcionamento do dispositivo. |
| **gw** | Gateway ID | Identificador do gateway LoRaWAN responsável pela recepção do pacote transmitido pelo sensor. Permite avaliar cobertura e desempenho da rede. |
| **rssi** | Received Signal Strength Indicator | Intensidade do sinal recebido pelo gateway, expressa em dBm. Quanto mais próximo de zero, melhor o sinal. Referência: -30 dBm (excelente), -70 dBm (muito bom), -90 dBm (adequado), -120 dBm (fraco), abaixo de -130 dBm (risco de perda de comunicação). |
| **snr** | Signal-to-Noise Ratio | Relação sinal-ruído da comunicação LoRaWAN, expressa em dB. Valores maiores indicam melhor qualidade do enlace. Referência: >10 dB (excelente), 0 a 10 dB (boa), -10 a 0 dB (aceitável), < -20 dB (crítica). |
| **frq** | Frequency | Frequência utilizada na transmissão do pacote LoRaWAN. No Brasil, a faixa ISM utilizada situa-se próxima de 915 MHz, conforme regulamentação da Anatel. |
| **bwd** | Bandwidth | Largura de banda utilizada pelo rádio LoRa. Valores típicos: 125 kHz, 250 kHz e 500 kHz. Larguras menores aumentam a sensibilidade do receptor e o alcance da comunicação. |
| **sf** | Spreading Factor | Fator de espalhamento do protocolo LoRa. Valores típicos variam de SF7 a SF12. Valores maiores proporcionam maior alcance e robustez da comunicação, porém aumentam o tempo de transmissão e o consumo energético. |
| **cr** | Coding Rate | Taxa de correção de erros utilizada pelo protocolo LoRa. Valores típicos: 4/5, 4/6, 4/7 e 4/8. Taxas maiores aumentam a confiabilidade da comunicação em ambientes com interferência, porém aumentam o tamanho do pacote e o consumo de energia. |
| **air** | Time on Air | Tempo necessário para transmitir um pacote LoRaWAN. Depende do tamanho do pacote, largura de banda (BW), fator de espalhamento (SF) e taxa de codificação (CR). Influencia diretamente o consumo energético e a capacidade da rede. |
| **lat** | Latitude | Coordenada geográfica de latitude do local de instalação do sensor. Utilizada para georreferenciamento e visualização em mapas. |
| **lon** | Longitude | Coordenada geográfica de longitude do local de instalação do sensor. Em conjunto com a latitude, permite identificar precisamente o ponto monitorado. |
| **alt** | Altitude | Altitude do local do sensor em relação ao nível médio do mar, expressa em metros (m). Pode ser utilizada em análises hidrológicas e integração com sistemas de informações geográficas (SIG). |
