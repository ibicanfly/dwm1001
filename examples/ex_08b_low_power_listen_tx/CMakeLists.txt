cmake_minimum_required(VERSION 3.13.1)

set(BOARD_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/../..")
set(DTS_ROOT   "${CMAKE_CURRENT_SOURCE_DIR}/../..")
set(BOARD nrf52_dwm1001)

include($ENV{ZEPHYR_BASE}/cmake/app/boilerplate.cmake NO_POLICY_SCOPE)
project(zephyr-dwm1001)

add_definitions(-DEX_08B_DEF)

target_sources(app PRIVATE ../../main.c)
target_sources(app PRIVATE ex_08b_main.c)

target_sources(app PRIVATE ../../decadriver/deca_device.c)
target_sources(app PRIVATE ../../decadriver/deca_params_init.c)

target_sources(app PRIVATE ../../platform/port.c)
target_sources(app PRIVATE ../../platform/deca_mutex.c)
target_sources(app PRIVATE ../../platform/deca_range_tables.c)
target_sources(app PRIVATE ../../platform/deca_sleep.c)
target_sources(app PRIVATE ../../platform/deca_spi.c)
target_sources(app PRIVATE ../../platform/port.c)


target_include_directories(app PRIVATE ../../decadriver/)
target_include_directories(app PRIVATE ../../platform/)
target_include_directories(app PRIVATE ../../compiler/)
