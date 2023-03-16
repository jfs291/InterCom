# InterCom

InterCom is a low-[latency](https://en.wikipedia.org/wiki/Latency_(engineering)) [full-duplex](https://en.wikipedia.org/wiki/Duplex_(telecommunications)#FULL-DUPLEX) intercom(municator) designed for the transmission of media (at this moment, only [audio](https://en.wikipedia.org/wiki/Digital_audio)) between networked users. It is implemented in [Python](https://www.python.org/) and designed as a set of layers that provide an incremental functionality, following a multilevel (one-to-one) [inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)) model:

1. `minimal`: records/plays raw ([CD](https://en.wikipedia.org/wiki/Compact_disc#Audio_CD) quality) audio, and sends/receives the chunks of audio to/from another `intercom` instance.
2. `buffer`: delays the playing of chunks to hide the [network jitter](https://en.wikipedia.org/wiki/Packet_delay_variation).
3. `compress`: uses [DEFLATE](https://en.wikipedia.org/wiki/Deflate) to compress the chunks.
4. `br_control`: uses [quantization](https://en.wikipedia.org/wiki/Quantization_(signal_processing)) to control the transmission [bit-rate](https://en.wikipedia.org/wiki/Bit_rate).
5. `stereo_coding`: removes [spatial](https://en.wikipedia.org/wiki/Joint_encoding) (inter-channel) [redundancy](https://en.wikipedia.org/wiki/Redundancy_(information_theory)).
6. `temporal_coding`: removes [temporal](https://en.wikipedia.org/wiki/Data_compression#Audio) (intra-channel) redundancy.
7. `threshold`: removes phycho-acoustic redundancy generated by the expected [threshold of hearing](https://en.wikipedia.org/wiki/Psychoacoustics#Limits_of_perception).
8. `temporal_masking`: removes phycho-acoustic redundancy generated by the expected [temporal masking effect](https://en.wikipedia.org/wiki/Auditory_masking#Temporal_masking).
9. `spectral_masking`: removes phycho-acoustic redundancy generated by the expected [simultaneous masking effect](https://en.wikipedia.org/wiki/Auditory_masking#Simultaneous_masking).
