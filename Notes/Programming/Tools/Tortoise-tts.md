https://github.com/neonbjb/tortoise-tts

1. `cd ~/.local/lib/python<version>/site-packages/tortoise`
- Results are stored under `results`
- Available voices are under `voices`

- You can merge a list of wavs using sox
```
sox $(ls *.wav | sort -n) out.wav
```