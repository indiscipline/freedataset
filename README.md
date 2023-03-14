# Free Dataset

This is a dataset of various freely-distributed files, primarily intended for testing data compression.

Currently includes only audio.

## Naming scheme

### Audio

`type-channels-samplerate-bitdepth-{description}.wav`

- Type: `instruments` / `music` / `noises` / `tones` / `voice`
- Channels: `mono` / `stereo` / number of channels
- Samplerate: float value in kHz + `k`
- Bitdepth: number of bits + `k` + `f` for floating-point
- Description: `{` + name, notes, other info + `}`

Peg grammar for [Nim pegs](https://nim-lang.org/docs/pegs.html):
```Nim
const DatasetNameRules = """
namingscheme <- {type} '-' {channels} '-' {samplerate} '-' {bitdepth} ('-' description)?
type <- 'instruments' / 'music' / 'noises' / 'tones' / 'voice'
channels <- \d+ / 'mono' / 'stereo'
samplerate <- \d+ ('.' \d+)?  'k'
bitdepth <- ('8' / '16' / '24' / '32' / '64') 'b' 'f'?
description <- '{' {@} '}'"""
```

## Content information

### audio/

The set includes files in a wide variety of PCM formats holding various kinds of sounds, including artificial test tones. This means, this group of files **does not represent a common set of audio** you would find in the wild, **treating them jointly is not statistically representative**.

| File | Description | License
| --- | --- | ---
| instruments-stereo-48k-24b-{Drum stem}.wav | Drum recording, overhead mics with minimal processing. Typical file for audio-engineering workflows. By @indiscipline. | CC BY 4.0
| music-stereo-44k-16b-{Spitsbergen 3}.wav | Progressive electronica. A great track by Viktor Mayorov, this repo's author late friend, coincidentally released under `CC Attribution 3.0 Unported`. From the album ["Мохообразные, лишайники и цианопрокариоты острова Шпицберген"](https://reptalselectricgardens.bandcamp.com/album/--4). | CC BY 3.0
| music-stereo-48k-24b-{Long Way to Tipperary}.wav | "[It's A Long Way To Tipperary](https://archive.org/details/78_its-a-long-long-way-to-tipperary_victor-novelty-band-jack-judge-harry-williams-na_gbia0211792b)" by Judge & Williams, performed by Victor Novelty Band, 1930 (Victor 22487-B).  | Public Domain
| music-stereo-96k-24b-{Drunken Sailor}.wav | ["Drunken Sailor"](https://archive.org/details/78_a-haul-away-joe-b-what-shall-we-do-with-the-drunken-sailor_john-goss-and-the-c_gbia0077233a), trad. arranged by R.R. Terry, performed by John Goss and the Cathedral Male Voice Quartet, 1927 (His Master's Voice (B 2420)). | Public Domain
| noises-mono-48k-16bf.wav | Pink Noise, Binary White Noise, Brown Noise. One minute of each. | CC0
| noises-stereo-96k-16b-{faux-stereo;dithered}.wav | Dithered faux-stereo. One minute of Pink, Binary White and Brown noises. Converted from a higher bitdepth to 16 bit with a conventional dithering noise added. This introduces small differences between otherwise identical interleaved stereo samples, which broadens the distribution of the sample values. For example, in case of Binary noise, you can see `4a0e 4c0e` for left and right channels. | CC0
| noises-stereo-96k-32bf-{faux-stereo}.wav | Faux-stereo: both channels hold identical data, so each other sample is redundant. | CC0
| tones-stereo-48k-32bf-{sweeps}.wav | Sweeps in the audible range, up to ~ 8kHz: 20s sine sweep, 10s triangle sweep, 10s square sweep, 20s of two close sines (beating), 20s of counterdirectional sines.  | CC0
| voice-mono-44.1k-16b-{upconvert}.wav | Narration of "The Art of War" by Sun Tzu [performed by Moira Fogarty for LibriVox.org](https://librivox.org/the-art-of-war-by-sun-tzu/), 2006-11-02. Upconvert: Originally an mp3, decoded to WAV PCM, which should theoretically decrease the entropy. | Public Domain

## Disclaimer

⚠️ Legal status of Public Domain media differs around the world, so take legal advice from a professional. 