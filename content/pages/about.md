---
title: "About Hello Drinkbot"
date: 2019-02-01
type: pages
---

Hello Drinkbot is an open-source cocktail robot platform created by Rich Gibson. The goal is simple: provide the shortest possible path to the "hello world" of cocktail robotics — dispensing cocktails under computer control — while leaving plenty of room to customize, explore, and expand.

## The Philosophy

Cocktail robotics can be about more than robots which serve cocktails. The [Roboexotica](http://www.roboexotica.at/) model describes it as "an index for the integration of technological innovations into the human Lebenswelt" and "radical hedonism in man-machine communication."

The goal of this project is to get more people making more cocktail robots by providing a simple and affordable solution to the "hello world" problem of dispensing cocktails under computer control, with options to customize, explore, and expand on the basic model.

## The Hardware

The bot is built around:

- **Raspberry Pi** — a tiny single-board computer running Linux
- **AdaFruit DC & Stepper Motor HAT** — controls up to 8 peristaltic pumps (or up to 256 with stacked HATs)
- **Peristaltic pumps** — for clean, controllable liquid dispensing
- **Laser-cut wood or acrylic frame** — several case designs available in the GitHub repo

Once assembled, the bot presents as a WiFi access point. Connect to it and control operations via a customized version of the Party Robotics Bartendro software, or roll your own via the REST API.

## The Software

The project includes:

- Sample Python code for command-line dispensing
- A modified fork of [Bartendro](https://github.com/RichGibson/bartendro) — manage ingredients, create cocktail recipes, web-based interface, REST API
- The REST API lets you call dispensing from your own code: `http://hellodrinkbot.local/ws/drink/12?booze14=75&booze11=75`

## History

Hello Drinkbot was featured in **Make Magazine** (Tasty Tech article). It has been demonstrated at Maker Faire, the Cocktail Robotics Grand Challenge at DNA Lounge, and the North Bay Python conference (2024).

The project has had workshops where participants built working four-pump Hello Drinkbots to take home. Approximately 30 bots have been laser-cut and built.

## Contact

- GitHub: [RichGibson/hellodrinkbot](https://github.com/RichGibson/hellodrinkbot)
- Discord: [Join the server](https://discord.gg/HhaduD6ag4)
- Facebook: [Hello Drinkbot group](https://www.facebook.com/groups/602734573508700/)
- Email: Rich.Gibson at gmail.com
