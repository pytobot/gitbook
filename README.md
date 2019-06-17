---
description: An end project by Sybren Maréchal (SAMK University of Applied Science (2019)).
---

# Multi control open source robot for universal programming education \[PYTOBOT\]

## Preface

The following end project is a summary of my 3 year study as a software engineer. All of the gained knowledge from electrotonic to networking and project design are combined into the Pytobot project. With this project that I chose myself, I wanted to support the educational system to provide a robot for children that makes the way into programming easier.

There are a lot of people I’d like to thank for helping me during the process of making the Pytobot. But first of all I want to thank the open source community. For me it was a great help that I could consult the open source community at any time I wanted to. To thank them, my Pytobot will also be added as an open source project, so that other engineers can gain knowledge about it.

Further on, I would like to thank my lectors and professors from SAMK Robotic Engeneering in Finland and VIVES Software Engineering in Belgium. For SAMK, a special thanks to Kortelainen Joonas, Leino Mirka, Petteri Pulkkinen and Valo Pauli to always believe in me and helped me trough the project. In my home University "VIVES", i would like to thank my lectors Nico De Witte, Sille Van Landschoot, Tom Cordemans and Franky Loret. They taught over 3 years all of the knowledge I needed to succeed in this project and they guided me through a difficult path of becoming an engineer.

And last but not least, I want to thank my little brother to always have my back.   
My parents to always support me and my best friends from KSA De Graal to remind me who i am. They are a big part of my life and they guide me to become the best version of myself.

Sybren Maréchal

## Structure

```text
├── Pytobot
├── Hardware
│   ├── Design
│   ├── Circuit-board
│   │   └── Controller
│   │       ├── Battery-input
│   │       │   └── Voltage-regulation
│   │       └── Kill-switch
│   └── Electronic
│       ├── Motor
│       ├── Led-strip
│       ├── Distance-sensor
│       ├── Line-sensor
│       └── Oled
├── Programming
│   ├── Software
│   │    ├── Local-hotspot
│   │    ├── Local-share
│   │    └── Systemd
│   └── Program
│       ├── Frameworks
│       └── Front-end
├── Extra
│   ├── Abbreviation
│   ├── Goals
│   ├── Log
│   └── Sources
└── Business
    ├── Business-model-canvas
    └── Curriculum
```

