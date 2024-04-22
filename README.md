# AeroPy
Projeto de um drone com python o projeto é um hobby 


Passo a Passo:

# Projeto Drone de Alta Velocidade com Raspberry Pi

Este repositório contém todos os recursos necessários para construir e programar um drone de alta velocidade utilizando um Raspberry Pi como controlador de voo. O projeto é focado em entusiastas de drones e programadores que desejam explorar o uso de Python para controlar drones.

## Descrição do Projeto

O objetivo deste projeto é criar um drone de alta velocidade com capacidades de voo autônomo, usando um Raspberry Pi para integrar componentes eletrônicos como motores, ESCs, GPS e sensores. Este drone será programado usando Python, com ênfase no controle preciso e na resposta rápida.

## Componentes Necessários

- Raspberry Pi (Modelo 3B+ ou superior)
- Cartão SD com Raspberry Pi OS instalado
- Módulo GPS compatível com Raspberry Pi
- Motores brushless (4x)
- ESCs compatíveis (4x)
- Quadro de drone
- Bateria LiPo
- Hélices
- Conexões e cabos apropriados

## Configuração do Ambiente

Antes de iniciar, certifique-se de ter o ambiente Python configurado e todas as bibliotecas necessárias instaladas:

```bash
sudo apt update
sudo apt install python3 python3-pip
pip3 install RPi.GPIO pyserial
```

## Exemplo de uso de GPIO

```python
import RPi.GPIO as GPIO
import time

# Configuração do GPIO
motor_pin = 18  # Substitua pelo pino GPIO conectado ao ESC
GPIO.setmode(GPIO.BCM)
GPIO.setup(motor_pin, GPIO.OUT)

# Configuração do PWM
pwm = GPIO.PWM(motor_pin, 50)  # 50 Hz (frequência PWM)
pwm.start(0)

def set_speed(speed_percent):
    duty_cycle = (speed_percent / 100.0) * 10 + 5  # Converter porcentagem para ciclo de trabalho
    pwm.ChangeDutyCycle(duty_cycle)

# Exemplo de uso
set_speed(50)  # Configura a velocidade para 50%
time.sleep(10)
set_speed(0)
pwm.stop()
GPIO.cleanup()
```


## Estrutura do Repositório
<b>src/</b>: Contém todos os scripts Python para controlar o drone.<br>
<b>docs/</b>: Documentação adicional e esquemas.<br>
<b>tests/</b>: Scripts de teste para diferentes componentes do drone.<br>

## Instruções de Uso
<ul>
<li><b>Montagem do Hardware:</b> Siga o esquema no diretório <b>docs/</b> para montar o drone.</li>
<li><b>Configuração de Software:</b> Carregue os scripts de <b>src/</b> para o Raspberry Pi.</li>
<li><b>Testes Iniciais:</b> Execute os testes de <b>tests/</b> para garantir que todos os componentes estão funcionando corretamente.</li>
<li><b>Calibração:</b> Calibre os sensores e motores usando os scripts fornecidos.</li>
<li><b>Voos de Teste:</b> Inicie com voos de baixa velocidade e aumente progressivamente à medida que o sistema for calibrado.</li>
</ul>

## Segurança
<ul>
<li>Realize todos os testes em uma área aberta e segura.</li>
<li>Verifique a legislação local sobre o uso de drones.</li>
<li>Monitore constantemente a condição da bateria e dos motores durante os testes.</li>
</ul>

## Contribuições
Contribuições são bem-vindas! Se você tem melhorias ou correções, por favor, faça um fork do repositório e submeta um pull request.

## Licença
Este projeto é distribuído sob a licença MIT. Veja o arquivo <b>LICENSE</b> para mais detalhes.