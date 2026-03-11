---
title: "What Is Hello Drinkbot?"
date: 2019-03-01
tags: ["overview", "hardware", "software"]
summary: "An overview of the Hello Drinkbot project — hardware, software, philosophy, and how it all fits together."
---

## The Goal

There are a lot of fun "cocktail robots" which don't dispense cocktails, and there are lots of robots which dispense cocktails without a computer (see "Balls of Steel" and "The Corpse Reviver"), but the goal of this project is to get more people making more cocktail robots by providing a simple and affordable solution to the "hello world" problem of dispensing cocktails under computer control — and to provide options where one can customize, explore, and expand on the basic model.

The [Roboexotica](http://www.roboexotica.at/) model is that cocktail robotics serves as "an index for the integration of technological innovations into the human Lebenswelt" and "radical hedonism in man-machine communication."

## How It Works

The bot starts with some laser-cut parts and a few other parts. Once assembled, the bot presents as a WiFi access point. You can connect to it and control its operations using a customized version of the feature-rich software that controls the Party Robotics Bartendro.

The bot uses:
- A **Raspberry Pi** with an **AdaFruit DC & Stepper Motor HAT** to control peristaltic pumps
- **Peristaltic pumps** to dispense liquids and make cocktails or Italian sodas
- A **laser-cut wood or acrylic frame** (several case designs in the GitHub repo)

## The Software

The project comes with sample code that will dispense ingredients from the command line, and a modified version of the Bartendro code that allows you to:

- Manage which ingredients are in each position
- Create and manage a database of cocktail recipes
- Provide a web-based interface for users to select and customize drinks
- Provide a RESTful interface to dispense cocktails from your own code

## The Electronics

The Adafruit motor controller HAT can control two stepper motors, or control forward and reverse on four DC motors, such as the peristaltic pumps in Hello Drinkbot. Since we don't normally need forward and reverse, we can take advantage of that to control **eight peristaltic pumps** with a HAT that normally controls four.

To double the pump capacity: connect one side of your first motor to the first M1 pin and the other side to ground; connect your second motor to the second pin of M1 and ground.

AdaFruit provides a Python library for the motor HAT.

## The Case

The default case is a basic box with openings cut for four peristaltic pumps, mounting holes for a Raspberry Pi, and holes for a monitor cable, 12V power cable, and USB cable. This needs to be placed on a shelf or other support to position it above the supply bottles.

Several case designs are available in the [GitHub repository](https://github.com/RichGibson/hellodrinkbot).
