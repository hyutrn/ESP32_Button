# ESP32 Multi-threaded WiFi and Button Handling

This project demonstrates a multi-threaded approach using ESP-IDF v4.4.7 on an ESP32 to manage WiFi connectivity and handle button presses. The program uses FreeRTOS tasks to separate WiFi handling and button state management, utilizing a shared memory space protected by a semaphore for safe access.

## Features

- **Multi-threading**: Two FreeRTOS tasks are used - one for handling WiFi functions and another for managing button states.
- **WiFi Management**: The program can scan for WiFi networks, switch between AP and STA modes, and disconnect from WiFi based on button inputs.
- **Button Handling**: Four buttons are used to control the WiFi functions:
  - Button 1: Scan for WiFi networks
  - Button 2: Switch to AP mode
  - Button 3: Switch to STA mode
  - Button 4: Disconnect from WiFi
- **Semaphore Protection**: A semaphore is used to ensure safe access to the shared memory where button states are stored.

## Directory Structure

- ├── main
- │   ├── button.c
- │   ├── button.h
- │   ├── main.c
- │   ├── wifi.c
- │   ├── wifi.h
- ├── CMakeLists.txt
- └── sdkconfig

## Getting Started

### Prerequisites

- ESP-IDF v4.4.7
- An ESP32 development board
- Four push buttons connected to GPIO pins

### Installation

1. **Clone the repository**:

    ```sh
    git clone https://github.com/hyutrn/ESP32_Button.git
    cd esp32_button
    ```

2. **Set up ESP-IDF environment**:

    Follow the instructions from the [ESP-IDF documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html) to set up the ESP-IDF environment.

3. **Configure the project**:

    ```sh
    idf.py menuconfig
    ```

4. **Build and flash the project**:

    ```sh
    idf.py build
    idf.py flash
    ```

5. **Monitor the output**:

    ```sh
    idf.py monitor
    ```

## Code Overview

### main.c

The main file initializes the semaphore and creates two FreeRTOS tasks: `wifi_task` and `button_task`. It also sets up the GPIO configuration for the buttons.

### wifi.c and wifi.h

These files contain functions for WiFi management, including scanning for networks, switching modes, and disconnecting.

### button.c and button.h

These files handle the state of the buttons, updating the shared memory that the `wifi_task` uses to determine which action to take.

## GPIO Configuration

Make sure to connect your buttons to the appropriate GPIO pins defined in `button.c`:

```c
#define BUTTON1_GPIO 0
#define BUTTON2_GPIO 2
#define BUTTON3_GPIO 4
#define BUTTON4_GPIO 5
```

## Contributing
Contributions are welcome! Please open an issue or submit a pull request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.



