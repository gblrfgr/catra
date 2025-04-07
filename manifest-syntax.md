# Guide to the Catra Manifest Syntax

A Catra configuration is described fully by a single TOML file, called the *manifest*. This file contains everything the system needs to know about the physical design of the device, what firmware/drivers need to be installed (and with which options), and what apps you want to have. The file is broken down into three sections: **system**, **user**, and **apps**.

## The `system` section

```toml
[system]
```

This section describes, as expected, the physical layout of the system. For example, to describe a system with a LilyGO T-Display-S3 connected to an LIS3DH accelerometer and a piezo buzzer, we might have a section that reads:

```toml
[system]
components = ["battery", "button_a", "button_b", "display", "accelerometer", "buzzer"]
mcu = "esp32s3"

[system.battery]
enable_pin = 15
enable_high = true

[system.button_a]
pin = 
```

We could've broken out the WiFi and Bluetooth Low-Energy drivers, but Catra's compiler understands that the ESP32-S3 includes these by default, and so we don't need to state it explicitly.
