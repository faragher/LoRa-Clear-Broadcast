# LoRa-Clear-Broadcast
Proof of concept that LoRa packets can be sent by RNodes without encryption

*I am not an attorney. This is not legal advice. This is a technical demonstration*

As a layman, the FCC seems to prohibit encrypted transmissions over amateur bands. §97.113(a)(4) (https://www.law.cornell.edu/cfr/text/47/97.113) prohibits, in part "messages encoded for the purpose of obscuring their meaning, except as otherwise provided herein;"

This seems to broadly cover encryption, ciphers, and code words, but does not appear to prohibit Slow Scan Television (SSTV) or Frequncy Modulation (FM). Therefore it is important for the future of LoRa over Amateur Bands to show that the encoding belongs in the latter category, not the former.

To do this, the following objectives must be fulfilled:
* A broadcast must be made with unmodified RNode reference hardware and software. (Changing frequency bands, coding rate, spreading factor, and bandwidth are acceptable)
* A naive hardware and software combination must be able to receive this code.
* The payload of the transmission must be human readable and unmodified.
* No external knowledge, outside of frequency, bandwidth, coding rate, and spreading factor can be used to decode the message.

By fulfilling all these objectives, it indicates that any given person, knowing of the signal's existance, can determine the meaning and content of the signal, and therefore the meaning is not obscured and would lead a reasonable person to think that it complies with §97.113(a)(4).
