Based on ![magcode's](https://github.com/magcode) ![work](https://github.com/magcode/mopidy-mqtt).

[![Build Status](https://travis-ci.org/odiroot/mopidy-mqtt.svg?branch=master)](https://travis-ci.org/odiroot/mopidy-mqtt)

# Installation

<!-- TOOD: Update -->
<!-- TODO: Publish to PyPI -->

# Features

* Sends information about Mopidy state on any change
    - Playback status
    - Volume
    - Track description
* Reacts to control commands
    - Playback control
    - Tracklist control
    - Volume control
    - Track search [WIP]
* Responds to specific information inquiries

# MQTT protocol

## Topics

Default top level topic: `mopidy`.

Control topic: `mopidy/c`.

Information topic `mopidy/i`.

## Publishing

|      Kind     |  Subtopic |                  Values                   |
|:-------------:|:---------:|:-----------------------------------------:|
| State         |   `/sta`  | `paused` / `stop` / `playing`             |
| Volume        |   `/vol`  |               `<level:int>`               |
| Current track |   `/trk`  | `<artist:str>;<title:str>;<album>` or ` ` |

## Subscribing

|       Kind       | Subtopic |                               Values                              |
|:----------------:|:--------:|:-----------------------------------------------------------------:|
| Playback control | `/plb`   | `play` / `stop` / `pause` / `resume` / `toggle` / `prev` / `next` |
| Volume control   | `/vol`   | `=<int>` or `-<int>` or `+<int>`                                  |
| Add to queue     | `/add`   | `<uri:str>`                                                       |
| Load playlist    | `/loa`   | `<uri:str>`                                                       |
| Clear queue      | `/clr`   | ` `                                                               |
| Search tracks    | `/src`   | `<str>`                                                           |
| Request info     | `/inf`   | `state` / `volume` / `queue`                                  |
