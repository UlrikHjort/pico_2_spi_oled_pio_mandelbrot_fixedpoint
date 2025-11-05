Raspberry PICO2 RISC-V (Pico Platform (PICO_PLATFORM) is 'rp2350-riscv') spi pio statemachine for
128x64 OLED drawing a 8.24 fixed point Mandelbrot set.


8.24 Fixed point fomulars used to convert doubles to fixed points in the Mandelbrot set function:

#define DECIMAL_PRECISION 24

#define DOUBLE_TO_FIXED(d) ((int32_t) (d * (double) (1 << DECIMAL_PRECISION) + (d >= 0.0 ? 0.5 : -0.5)))

#define FIXED_TO_DOUBLE(f) ((double) f / (double) (1 << DECIMAL_PRECISION))

#define INT_TO_FIXED(i) ((int32_t) i << DECIMAL_PRECISION)


Usage:
Build: mkdir build; cd build; cmake ..; make

cp spi_oled_pio_mandelbrot_fixedpoint.uf2 <MOUNTPOINT>/RP2350/