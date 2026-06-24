# Flood Monitor

Documentação do Projeto Flood Monitor

## Visão Geral

O Flood Monitor é uma plataforma de monitoramento de enchentes baseada em Internet das Coisas (IoT) e tecnologia LoRaWAN. O sistema foi desenvolvido para coletar, armazenar e visualizar dados hiperlocais de alagamentos e enchentes urbanas, auxiliando pesquisadores, órgãos públicos e equipes de defesa civil na análise e mitigação dos impactos causados por eventos hidrológicos extremos.

Além das medições de nível de água obtidas por sensores ultrassônicos, o sistema registra parâmetros de comunicação LoRaWAN, informações de geolocalização e indicadores do estado operacional dos dispositivos. Esses dados permitem avaliar simultaneamente as condições hidrológicas monitoradas e o desempenho da infraestrutura de comunicação sem fio.

---

# Glossário das Variáveis Registradas

## Datasource Name

**Significado:** Nome da Fonte de Dados

Identifica a fonte de dados cadastrada na plataforma Flood Monitor. Esse campo é utilizado para organizar informações provenientes de diferentes projetos, localidades ou grupos de sensores, facilitando a gestão de grandes redes de monitoramento.

---

## Variable Name

**Significado:** Nome da Variável

Identifica o sensor ou dispositivo responsável pela medição.

### Exemplos

* FloodMonitor1
* SensorDeAlagamento
* SensorA
* SensorPonte01

---

## Value

**Significado:** Valor Medido

Corresponde ao valor processado e disponibilizado pela plataforma Flood Monitor.

Para sensores de alagamento, esse valor normalmente representa a altura da lâmina d'água em milímetros (mm), calculada a partir da calibração do sensor ultrassônico.

### Exemplo

| Valor | Interpretação           |
| ----- | ----------------------- |
| 10    | 10 mm de lâmina d'água  |
| 100   | 100 mm de lâmina d'água |
| 500   | 500 mm de lâmina d'água |

---

## Unit

**Significado:** Unidade de Medida

Define a unidade associada ao campo **Value**.

### Exemplos

* mm (milímetros)
* cm (centímetros)
* m (metros)

A unidade é configurada durante o cadastro da variável na plataforma.

---

## Date

**Significado:** Data e Hora da Medição

Representa o instante em que o pacote de dados foi recebido pelo servidor LoRaWAN e processado pela plataforma Flood Monitor.

Esse campo permite a construção de séries temporais e análises históricas dos eventos de inundação.

---

## Description

**Significado:** Descrição

Contém informações detalhadas sobre o pacote de dados recebido, podendo incluir observações adicionais sobre o sensor, localização ou processamento realizado.

---

## id

**Significado:** Identificador do Registro

Identificador único atribuído a cada registro armazenado no banco de dados da plataforma.

Esse campo permite rastrear individualmente cada medição realizada.

---

## dev_eui

**Significado:** Device Extended Unique Identifier

Identificador único global do dispositivo LoRaWAN.

O DEV_EUI é utilizado durante o processo de autenticação na rede e garante que os dados recebidos sejam associados corretamente ao sensor correspondente.

### Exemplo

```text
70B3D57ED0075E28
```

---

## bat

**Significado:** Battery Level

Representa o estado de carga da bateria do dispositivo.

O valor pode ser utilizado para planejamento de manutenção preventiva e monitoramento remoto da autonomia energética dos sensores.

### Faixa típica para baterias Li-Ion

| Estado          | Tensão |
| --------------- | ------ |
| Carga Total     | 4.2 V  |
| 75%             | 4.0 V  |
| 50%             | 3.8 V  |
| 25%             | 3.5 V  |
| Descarga Limite | 3.2 V  |

---

## dis

**Significado:** Distance

Distância medida pelo sensor ultrassônico entre o transdutor e a superfície da água.

**Importante:** Este valor não representa diretamente a altura da inundação.

O campo **Value** é o resultado processado utilizado para representar a lâmina d'água.

### Exemplo

Sensor instalado a 1000 mm do solo:

| Distância medida (dis) | Nível de água (Value) |
| ---------------------- | --------------------- |
| 1000 mm                | 0 mm                  |
| 800 mm                 | 200 mm                |
| 500 mm                 | 500 mm                |
| 200 mm                 | 800 mm                |

---

## err

**Significado:** Error Flag

Indica possíveis falhas de operação do sensor.

### Valores típicos

| Valor | Significado          |
| ----- | -------------------- |
| 0     | Operação normal      |
| 1     | Erro de leitura      |
| 2     | Sensor desconectado  |
| 3     | Falha de comunicação |

Os códigos podem variar conforme a versão do firmware.

---

## gw

**Significado:** Gateway ID

Identificador do Gateway LoRaWAN responsável pela recepção do pacote transmitido pelo sensor.

### Exemplo

```text
a940477d26384157
```

Esse parâmetro permite avaliar cobertura e redundância da rede LoRaWAN.

---

## rssi

**Significado:** Received Signal Strength Indicator

Indica a intensidade do sinal recebido pelo gateway.

Unidade: **dBm**

Quanto mais próximo de zero, melhor é a potência do sinal.

### Valores típicos

| RSSI       | Qualidade                     |
| ---------- | ----------------------------- |
| -30 dBm    | Extremamente forte            |
| -70 dBm    | Excelente                     |
| -90 dBm    | Boa                           |
| -120 dBm   | Fraca                         |
| < -130 dBm | Risco de perda de comunicação |

---

## snr

**Significado:** Signal-to-Noise Ratio

Representa a relação entre o sinal útil e o ruído presente no canal de comunicação.

Unidade: **dB**

Ao contrário de outras tecnologias sem fio, o LoRaWAN pode operar com SNR negativo.

### Valores típicos

| SNR        | Qualidade |
| ---------- | --------- |
| > 10 dB    | Excelente |
| 0 a 10 dB  | Boa       |
| -10 a 0 dB | Aceitável |
| < -20 dB   | Crítica   |

---

## frq

**Significado:** Frequency

Frequência utilizada para transmissão do pacote LoRaWAN.

### Exemplo

```text
916200000 Hz
```

No Brasil, a faixa mais utilizada situa-se próxima de **915 MHz**, conforme regulamentação da Anatel.

---

## bwd

**Significado:** Bandwidth

Largura de banda utilizada pelo rádio LoRa.

### Valores típicos

* 125 kHz
* 250 kHz
* 500 kHz

Larguras menores aumentam a sensibilidade do receptor e o alcance da comunicação.

---

## sf

**Significado:** Spreading Factor

Parâmetro responsável por controlar o alcance da comunicação, taxa de transmissão e consumo energético.

### Valores típicos

* SF7
* SF8
* SF9
* SF10
* SF11
* SF12

Valores maiores proporcionam:

* Maior alcance;
* Maior robustez;
* Melhor sensibilidade;

Porém aumentam:

* Consumo energético;
* Tempo de transmissão.

---

## cr

**Significado:** Coding Rate

Taxa de correção de erros utilizada pelo protocolo LoRa.

### Valores comuns

* 4/5
* 4/6
* 4/7
* 4/8

Taxas maiores aumentam a confiabilidade da comunicação, porém geram pacotes maiores e maior consumo de energia.

---

## air

**Significado:** Time on Air (ToA)

Tempo necessário para transmitir um pacote LoRaWAN.

Unidade: **segundos (s)**

Esse parâmetro depende de:

* Tamanho do pacote;
* Spreading Factor;
* Bandwidth;
* Coding Rate.

### Exemplo

```text
0.051456 s
```

O Time on Air influencia diretamente:

* Consumo energético;
* Capacidade da rede;
* Número máximo de dispositivos suportados.

---

## lat

**Significado:** Latitude

Coordenada geográfica de latitude do local onde o sensor está instalado.

### Exemplo

```text
-23.600108
```

Utilizada para georreferenciamento e visualização em mapas.

---

## lon

**Significado:** Longitude

Coordenada geográfica de longitude do local monitorado.

### Exemplo

```text
-46.759829
```

Em conjunto com a latitude, permite identificar precisamente o ponto de instalação do sensor.

---

## alt

**Significado:** Altitude

Altitude do local de instalação em relação ao nível médio do mar.

Unidade: **metros (m)**

### Exemplo

```text
760 m
```

Essa informação pode ser utilizada em análises hidrológicas, modelagem de drenagem urbana e integração com Sistemas de Informação Geográfica (SIG).
