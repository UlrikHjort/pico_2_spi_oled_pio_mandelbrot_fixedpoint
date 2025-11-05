cmake_minimum_required(VERSION 3.12)


set(TARGET_NAME spi_oled_pio_mandelbrot_fixedpoint)
set(PICO_BOARD pico2)
include(pico_sdk_import.cmake)
project(${TARGET_NAME})


pico_sdk_init()
add_executable(${TARGET_NAME}
  ${TARGET_NAME}.c
  )

# Fix for oscillator nominal state problem when booting after flashing
target_compile_definitions(
${TARGET_NAME} PUBLIC
PICO_XOSC_STARTUP_DELAY_MULTIPLIER=128
)
pico_generate_pio_header(${TARGET_NAME} ${CMAKE_CURRENT_LIST_DIR}/${TARGET_NAME}.pio)
target_link_libraries(${TARGET_NAME} pico_stdlib hardware_pio)
pico_add_extra_outputs(${TARGET_NAME})



