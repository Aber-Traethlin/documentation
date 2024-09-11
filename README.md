# Traethlin documentation

This package is to document the various aspects of the Traethlin robot, from its construction to its use and possible developments.

Traethlin (*shoreline* in Welsh) is a robot initially designed to survey the elevation of coastal areas of Wales, in collaboration with the [Wales Coastal Monitoring Centre](https://www.wcmc.wales/_files/ugd/d0d240_1d66067560554c429da7188d70d49375.pdf).  The aim was to produce a design that could be implementd with little effort and only reasonable technical know-how.

There are other uses planned.

![A picture of Traethlin](images/traethlin.jpg "Traethlin")

You will find documentation for:

- [hardware](#traethlins-hardware)
- [software](#traethlins-software)
- [usage](#usage)

## Traethlin's hardware

### Chassis

The robot is based on a RC rock crawler chassis, the [Traxxas trx-4](https://traxxas.com/products/landing/trx-4/).

### Computing

The main computer is a [Raspberry Pi 4 model b](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) running Ubuntu (currently 22.04).  All the high-level processing happens on the RPi, in particular using the [Robotic Operating System](https://ros.org/) (ROS, currently *humble*).  More on this can be found [here](#traethlins-software).

An ESP32 is used to interface with some of the hardware.  Specifically, a [DevKitC](https://www.espressif.com/en/products/devkits/esp32-devkitc/overview) is used for the ESP32 for its convenience of use.  This runs [micro-ROS](https://micro.ros.org/).

These are installed in a waterproof box.  Air is being circulated via a small fan mounted at the base of the mast that holds the camera and the status LEDs.  This helps keep the Raspberry Pi cool.

### GNSS

Positioning is obtained from an [Emlid Reach module](https://emlid.com/reach/).  This provides RTK differential GNSS as long as it has access to a Emlid base station (using a LoRa [adapter](https://hk.store.emlid.com/products/reach-m-lora-radio?variant=44249818824943)) or [NTRIP correction signals](#ntrip).  Other GNSS solutions exist.

### Cameras

3D and thermal

### IMU

### Battery

The battery is a LiPo 3 cells.

The voltage/charge is not being monitored for now so it is useful to connect to the battery a battery low voltage alarm.

### Schematics

#### Electronics

#### Mechanical components

### Building instructions

## Traethlin's software

### ROS

### Micro-ROS

### NTRIP

## Usage

### Starting and stopping Traethlin

Start by connecting the battery.  Not much will happen, apart from the cooling fan will start spinning.

Slide the switch on the side of the computer box forward.  This will power the system.  While the computers are booting up, the LEDs on the mast flash on a green-white pattern.  The pattern becomes flashing green when the system has booted.

At this point the controlling device (mobile phone, tablet, laptop) can be connected to the robot.  By default, the SSID of the robot will be "traethlin-??:??:??" where the question marks are replaced by digits or the letters 'a' to 'f' (this is based on the last three numbers of the MAC address of the WIFI board of the Raspberry Pi, and is therefore unique (enough) to the specific robot).  This can be, for example, "traethlin-7d:2c:c4".  The default password is "traethlin2023".

Once connected, other Internet connections on the device may have to be disabled, such as via a data connection.

A Web browser can now be pointed to "http://traethlin.local/".  This will show a Web page that contains a number of buttons as well as a "joystick" (initially a dark grey circle inside a light grey circle).

Press the "Connect to system" button.  Once connected, the joystick becomes active (dark blue on light blue).

For the original Traxxas speed controller (ESC), press and hold the "EZ set" button for a couple of seconds.  Check the LED on the ESC:

- Solid green: all is well (signal received from the computer (ESP32).
- Flashing green: no signal received.  Start again.
- Flashing red: low voltage, the motor will go slower.
- Solid red: too low voltage, the motor and servos will not run.

For other ESCs, the procedure might be different.  On our robot, slide the switch labelled "Motor" at the front of the computer box outwards.  This powers the motor controller.  Depending on the motor controller, there could be some beeping sounds and some LEDs.

At this point Traethlin can be driven.  Sliding the inner circle of the joystick on the Web page in any direction will result in Traethlin moving in the direction (forward, backward, steering right or left), proportionally to how much the circle is moved.  There are also buttons to lock the front and rear differentials (only lock them on slippery terrain) and to change the gear of the gearbox.

The ESC can be switched off at any time to stop Traethlin from moving.

When all done, press the "Shutdown the system" button and wait for the LEDs on the mast to show a rapid rainbow pattern.  When the rainbow pattern shows, **and only then**, the main switch can be moved back to cut the power to the computer systems.  **Do not forget to disconnect the battery**.
