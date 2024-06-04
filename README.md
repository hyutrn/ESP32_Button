# ESP32_Button
This project demonstrates a multi-threaded approach using ESP-IDF v4.4.7 on an ESP32 to manage WiFi connectivity and handle button presses. The program uses FreeRTOS tasks to separate WiFi handling and button state management, utilizing a shared memory space protected by a semaphore for safe access.
