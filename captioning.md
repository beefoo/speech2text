# Captioning workflow

The goal of this workflow is to generate captions from a video with speech audio, and optionally burn the resulting subtitles into the video using ffmpeg.

## Requirements

1. [FFmpeg](https://ffmpeg.org/download.html) for extracting audio from video and for burning subtitles into video. Subtitle processing requires ffmpeg to be built with `--libass`. If you use the pre-built version of ffmpeg, this should be included by default.
2. [Whisper](https://github.com/openai/whisper) for speech-to-text which requires [Python](https://www.python.org/) and [PyTorch](https://pytorch.org/). If you would like to use GPU for faster processing times, you will also need to install a version of the [CUDA toolkit](https://developer.nvidia.com/cuda-toolkit-archive) that is compatible with the PyTorch installation.

## Steps

1. Extract audio from video:

```
ffmpeg -i sample/la_guardia.mp4 -q:a 0 -map a sample/la_guardia.mp3
```

2. Run speech-to-text:

```
whisper sample/la_guardia.mp3 --model medium --output_format srt
```

3. Make any changes/corrections to the .srt file that is needed

4. Burn the subtitles onto the video

```
ffmpeg -i sample/la_guardia.mp4 -vf subtitles=sample/la_guardia.srt sample/la_guardia_captioned.mp4
```
