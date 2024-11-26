# STM32 USB Device Composite Class based on the STM32H503

Change for PB_MCU01_H503A board

In this repository : 

* This application provides a C code example showing on how to use the legacy USB Middleware to develop a USB Device Composite application, based on the article published here> https://community.st.com/t5/stm32-mcus/how-to-implement-a-usb-device-composite-in-stm32h5/ta-p/691123
* The application is designed to open a Virtual COM Port and control a Mouse through the CDC and HID Classes. The main purpose of the application is to provide a functional example for opening more than a class in a single USB Application.
* The application runs over the NUCLEO-H503RB board, and can be tailored/used as example to any other STM32 Family. 
* The repositor contains a project for STM32CubeIDE v1.15.1 for the STM32H503RB.

### <b>Application</b>

   At the beginning of the application, the USB Stack is started and the HID and CDC classes are registered. Following that, the USB Device peripheral in Full-Speed mode is started.
   Once all this process is done, the application monitors the GPIO PC13, which has a user button connected. While the board blue button is pressed a message and a report are sent through the CDC Class and an HID.
   The CDC message can be saw through a Virtual COM Port terminal, and the HID report makes the cursor to move 100 points to the right.

### <b>Keywords</b>

ADC, analog digital converter, analog, conversion, voltage, channel, analog input, interruption

### <b>Directory contents</b>

   Here are the list of the most relevant files for the application. The other files are Read Only or were not modified to build the application.

  - Core/Src/main.c                                            -> Commom peripheral initialization functions, HID and CDC functions
  - Core/Inc/main.h                                            -> Exported function prototypes and includes
  - USB/Class/CDC/Inc/usbd_cdc.h                               -> CDC EP addresses and Settings
  - USB/Class/CDC/Inc/usbd_cdc_if.h                            -> CDC Interface header file with the strutct of pointers o function to handle the CDC Communication
  - USB/Class/CDC/Src/usbd_cdc.c                               -> CDC Function drivers to handle the data flow through the HID Endpoint
  - USB/Class/CDC/Src/usbd_cdc_if.c                            -> CDC Interface functions to handle the CDC Communication
  - USB/Class/CompositeBuilder/Inc/usbd_composite_builder.h    -> Composite builder header file to share the resource references for the USB application to build the composite descriptor
  - USB/Class/CompositeBuilder/Src/usbd_composite_builder.c    -> Contains the functions to build the composite descriptor to be transmitted through USB during enumeration phase
  - USB/Class/HID/Inc/usbd_hid.h                               -> HID EP adresses and Settings
  - USB/Class/HID/Src/usbd_hid.c                               -> HID Function drivers to handle the data flow through the HID Endpoint
  - USB/Core/Inc/usbd_conf.h                                   -> Include the STM32 Familly HAL drivers and defines to configure the USB Stack Application
  - USB/Core/Src/usbd_conf.c                                   -> Implementation of interrupts and callbacks for the USB Peripheral
  - USB/Core/Src/usbd_desc.c                                   -> Definition of VID, PID, and Descriptor Strings 


### <b>Hardware and Software environment</b>

  - This example runs on STM32H503RBTx devices.

  - This example has been tested with NUCLEO-H503RB board and can be
    easily tailored to any other supported device and development board.

### <b>How to use it ?</b>

In order to make the program work, you must do the following :

 - Open and import the project into STM32CubeIDE v1.15.1 or newer
 - Rebuild all files and load your image into target memory
 - Run the example
