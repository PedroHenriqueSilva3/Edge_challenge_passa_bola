Video do youtube: https://youtu.be/mYxGTfYziNE
Link do projeto no wokwi: https://wokwi.com/projects/442307023172067329


Monitoramento de Atleta com IoT – ESP32 + MPU6050 + Sensor de Pulso/Oxigenação
👥 Integrantes

Gabriel Carvalho Simões da Silva RM563169
João Gabriel C. M. Santos RM563953
Leonardo Vinicius de Souza RM562299
Pedro Henrique da Silva RM566235

📋 Descrição do Projeto

Este projeto tem como objetivo monitorar parâmetros vitais e físicos de um atleta em tempo real utilizando um microcontrolador ESP32.
Os dados coletados incluem:

Batimentos cardíacos (BPM)

Nível de oxigenação no sangue (SpO₂ simulado)

Velocidade média e máxima

Distância percorrida

Temperatura corporal da atleta

As informações são processadas no ESP32 e enviadas automaticamente para a plataforma ThingSpeak via HTTP, permitindo visualização e análise online.

🏗️ Arquitetura Proposta
Diagrama
graph LR
A[Sensores - Pulso / Oxigenação] -->|Analógico| B[ESP32]
C[MPU6050 - Acelerômetro/Giroscópio] -->|I2C| B
B -->|Wi-Fi HTTP| D[Plataforma ThingSpeak]
D -->|Dashboard| E[Usuário/Aplicação Web]

Explicação

Sensores de Pulso e Oxigenação: conectados às entradas analógicas do ESP32 para ler valores simulados de BPM e SpO₂.

MPU6050: envia dados de aceleração para cálculo da velocidade e distância percorrida.

ESP32: conecta-se à rede Wi-Fi, processa os dados dos sensores, faz cálculos e envia as informações via HTTP.

ThingSpeak: recebe os dados e exibe em gráficos online.

Usuário: acessa o dashboard para acompanhar métricas do atleta em tempo real.

🛠️ Recursos Necessários
Hardware

ESP32 (modelo com Wi-Fi)

Sensor MPU6050 (Acelerômetro + Giroscópio)

Sensor de Pulso (analógico)

Sensor de Oxigenação (analógico – simulado)

Jumpers / Protoboard

Software / Plataformas

Arduino IDE ou PlatformIO (para programar o ESP32)

Bibliotecas:

Adafruit_MPU6050

Adafruit_Sensor

Wire

WiFi

HTTPClient

Conta no ThingSpeak
 e chave API configurada

🚀 Instruções de Uso

Montagem do Hardware:

Conecte o MPU6050 ao ESP32 via I2C (SDA e SCL).

Conecte os sensores analógicos de pulso e oxigenação às portas GPIO 34 e 32.

Configuração do Software:

Instale as bibliotecas no Arduino IDE.

Insira suas credenciais Wi-Fi e API Key do ThingSpeak no código.

Upload do Código:

Selecione a placa ESP32 correta no Arduino IDE.

Faça upload do código para o ESP32.

Visualização:

Abra o Serial Monitor para ver os dados locais.

Acesse o canal do ThingSpeak para visualizar gráficos online.


📈 Métricas Enviadas para o ThingSpeak
Campo	Métrica
field1	BPM
field2	Oxigenação
field3	Velocidade (km/h)
field4	Distância (m)
field5	Temperatura (°C)
field6	Velocidade Máxima (km/h)
📝 Observações

O projeto usa valores analógicos para simular pulso e oxigenação; sensores reais podem ser conectados.

O intervalo de envio para o ThingSpeak está configurado para 15 segundos (delay(15000)).
