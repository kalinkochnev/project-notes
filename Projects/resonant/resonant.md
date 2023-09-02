## Questions:
- What is the Welch's method?
# ideas
- using a hash function that dictates how similar 2 functions are to replace the FFT

# Purchases
SD cards
USB C cables
https://www.seeedstudio.com/ReSpeaker-Core-v2-0.html

## Respeaker
Github repo: https://github.com/respeaker/seeed-voicecard

Listing audio devices:
`aplay -l`

Log 2/5/23:
- Turns out that the RP4 is not supported by respeaker. I posted a question to see if it is something I could fix.

Log 2/19/23:
- Tried reading and writing to audio buffers with Rust. It was actually pretty easy using the `alsa` library
- Should look into reducing latency of ALSA [[ALSA#Decreasing latency]]
- Apparently FFTs depend on the factorization of N (the size of the FFT). Prime numbers = Bad [[Rustfft]] (actually only for AVX hardware)
- Also apprently there are hardware specific optimizations (avx, sse, neon)
- Rust FFT package https://crates.io/crates/rustfft
- Should I be using threads or [[Rust#Futures]] when I'm streaming data

**Ideas for development improvements**
- Have the Pi constantly recording audio and leave the processing for an external computer (via sockets) instead of constantly uploading code to the Pi
- Create audio sources from simulation (python)
- 

