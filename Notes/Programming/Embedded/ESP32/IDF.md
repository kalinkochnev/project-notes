# Setup
*Sets* up the build environment/dev framework
- I installed the repository under `~/Applications/esp32/`
```
git clone --recursive https://github.com/espressif/esp-idf
```

Run `./install.sh` (installs pip and apt repositories necessary)
Add the scripts to the current environment `. ./export.sh`. This adds the main script `idf.py` to the environment. 

**Create project**
`idf.py create-project <project-name>`

**Build project**
`idf.py build`


## menuconfig
Can configure aspects of the esp32 for the build process. A `.projbuild` variable substitution can be made if CONFIG_ is prepended to the variable of the same name in `.projbuild`
```c
#define MY_CONST CONFIG_<NAME HERE>
```

## monitor
You can exit the monitor by hitting `Ctrl+]`


# Components
## Build system resources
https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-guides/build-system.html?highlight=components#including-components-in-the-build

## Creating component

Components are basically libraries you can import into your project. There is an online repository or you can create a component locally.

```
idf.py create-component <component-name>
```

Pay attention to the CMakeLists which makes use of a custom command to register the component

```CMake
idf_component_register(SRCS "my_component.c" INCLUDE_DIRS "include")
```

[Signature of idf_component_register](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-guides/build-system.html#cmake-component-register)

## Drivers and components
In order to use a driver, such as UART or GPIO, you need to include it privately in CmakeLists.

ex: To enable 
```c
#include "driver/uart.h"
#include "driver/gpio.h"
```

Modify the `idf_component_register` to 
```CMake
idf_component_register(
	SRCS ${SOURCES} 
	INCLUDE_DIRS "include"
	PRIV_REQUIRES "esp_driver_uart" "esp_driver_gpio"
)
```