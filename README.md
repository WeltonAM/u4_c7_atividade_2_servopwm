# Atividade 2 - Unidade 4 - Capítulo 7 - Controle de Servomotor por PWM

Este projeto foi desenvolvido como parte da **Atividade 2** do curso de **EmbarcaTech TIC37 - Unidade 4**, **Capítulo 7**, consistindo na implementação de um sistema de controle de ângulo de um servomotor utilizando o módulo PWM do microcontrolador **RP2040** por meio da ferramenta **Pico SDK**. 
Além disso, usando a placa **BitDogLab**, ferramenta da formação, ver resultado no LED rgb usando a porta GPIO 12.

## Descrição

A atividade requer a configuração de um sistema para controle de posição do servomotor, utilizando a **GPIO 22** para gerar o sinal PWM. O experimento simulará o comportamento do motor no ambiente **Wokwi**.

### Componentes Utilizados

- **Microcontrolador**: Raspberry Pi Pico W.
- **Servomotor**: Motor micro servo padrão (simulado no Wokwi).
- **BitDogLab**: LED rgb GPIO 12.

### Para teste na placa BitDogLab, altere os seguintes códigos:

```c
#define PWM_PIN 12    // Pino GPIO do LEDS para teste na placa BitDogLab
// #define PWM_PIN 22       // Pino GPIO do servo
```

### 🎥 Vídeo de Demonstração

[![Assistir Vídeo](https://img.shields.io/badge/Assistir%20Vídeo-Demonstrativo-blue?style=for-the-badge&logo=youtube)](https://drive.google.com/file/d/1Tn9JLP6RqMfpO50SAAN_LrH93A7aRCu_/view?usp=sharing)

## Requisitos da Atividade

1. **Configuração da GPIO 22**: Definir a frequência do PWM para aproximadamente **50Hz** (período de 20ms).
2. **Posicionamento do servo a 180°**: Definir o ciclo ativo do PWM para **2.400µs (0,12%)**, aguardar **5 segundos**.
3. **Posicionamento do servo a 90°**: Definir o ciclo ativo do PWM para **1.470µs (0,0735%)**, aguardar **5 segundos**.
4. **Posicionamento do servo a 0°**: Definir o ciclo ativo do PWM para **500µs (0,025%)**, aguardar **5 segundos**.
5. **Movimento contínuo entre 0° e 180°**: Criar uma rotina para movimentação periódica entre os ângulos extremos, com incremento de **±5µs** e atraso de **10ms** para suavidade.
6. **Experimento com LED RGB - BitDogLab**: Testar o código usando o **LED RGB (GPIO 12)** e analisar seu comportamento.

---

### Explicação do Cálculo da Frequência do PWM

![Cálculo do Divisor do Clock](https://drive.google.com/file/d/1N8XYCjX1BpD_Bkgt_Jv2n9tdahdk5hgJ/view?usp=sharing)

### Resultado

O divisor do clock é \(100\), ou seja:

- \(d_i = 100\)
- \(d_f = 0\)

### Conclusão

Isso garante que a frequência PWM seja exatamente **50Hz**.