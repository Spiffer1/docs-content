---
title: 'Detect a Knock'
compatible-products: [all-boards]
difficulty: beginner
description: 'This tutorial shows you how to use a Piezo element to detect vibration.'
tags: 
  - Sensors
  - Input
  - Piezo
---

This tutorial shows you how to use a [**Piezo element**](http://en.wikipedia.org/wiki/Piezoelectric_sensor) to detect vibration, in this case, a knock on a door, table, or other solid surface.

A **piezo** is an electronic device that generates a voltage when it's physically deformed by a vibration, sound wave, or mechanical strain.  Similarly, when you put a voltage across a piezo, it vibrates and creates a tone. Piezos can be used both to play tones and to detect tones.

The sketch reads the piezo output using the `analogRead()` command, encoding the voltage range from 0 to 5 volts to a numerical range from 0 to 1023 in a process referred to as *analog-to-digital conversion*, or *ADC*.

If the sensors output is stronger than a certain threshold, your board will send the string "Knock!" to the computer over the serial port.

Open the serial monitor to see this text.

### Hardware Required

- Arduino Board

- Piezo electric disc

- 1 Megohm resistor

- solid surface

### Circuit

Piezos are **polarized**, meaning that voltage passes through them (or out of them) in a specific direction. Connect the black wire (the lower voltage) to ground and the red wire (the higher voltage) to analog pin 0. Additionally, connect a 1-megohm resistor in parallel to the Piezo element to limit the voltage and current produced by the piezo and to protect the analog input.

It is possible to acquire piezo elements without a plastic housing. These will  look like a metallic disc, and are easier to use as input sensors. Piezo sensors work best when firmly pressed against, taped, or glued their sensing surface.

![](assets/circuit.png)


### Schematic

The piezo is attached to analog pin 0 with a 1 Megohm resistor in between the two legs. The placement of the resistor is used to save the piezo from damage from extra current. Without it, the analog pin might not be capable of reading the piezo's signal.

![](assets/schematic.png)

### Code

In the code below, the incoming piezo data is compared to a threshold value set by the user. Try raising or lowering this value to increase your sensor's overall sensitivity.

<iframe src='https://create.arduino.cc/example/builtin/06.Sensors%5CKnock/Knock/preview?embed&snippet' style='height:510px;width:100%;margin:10px 0' frameborder='0'></iframe>

Note: Line #53, "delay(100)", in the code snippet above should be moved up a line so that it is inside the "if" block and immediately after the "Serial.println("Knock")" command. Otherwise, the code only checks if there is a knock once each 100 milliseconds, and this causes many knocks to go undetected. As the comment on line #53 points out, the only purpose of the delay() is to avoid overwhelming the serial port buffer, so the delay() only needs to occur when something is printed to the Serial port.

### Learn more

You can find more basic tutorials in the [built-in examples](/built-in-examples) section.

You can also explore the [language reference](https://www.arduino.cc/reference/en/), a detailed collection of the Arduino programming language.
