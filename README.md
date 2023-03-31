# LoRa-Clear-Broadcast
Proof of concept that LoRa packets can be sent by RNodes without encryption

*I am not an attorney. This is not legal advice. This is a technical demonstration*

## Bottom Line Up Front

LoRa packets can be decoded without specialized hardware or pre-shared information, and the messages contained therein are not obscured. A reasonable person would conclude that this does not violate amateur radio restrictions on obscured communications.

## Situation

As a layman, the FCC seems to prohibit encrypted transmissions over amateur bands. §97.113(a)(4) (https://www.law.cornell.edu/cfr/text/47/97.113) prohibits, in part, "messages encoded for the purpose of obscuring their meaning, except as otherwise provided herein;"

This seems to broadly cover encryption, ciphers, and code words, but does not appear to prohibit Slow Scan Television (SSTV) or Frequncy Modulation (FM). Therefore it is important for the future of LoRa over Amateur Bands to show that the encoding belongs in the latter category, not the former.

## Objective

To demonstrate the status of the RNode/LoRa encoding as non-obscuring, the following objectives must be fulfilled:

1. A broadcast must be made with unmodified RNode reference hardware and software. (Changing frequency bands, coding rate, spreading factor, and bandwidth is acceptable)
3. A naive hardware and software combination must be able to receive this code.
4. The payload of the transmission must be human readable and unmodified.
5. No external knowledge, outside of frequency, bandwidth, coding rate, and spreading factor can be used to decode the message.

By fulfilling all these objectives, it indicates that any given person, knowing of the signal's existance, can determine the meaning and content of the signal, and therefore the meaning is not obscured and would lead a reasonable person to think that it complies with §97.113(a)(4).

## Testing setup consists of:
* Lilygo TTGO T3_v1.6.1 (20210104) using a stock antenna and attached, via USB, to a Windows 10 machine. 
* Lilygo TTGO T3_v1.6.1 (20210104) using a stock antenna and attached, via USB, to a Raspberry Pi 4B. 
* Transmitting/receiving software on Lilygo units is reference implementation of RNode: https://github.com/markqvist/RNode_Firmware/blob/master/Python%20Module/Example.py
* RTL-SDR v3 (Jan 2023) using a 1/2 wavelength dipole, attached to a Windows 10 machine.
* SDR receiving software is SDRAngel https://github.com/f4exb/sdrangel

## Transmission script:
![](https://github.com/faragher/LoRa-Clear-Broadcast/blob/main/XMit.png)

Script has been modified only for com port and RNode configuration. Displayed configuration is for Windows machine. Only difference between implementations is changing COM7 to /dev/ttyAMC0

# Results

The Lilygo units, using the example script, provide a quick proof of concept, but do not ensure that broadcasts are in plaintext. 

![](https://github.com/faragher/LoRa-Clear-Broadcast/blob/main/LilyGo.png)

The chirpchat plugin for SDRAngel was used, without modification, to receive and decode the LoRa transmissions. These are packets from the above transmissions, and demonstrates that the message can be extracted using different software and hardware without knowledge beyond the physical properties of the signal.

![](https://github.com/faragher/LoRa-Clear-Broadcast/blob/main/SDRAngel.png)

To address our objectives:

1. A broadcast must be made with unmodified RNode reference hardware and software. (Changing frequency bands, coding rate, spreading factor, and bandwidth are acceptable)

Broadcasts were made using unmodified LilyGo boards and RNode firmware / libraries. This is a reference implementation of RNodes, modified only for com port names and standard device/message configuration.

2. A naive hardware and software combination must be able to receive this code.

The RTL-SDR is unable to natively decode LoRa transmissions. SDRAngel and its plugins can decode LoRa transmissions, but have no capacity for encryption or obfuscation. 

3. The payload of the transmission must be human readable and unmodified.

The decoded message is in plain text and immediately apparent.

4. No external knowledge, outside of frequency, bandwidth, coding rate, and spreading factor can be used to decode the message.

The entirety of the configuration of ChirpChat is shown, and it includes only basic information regarding the frequency, bandwidth, spreading factor, and basic LoRa information. These have limited options and are often apparent from the signal itself. There is no capacity for obfuscation or secrecy, and the message is decoded properly.

Beyond these objectives, the following generalized points have been demonstrated:

* LoRa signals can be decoded without LoRa specific hardware.
* LoRa signals can be decoded without pre-shared information.
* Decoded signals provide unobfuscated data.

Therefore, the information contained within is not obscured. Encoded data, such as SSTV signals, has been shown to be acceptable so long as it is decodable without obscuring its content. 

It is worth noting that LoRa decoding is difficult without the proper hardware, leading to minor errors in the decoded packets above, but it has been shown that even without specialized hardware, the content of a LoRa message is, in no way, obscured.
