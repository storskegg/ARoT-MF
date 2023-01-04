# 1. ARoT-MF
Amateur Radio of Things - Message Formats

- [1. ARoT-MF](#1-arot-mf)
  - [1.1. Kudos](#11-kudos)
  - [1.2. About](#12-about)
  - [1.3. Message Formats](#13-message-formats)
    - [1.3.1. Message Encapsulation Format (MEF)](#131-message-encapsulation-format-mef)
    - [1.3.2. Message Type 2: Hygge](#132-message-type-2-hygge)


## 1.1. Kudos

The name for this repository is inspired in part by [WB2OSZ's HRoT](https://github.com/wb2osz/hrot).

## 1.2. About

I have built a number of wireless devices that are "IoT" at least in spirit, albeit not in practice--that is, while pieces may expose some control plane via web services over my internal network, none of these things are exposed externally over the internet. However, they are generally independent, facilitate either unidirectional or bidirectional communication wirelessly, and do so typically within the ISM regions of the 70cm and 33cm amateur radio bands (ITU Region 1).

While the specific characteristics of each independent device (station) typically fall within the ISM usage regulations, they don't always, ergo they fall into amateur radio use. FCC regulations require documentation of binary encoding that isn't clearly "plaintext." That is, a human may not look at the contents of transmission, and intuitively recognize the contents. As such...

This repository serves as documentation of message formats / payload encodings that I commonly use in my wireless projects for when they fall under the jurisdiction of amateur radio regulations.

## 1.3. Message Formats

If communication is unidirectional, there will be a producor and a consumer of messages. If the communication is bidirectional, there will be a remote and a host (or controller).

### 1.3.1. Message Encapsulation Format (MEF)

Nearly every message I send using these schemes is for my own consumtion. The top level of my encoding is called the Message Encapsulation Format (MEF), and contains two portions:

1. Preamble -- 6 - 11 bytes
2. Data -- >= 1 byte

The Preamble has two parts:

1. Callsign -- 4 to 9 bytes -- Is always my own callsign, and may contain an APRS-like suffix (e.g. W4PHO-7). This serves a dual function. Firstly, it's station identification. Secondly, since other stations share the airwaves, it allows a consumer or host/controller to selectively parse only the messages I wish to, ignoring any other message received.
2. Message Type -- `uint16` -- Message type defined as a 16-bit unsigned integer (0 - 65535).


### 1.3.2. Message Type 2: Hygge

[Details Here](02_hygge.md)
