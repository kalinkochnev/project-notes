[[Introduction to Sound Programming With ALSA| Article Highlights]]
- Series of kernel drivers for soundcards

**Control interfaces**: a general-purpose vacility ofr managing resgisters of sound cards
**PCM interface**: The interface for managing digital audio capture and playback

## Accesing specific ALSA device
- Can use hardware/software devices. indicated with `hw: i,j` where `i` is the card number and `j` is the device on the card

## Hardware software abstraction
- The hardware buffer in a soundcard is a ring buffer. If exceeds limit, it writes over itself (overrun). This triggers an interrupt.
- Overrun/Underun appears as `XRUN` error
- ALSA abstracts the hardware with an "application buffer"

## Interleaved vs Non-interleaved
- Interleaved buffers alternate channels with each index `[<1>, <2>, <1>, <2>]`
- Non-interleaved has each channel's data appended one after another `[<1>, <1>, <2>, <2>]`


![[Pasted image 20230219152811.png]]

## Typical ALSA use-case
1. Open interface for capture or playback
2. Set hardware parameters
3. (access mode, data format, channels, rate, etc.)
4. While there is data to be processed:
		read PCM data (capture)
		or write PCM data (playback)
1. Close interface

## Fragments and periods
[Article](http://0pointer.de/blog/projects/all-about-periods.html)
![[Pasted image 20230219153909.png]]
- ALSA breaks up buffers into periods to prevent massive block writes
- You should not decrease the period because this will result in extra scheduling work for the operating system
- In practice you want to write as much data as `snd_pcm_avail()` says is available. If the data written does not fit, you will have to buffer it yourself

**Latency**: defined by buffer size
**Wake up interval**: defined by fragment/period size

## Decreasing latency
- Increase the priority of the thread
- https://www.alsa-project.org/wiki/Low_latency_howto
