# XAudio2Playback
XAudio2 Sound Playback Demo

A small demo of playing .wav files using twinBASIC and my WinDevLib package. 

The main difficulty with XAudio2 in tB is that many interfaces do not inherit from IUnknown and have no associated GUID. tB has partial support for these currently; it allows `Extends Nothing` syntax so there's no IUnknown methods at the start of the vtable, but it will still attempt to call Release, causing a crash. We can work around this as a consumer by zeroing the pointer prior to exiting a procedure or other release point. I haven't yet tested how it might work on the `Implements` side, but that's not needed for simple sound playback.

Requires Windows 10+. Windows 8 is possible but you'd need to build WinDevLib with the `WDL_XAUDIO8` compiler const.
