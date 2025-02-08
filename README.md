# Atividade - Controle de Servomotor por PWM

Esta atividade consiste na implementação de um sistema de controle de ângulo de um servomotor utilizando o módulo PWM do microcontrolador **RP2040** por meio da ferramenta **Pico SDK**. A simulação será realizada no **Wokwi**, empregando um **motor micro servo padrão**.

## Descrição

A atividade requer a configuração de um sistema para controle de posição do servomotor, utilizando a **GPIO 22** para gerar o sinal PWM. O experimento simulará o comportamento do motor no ambiente **Wokwi**.

### Componentes Utilizados

- **Microcontrolador**: Raspberry Pi Pico W.
- **Servomotor**: Motor micro servo padrão (simulado no Wokwi).

> **Observação**: Não será necessária a implementação de um circuito de interface entre o Raspberry Pi Pico W e o servomotor, pois a prática será realizada apenas com componentes simulados.

### 📌 Simulação no Wokwi

[![Abrir Simulação no Wokwi](https://img.shields.io/badge/Simular%20no-Wokwi-green?style=for-the-badge&logo=raspberrypi)](https://wokwi.com/projects/your_project_link_here)

### 🎥 Vídeo de Demonstração

[![Assistir Vídeo](https://img.shields.io/badge/Assistir%20Vídeo-Demonstrativo-blue?style=for-the-badge&logo=youtube)](https://www.dropbox.com/scl/fi/i32f4t9dqggn4c1durb4o/2025-02-04-08-52-05.mkv?rlkey=s6ofq9yumuts3h8chte052cuj&dl=0)

## Requisitos da Atividade

1. **Configuração da GPIO 22**: Definir a frequência do PWM para aproximadamente **50Hz** (período de 20ms). **(20% da nota)**
2. **Posicionamento do servo a 180°**: Definir o ciclo ativo do PWM para **2.400µs (0,12%)**, aguardar **5 segundos**. **(10% da nota)**
3. **Posicionamento do servo a 90°**: Definir o ciclo ativo do PWM para **1.470µs (0,0735%)**, aguardar **5 segundos**. **(10% da nota)**
4. **Posicionamento do servo a 0°**: Definir o ciclo ativo do PWM para **500µs (0,025%)**, aguardar **5 segundos**. **(10% da nota)**
5. **Movimento contínuo entre 0° e 180°**: Criar uma rotina para movimentação periódica entre os ângulos extremos, com incremento de **±5µs** e atraso de **10ms** para suavidade. **(35% da nota)**
6. **Experimento com LED RGB - BitDogLab**: Testar o código usando o **LED RGB (GPIO 12)** e analisar seu comportamento. **(15% da nota)**

---

## Explicação do Cálculo da Frequência do PWM

A frequência do PWM (
\( f_{PWM} \)
) é calculada com base na seguinte equação:

\[
f_{PWM} = \frac{f_{clock}}{(d_i + \frac{d_f}{16}) \times (wrap + 1)}
\]

Onde:

- **\( f_{clock} \)**: Frequência do clock principal (125 MHz para o RP2040).
- **\( d_i \)**: Parte inteira do divisor do clock.
- **\( d_f \)**: Parte fracionária do divisor do clock.
- **\( wrap \)**: Valor máximo do contador PWM.

### Cálculo do divisor do clock:

Sabemos que:

- \( f_{clock} = 125 \times 10^6 \) Hz
- \( f_{PWM} = 50 \) Hz
- \( wrap = 25000 \)

Reorganizando a equação:

\[
d_i + \frac{d_f}{16} = \frac{125000000}{50 \times (25000 + 1)}
\]

Calculamos o denominador:

\[
50 \times (25000 + 1) = 1250000
\]

Agora, o quociente:

\[
d_i + \frac{d_f}{16} = \frac{125000000}{1250000} = 100
\]

Portanto, o **divisor do clock é 100**, ou seja:

- **\( d_i = 100 \)**
- **\( d_f = 0 \)**

Isso garante uma frequência PWM precisa de **50Hz**.

