# Simple Camera Capture with Arduino

## Project Goal
This project is an automated system to take pictures using a cheap camera module (**OV7670**) controlled by an **Arduino Uno**, and then automatically save those pictures to your computer.

The main aim was to build a system that can take a picture on command and quickly send the raw image data to a PC for saving.

***

## How the System Works

The system has two main parts: the **Arduino** (the brain) and the **PC** (the storage).

### 1. The Camera and Arduino (The Brain)
The Arduino is responsible for three main tasks:

* **Setup:** It tells the camera which settings to use, like the color format (YUV422) and the image size (**QVGA: $320 \times 240$ pixels**). This setup is done using a two-wire digital language called **I2C**.
* **Trigger:** The system is set up to wait for a signal (a **HIGH** voltage) on Pin 13 before it starts taking a picture.
* **Capture & Send:** When triggered, the Arduino quickly reads the image data, which comes out of the camera on 8 parallel data pins. It then immediately sends this data to the computer using a very fast serial connection (**1 Mbps**).

### 2. The Computer (The Storage)
The computer uses a separate program (written in **Java**) to handle the image data:

* It opens the fast serial connection.
* It listens for the stream of raw pixel data coming from the Arduino.
* It takes all the incoming bytes and saves them into a file on your hard drive.

***

## Key Components

* **Microcontroller:** Arduino Uno
* **Camera Module:** OV7670
* **Control Code:** Custom C/C++ code on the Arduino.
* **PC Program:** Java application to receive and save the images.

The whole process demonstrates how a small microcontroller can manage a complex camera sensor and stream large amounts of data to a host computer efficiently.
