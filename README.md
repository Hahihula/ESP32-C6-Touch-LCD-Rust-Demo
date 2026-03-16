# ESP32-C6 Touch LCD Rust Demo

A `no_std` Rust demo for the Waveshare ESP32-C6-Touch-LCD-1.47 module.

## Hardware

- **Board**: ESP32-C6-Touch-LCD-1.47 (Waveshare)
- **Display**: 172x320 RGB565 TFT LCD (JD9853 controller)
- **Touch**: AXS5106L capacitive touch controller (I2C)
- **IMU**: QMI8658 6-axis sensor (accelerometer + gyroscope)
- **MCU**: ESP32-C6 (RISC-V, 160 MHz, 512 KB RAM, 8 MB Flash)

## Features

- SPI LCD display with RGB565 color format
- Touch input detection with visual feedback (red circles at touch points)
- IMU sensor readings (accelerometer + gyroscope)
- Built-in temperature sensor
- Button navigation between demo pages:
  - **Page 0**: Touch demo - draw circles where you touch
  - **Page 1**: IMU demo - display accelerometer/gyroscope X, Y, Z values
  - **Page 2**: System info - chip info and temperature

## Pin Configuration

| Function | GPIO |
|----------|------|
| SPI SCK | 1 |
| SPI MOSI | 2 |
| SPI CS | 14 |
| LCD DC | 15 |
| LCD RST | 22 |
| LCD Backlight | 23 |
| I2C SDA | 18 |
| I2C SCL | 19 |
| Touch RST | 20 |
| Touch INT | 21 |
| Button | 9 |

## Requirements

- Rust toolchain with `rustup target add riscv32imc-unknown-none-elf`
- `espflash` CLI: `cargo install espflash`
- ESP32-C6 flashed with bootloader (see [ESP Rust Book](https://docs.espressif.com/projects/rust/book/))

## Build & Flash

```bash
# Build and flash
cargo espflash flash --release

# Open serial monitor
cargo espflash monitor
```

Press the button (GPIO9) to cycle through demo pages.

## Dependencies

- `esp-hal` 1.0.0-rc.0
- `embassy-executor` for async runtime
- `embedded-graphics` for 2D graphics
- `mipidsi` for display driver
- `axs5106l` for touch controller
- `ph-qmi8658` for IMU sensor

## License

MIT
