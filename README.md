# Traethlin documentation

This package is to document the various aspects of the Traethlin robot, from its construction to its use and possible developments.

Traethlin (*shoreline* in Welsh) is a robot initially designed to survey the elevation of coastal areas of Wales, in collaboration with the [Wales Coastal Monitoring Centre](https://www.wcmc.wales/_files/ugd/d0d240_1d66067560554c429da7188d70d49375.pdf).  The aim was to produce a design that could be implementd with little effort and only reasonable technical know-how.

There are other uses planned.

![A picture of Traethlin](images/traethlin.jpg "Traethlin")

You will find documentation for:

- [hardware](#traethlins-hardware)
- [software](#traethlins-software)
- usage

## Traethlin's hardware

### Chassis

The robot is based on a RC rock crawler chassis, the [Traxxas trx-4](https://traxxas.com/products/landing/trx-4/).

### Computing

The main computer is a [Raspberry Pi 4 model b](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) running Ubuntu (currently 22.04).  All the high-level processing happens on the RPi, in particular using the [Robotic Operating System](https://ros.org/) (ROS, currently *humble*).  More on this can be found [here](#traethlins-software).

An ESP32 is used to interface with some of the hardware.  Specifically, a [DevKitC](https://www.espressif.com/en/products/devkits/esp32-devkitc/overview) is used for the ESP32 for its convenience of use.  This runs [micro-ROS](https://micro.ros.org/).

### GNSS

Positioning is obtained from an [Emlid Reach module](https://emlid.com/reach/).  This provides RTK differential GNSS as long as it has access to a Emlid base station (using a LoRa [adapter](https://hk.store.emlid.com/products/reach-m-lora-radio?variant=44249818824943)) or [NTRIP correction signals](#ntrip).  Other GNSS solutions exist.

### Cameras

3D and thermal

### IMU

### Batteries

### Schematics

### Instructions

## Traethlin's software

### ROS

### Micro-ROS

### NTRIP
