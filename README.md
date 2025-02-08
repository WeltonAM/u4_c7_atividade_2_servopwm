# Atividade 2 - Unidade 4 - Capítulo 7 - Controle de Servomotor por PWM

Este projeto foi desenvolvido como parte da **Atividade 2** do curso de **EmbarcaTech TIC37 - Unidade 4**, **Capítulo 7**, consistindo na implementação de um sistema de controle de ângulo de um servomotor utilizando o módulo PWM do microcontrolador **RP2040** por meio da ferramenta **Pico SDK**. 
Além disso, usando a placa **BitDogLab**, ferramenta da formação, ver resultado no LED rgb usando a porta GPIO 12.

## Descrição

A atividade requer a configuração de um sistema para controle de posição do servomotor, utilizando a **GPIO 22** para gerar o sinal PWM. O experimento simulará o comportamento do motor no ambiente **Wokwi**.

### Componentes Utilizados

- **Microcontrolador**: Raspberry Pi Pico W.
- **Servomotor**: Motor micro servo padrão (simulado no Wokwi).
- **BitDogLab**: LED rgb GPIO 12.

### 🎥 Vídeo de Demonstração

[![Assistir Vídeo](https://img.shields.io/badge/Assistir%20Vídeo-Demonstrativo-blue?style=for-the-badge&logo=youtube)](https://www.dropbox.com/scl/fi/i32f4t9dqggn4c1durb4o/2025-02-04-08-52-05.mkv?rlkey=s6ofq9yumuts3h8chte052cuj&dl=0)

## Requisitos da Atividade

1. **Configuração da GPIO 22**: Definir a frequência do PWM para aproximadamente **50Hz** (período de 20ms).
2. **Posicionamento do servo a 180°**: Definir o ciclo ativo do PWM para **2.400µs (0,12%)**, aguardar **5 segundos**.
3. **Posicionamento do servo a 90°**: Definir o ciclo ativo do PWM para **1.470µs (0,0735%)**, aguardar **5 segundos**.
4. **Posicionamento do servo a 0°**: Definir o ciclo ativo do PWM para **500µs (0,025%)**, aguardar **5 segundos**.
5. **Movimento contínuo entre 0° e 180°**: Criar uma rotina para movimentação periódica entre os ângulos extremos, com incremento de **±5µs** e atraso de **10ms** para suavidade.
6. **Experimento com LED RGB - BitDogLab**: Testar o código usando o **LED RGB (GPIO 12)** e analisar seu comportamento.

---

## Explicação do Cálculo da Frequência do PWM

A frequência do PWM (\(f_{PWM}\)) é determinada pela fórmula:

\[
f_{PWM} = \frac{f_{clock}}{(d_i + \frac{d_f}{16}) \times (wrap + 1)}
\]

### Variáveis

- \(f_{clock} = 125 \times 10^6\) Hz (frequência do clock principal do RP2040).
- \(f_{PWM} = 50\) Hz.
- \(wrap = 25000\).

### Passo a Passo do Cálculo

1. Reorganizamos a fórmula para encontrar \(d_i + \frac{d_f}{16}\):

   \[
   d_i + \frac{d_f}{16} = \frac{f_{clock}}{f_{PWM} \times (wrap + 1)}
   \]

2. Substituímos os valores:

   \[
   d_i + \frac{d_f}{16} = \frac{125000000}{50 \times (25000 + 1)}
   \]

3. Calculamos o denominador:

   \[
   50 \times (25000 + 1) = 1250000
   \]

4. Agora, dividimos:

   \[
   d_i + \frac{d_f}{16} = \frac{125000000}{1250000} = 100
   \]

### Resultado

O divisor do clock é \(100\), ou seja:

- \(d_i = 100\)
- \(d_f = 0\)

### Conclusão

Isso garante que a frequência PWM seja exatamente **50Hz**.