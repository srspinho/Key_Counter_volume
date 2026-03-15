# RP2040 HID Remapper & System Monitor ⌨️📺

Este projeto transforma um **Raspberry Pi Pico (RP2040)** em um remapeador de teclado USB inteligente e monitor de sistema. Ele atua como um "man-in-the-middle", interceptando comandos de um teclado físico e remapeando teclas específicas enquanto exibe estatísticas em tempo real em um display OLED.

## 🚀 Funcionalidades

- **Remapeamento de Teclas:** Converte a combinação `AltGr + R` para a tecla `\` (barra invertida), facilitando o uso de teclados internacionais no padrão ABNT2.
- **Contador de Teclas:** Um "odômetro" de digitação que conta quantos pressionamentos de tecla foram realizados.
- **Monitor de Volume:** Exibe uma barra de volume visual e arredondada que responde aos comandos do Rotary Encoder do teclado.
- **Dual-Core Processing:** - **Core 0:** Gerencia a pilha USB Device (comunicação com o PC).
  - **Core 1:** Gerencia o USB Host (leitura do teclado) e a atualização do Display OLED.
- **Filtro de Estabilidade:** Implementação de *debounce* de software para evitar disparos acidentais no controle de volume.

## 🛠️ Hardware Necessário

- **Microcontrolador:** Raspberry Pi Pico (ou qualquer placa RP2040).
- **Display:** OLED SSD1306 128x64 (I2C).
- **Conexão USB:** Cabo OTG ou adaptador para conectar o teclado físico ao Pico via PIO-USB.

## 📁 Estrutura de Conexão (Pinout)

| Componente | Pino Pico (GPIO) |
|------------|------------------|
| OLED SDA   | GPIO 4           |
| OLED SCL   | GPIO 5           |
| USB Host D+| GPIO 16 (ou conforme config) |
| USB Host D-| GPIO 17 (ou conforme config) |

## 💻 Bibliotecas Utilizadas

- [U8g2](https://github.com/olikraus/u8g2) - Para renderização dos gráficos no OLED.
- [Adafruit_TinyUSB](https://github.com/adafruit/Adafruit_TinyUSB_Arduino) - Para as funções de USB Host e Device.
- [Pico-PIO-USB](https://github.com/sekigon-gonnoc/Pico-PIO-USB) - Para habilitar USB Host via hardware PIO.

## 📝 Como usar

1. Configure o ambiente Arduino para o Raspberry Pi Pico.
2. Certifique-se de que a velocidade da CPU está em **120MHz** ou **240MHz** (necessário para USB Host).
3. Instale as bibliotecas listadas acima.
4. Carregue o código e conecte seu teclado na porta USB Host.

<p align="center">
  <img src="[Key Count + Volume bar](https://github.com/srspinho/Key_Counter_volume/blob/main/IMG_20260313_152114.jpg)" width="400">
</p>

---
Desenvolvido com a ajuda do Gemini AI. 🚀
