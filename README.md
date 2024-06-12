# Traethlin documentation

This package is to document the various aspects of the Traethlin robot, from its construction to its use and possible developments.

Traethlin (*shoreline* in Welsh) is a robot initially designed to survey the elevation of coastal areas of Wales, in collaboration with the [Wales Coastal Monitoring Centre](https://www.wcmc.wales/_files/ugd/d0d240_1d66067560554c429da7188d70d49375.pdf).  The aim was to produce a design that could be implementd with little effort and only reasonable technical know-how.

There are other uses planned.

![A picture of Traethlin](images/traethlin.jpg "Traethlin")

You will find documentation for:

- [hardware](#hardware)
- software
- usage

## Traethlin's hardware {#hardware}

The robot is based on a RC rock crawler chassis, the [Traxxas trx-4](https://traxxas.com/products/landing/trx-4/).

The main computer is a [Raspberry Pi 4 model b](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) running Ubuntu (currently 22.04).  All the high-level processing happens on the RPi, in particular using the [Robotic Operating System](https://ros.org/) (ROS, currently *humble*).  More on this can be found [here](#software).

To interface with some of the hardware, an ESP32 running micro-ROS is used.

## Traethlin's software {#software}
