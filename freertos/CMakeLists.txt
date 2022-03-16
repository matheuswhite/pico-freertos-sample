#set(PICO_SDK_FREERTOS_SOURCE ${PICO_SDK_PATH}/lib/tinyusb/lib/FreeRTOS/FreeRTOS/Source/)
set(PICO_SDK_FREERTOS_SOURCE FreeRTOS-Kernel)
set(SYSTEM_VIEW_SOURCE ../system_view)

add_library(freertos
    ${PICO_SDK_FREERTOS_SOURCE}/event_groups.c
    ${PICO_SDK_FREERTOS_SOURCE}/list.c
    ${PICO_SDK_FREERTOS_SOURCE}/queue.c
    ${PICO_SDK_FREERTOS_SOURCE}/stream_buffer.c
    ${PICO_SDK_FREERTOS_SOURCE}/tasks.c
    ${PICO_SDK_FREERTOS_SOURCE}/timers.c
    ${PICO_SDK_FREERTOS_SOURCE}/portable/MemMang/heap_3.c
#    ${PICO_SDK_FREERTOS_SOURCE}/portable/GCC/ARM_CM0/port.c
    port.c
    ${SYSTEM_VIEW_SOURCE}/Sample/FreeRTOS/Config/SEGGER_SYSVIEW_Config_FreeRTOS.c
    ${SYSTEM_VIEW_SOURCE}/Sample/FreeRTOS/SEGGER_SYSVIEW_FreeRTOS.c
    ${SYSTEM_VIEW_SOURCE}/SEGGER/SEGGER_RTT.c
    ${SYSTEM_VIEW_SOURCE}/SEGGER/SEGGER_SYSVIEW.c
)

target_include_directories(freertos PUBLIC
    .
    ${PICO_SDK_FREERTOS_SOURCE}/include
    ${PICO_SDK_FREERTOS_SOURCE}/portable/GCC/ARM_CM0
    ${SYSTEM_VIEW_SOURCE}/SEGGER
    ${SYSTEM_VIEW_SOURCE}/Sample/FreeRTOS/Config
    ${SYSTEM_VIEW_SOURCE}/Sample/FreeRTOS/
    ${SYSTEM_VIEW_SOURCE}/Config
)
