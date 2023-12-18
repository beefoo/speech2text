# Captioning workflow

The goal of this workflow is to generate captions from a video with speech audio, and optionally burn the resulting subtitles into the video using ffmpeg.

## Requirements

1. [FFmpeg](https://ffmpeg.org/download.html) for extracting audio from video and for burning subtitles into video. Subtitle processing requires ffmpeg to be built with `--libass`. If you use the pre-built version of ffmpeg, this should be included by default.
2. [Whisper](https://github.com/openai/whisper) for speech-to-text which requires [Python](https://www.python.org/) and [PyTorch](https://pytorch.org/). If you would like to use GPU for faster processing times, you will also need to install a version of the [CUDA toolkit](https://developer.nvidia.com/cuda-toolkit-archive) that is compatible with the PyTorch installation.

## Steps
