# Eval CTF

For this eval, retrieve the `vcar` binary on the Teams and execute the following command :

`sudo systemctl stop virtualcar`
`chmod +x vcar`
`./vcar -c`

For almost all challenges, the flag will be sent on vcan0, using ArbitrationID 0x777.


## Chall CAN: Over the bits

Can you find a way to send a single CAN Frame with more than 8 bytes of data to ArbitrationID 0x18AABBCC ?


## Chall CAN: Forensic

Can you find the flag by analysing the provided PCAP ?


## Chall CAN: Unlock the secret

The door unlock command on your virtual car has been updated to a more secure one. Can you manage to unlock the trunk ?


## Chall SOME/IP: Getter, Eventer, Methoder, Stronger

For this challenge, the flag will be sent on vcan0, using ArbitrationID 0x777.

The VirtualCar hosts a SOMEIP Service 0x4500.

This Service has a **Getter**, 0xDDD which returns a 4 bytes value.

Everytime the getter is triggered, an event notification is sent for the **Event** 0xCCC.

You can get the flag by XORing the value returned by the **Getter** and the one from the **Event** at the **Method** 0xEEE.

Beware, each time you request the method, the previous value is discarded, so you'll need to ask the **Getter** again.

You may encounter some issue with Scapy `sr1` function on the localhost, try to run requests twice to get the result or monitor it using `tcpdump -i lo port 13400 -w filename.pcap` to analyse the packets.


## Chall UDS: Read Data By Identifier

Can you read the data Identifier **0x1337** on the ECU having  **UDS Arbitration ID** 0x700 ?


## Chall UDS: Find my secret

Using DoIP, send diagnostic messages to **logical address** 0x17EA to request a Security Access and guess the military grade algorithm used.

You may encounter some issue with Scapy `sr1` function on the localhost, try to run requests twice to get the result or monitor it using `tcpdump -i lo port 13400 -w filename.pcap` to analyse the packets.


## Chall Bonus: H4xx0r

If you're an 1337 H4xx0r, you'll know what to look for !


## SecOC

Can you compute the MAC for the following CAN message '49 53 45 4e' using Arbitration ID 0x321

The SecOC Profile used is SecOC Profile 1

The freshness value is the following:
TripCounter 0x01
ResetCounter 0x5B
MessageCounter 0x1337

The ResetFlag is on 4 bits


## TARA analysis

Perform a basic analysis for the following ECU.

Set a list of assets to protect and possible attacks (without C/I/A criterea).

For one of the attack, describe the attack path and fill an attack feasibility assessment, using value from 0 to 8.

**Qi Charger**
This ECU is a Qi charger, charging wirelessly driver's phone.
It communicates using NFC with the phone to know the charging power and the charge status.
The ECU has a STM32F4 MCU.
Firmware is stored onto the MCU Flash memory.
The ECU is connected on the BD-CAN (Body)
The car where the ECU will be used has a Telematic Control Unit with Bluetooth and Cellular connectivity. The TCU is on the EXT-CAN.
Message between EXT-CAN and BD-CAN are filtered by a gateway (GW).
The ECU supports UDS commands, and firmware upgrade require a valid SecurityAccess in Diagnostic Session Level 0x2.

