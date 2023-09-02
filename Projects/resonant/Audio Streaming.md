Goal: have raspberry Pi stream Respeaker channels to a desktop computer and perform computation there

2/19/23
- Use UDP. Can have packet loss but better for streaming data
-  Pi should be server so clients can reconnect when necessary

Calculate packet loss and how that might affect localization. Assuming lets say 0.1% packet loss, how does that affect localization when sampling rate is considered?

1. Implement ALSA streaming with interfaces
	1. Always be receiving and adding data to accumulator
	2. When the algorithm finishes running, get latest data from collecting thread
2. Create mock algorithm which uses streaming interface to verify applicability
3. Create File streaming interface (with fake sleep as well) to verify it is non-blocking