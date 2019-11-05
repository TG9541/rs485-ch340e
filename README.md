# RS485-CH340E

[![Order from OSH Park](https://oshpark.com/assets/badge-5b7ec47045b78aef6eb9d83b3bac6b1920de805e9a0c227658eac6e19a045b9c.png)](https://oshpark.com/shared_projects/ijwz2rTz)

I needed a USB-RS485 dongle with reliable automatic direction control and couldn't find any that's small and cheap. The "budget" cmmercial USB-RS485 dongles try to derive direction controll from the Tx signal. Unfortunately some also use a [questionable "dominant-recessive"](https://hackaday.io/project/167532-modbus-things-with-stm8-eforth/log/168474-finding-the-culprit) approach to RX-TX switching.

This repository provides a small CH340E based configurable RS485 or TTL 2/3-wire USB dongle. 

![front](doc/front.png)

![back](doc/back.png)

## PCB
![PCB](doc/pcb.png)

## Schematic

![schematic](doc/schematic.png)

The BOM is in the doc folder.

Note: with J3 weither 5V (default) or 3.3V (1-2 open, 2-3 closed) can be selected if U3 is populated.

## RS485 configuration:

Note: SW1 controlls "TX-RX echo" (pin1-1 closed) or "no echo" (pin2-3 closed). The latter is standard RS485 functionality. The switch can be replaced when connecting the pads as needed.

Note: when using the built-in CH340E 3.3V LDO the maximum number of RS485 nodes is limited by the current provided by the LDO. When a higher fan-out is needed it's better to populate U3 (XC6206P332MR).

### Core RS485 configuration: 
Populate the following:
* front side: U1, U2, C2, C4, J2
* back side: SW1

## Extended RS485 configuration:
Populate the following:
* front side: U1, U2, U3, C1, C2, C4, J2
* back side: SW1, R1, R2, D2, D3

## RS232-TTL configuration:

Either 3-wire or 2-wire (half duplex) configuration is possible:

### 3-wire configuration: 
Populate the following:
* front side: U1, C2, C4, J2
* back side: (optional) R1, R2, D2, D3 

Close jumpers J1 (RX, J2.3) and J2 (TX, J2.2) on the back side. 

### 2-wire configuration: 
Populate the following:
* front side: U1, C2, C4, J2
* back side: D1, (optional) R1, R2, D2, D3 

Close jumpers J1 (RX/TX, J2.3)  on the back side.
