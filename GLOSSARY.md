# Vibepollo

Vibepollo is a game-streaming host that sends video, audio and input to Moonlight-protocol clients, Artemis among them.

## Audio

**Audio codec**:
The audio encoding a host and client agree on for a session: Opus audio, PCM audio or Dolby audio.
_Avoid_: Audio mode

**Audio format**:
The host setting that picks which audio codec, besides Opus audio, the host offers to clients.
_Avoid_: Codec preference

**Opus audio**:
Audio sent as Opus multistream packets. Every client supports it, and it is the fallback codec when the client doesn't accept the codec the host offered.
_Avoid_: Compressed audio

**PCM audio**:
Audio sent as 16-bit signed samples at 48 kHz with no compression of any kind. The host offers it only when the audio format selects it.
_Avoid_: Uncompressed audio, lossless audio, raw audio

**Dolby audio**:
Audio sent as AC-3 (Dolby Digital) or E-AC-3 (Dolby Digital Plus) access units, in stereo or 5.1. The host offers it only when the audio format selects it.
_Avoid_: Dolby Digital (when either codec is meant), AC3 audio

**Packet duration**:
How many milliseconds of audio one audio packet carries. The client chooses it for Opus audio; PCM audio always uses 5 ms and Dolby audio 32 ms.
_Avoid_: Frame size, packet size

**Channel layout**:
How many speaker channels the audio carries: stereo, 5.1 or 7.1.
_Avoid_: Surround mode, channel config
