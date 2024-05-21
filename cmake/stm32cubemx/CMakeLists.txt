cmake_minimum_required(VERSION 3.22)

project(stm32cubemx)
add_library(stm32cubemx INTERFACE)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

target_compile_definitions(stm32cubemx INTERFACE 
	USE_HAL_DRIVER 
	STM32F407xx
    $<$<CONFIG:Debug>:DEBUG>
)

target_include_directories(stm32cubemx INTERFACE
    ../../RT-Thread
    ../../Core/Inc
    ../../Drivers/STM32F4xx_HAL_Driver/Inc
    ../../Drivers/STM32F4xx_HAL_Driver/Inc/Legacy
    ../../Drivers/CMSIS/Device/ST/STM32F4xx/Include
    ../../Drivers/CMSIS/Include
    ../../Middlewares/Third_Party/RealThread_RTOS/include/
    ../../Middlewares/Third_Party/RealThread_RTOS/bsp/_template/cubemx_config
    ../../Middlewares/Third_Party/RealThread_RTOS/finsh/
    ../../Middlewares/Third_Party/RealThread_RTOS/components/finsh
)

target_sources(stm32cubemx INTERFACE
    ../../Core/Src/main.c
    ../../Core/Src/stm32f4xx_it.c
    ../../Core/Src/stm32f4xx_hal_msp.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_rcc.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_rcc_ex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash_ex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_flash_ramfunc.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_gpio.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_dma_ex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_dma.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_pwr.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_pwr_ex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_cortex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_exti.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_tim.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_tim_ex.c
    ../../Drivers/STM32F4xx_HAL_Driver/Src/stm32f4xx_hal_uart.c
    ../../Core/Src/system_stm32f4xx.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/clock.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/components.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/cpu.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/idle.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/ipc.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/irq.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/kservice.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/mem.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/memheap.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/mempool.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/object.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/scheduler.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/slab.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/thread.c
    ../../Middlewares/Third_Party/RealThread_RTOS/src/timer.c
    ../../Middlewares/Third_Party/RealThread_RTOS/libcpu/arm/cortex-m4/cpuport.c
    ../../Middlewares/Third_Party/RealThread_RTOS/bsp/_template/cubemx_config/board.c
    ../../Middlewares/Third_Party/RealThread_RTOS/components/finsh/cmd.c
    ../../Middlewares/Third_Party/RealThread_RTOS/components/finsh/finsh_port.c
    ../../Middlewares/Third_Party/RealThread_RTOS/components/finsh/msh.c
    ../../Middlewares/Third_Party/RealThread_RTOS/components/finsh/shell.c
    ../../Middlewares/Third_Party/RealThread_RTOS/components/device/device.c
    ../../Core/Src/sysmem.c
    ../../Core/Src/syscalls.c
    ../../startup_stm32f407xx.s
    ../../Middlewares/Third_Party/RealThread_RTOS/libcpu/arm/cortex-m4/context_gcc.S
)

target_link_directories(stm32cubemx INTERFACE
)

target_link_libraries(stm32cubemx INTERFACE
)

# Validate that STM32CubeMX code is compatible with C standard
if(CMAKE_C_STANDARD LESS 11)
    message(ERROR "Generated code requires C11 or higher")
endif()


