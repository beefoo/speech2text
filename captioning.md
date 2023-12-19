# Captioning workflow

The goal of this workflow is to generate captions from a video with speech audio, and optionally burn the resulting subtitles into the video using ffmpeg.

## Requirements

1. [Whisper](https://github.com/openai/whisper) for speech-to-text which requires [Python](https://www.python.org/) and [PyTorch](https://pytorch.org/). If you would like to use GPU for faster processing times, you will also need to install a version of the [CUDA toolkit](https://developer.nvidia.com/cuda-toolkit-archive) that is compatible with the PyTorch installation.
2. [FFmpeg](https://ffmpeg.org/download.html) for extracting audio from video and for burning subtitles into video. [Subtitle processing](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo) requires ffmpeg to be built with `--libass`. If you use the pre-built version of ffmpeg, this should be included by default. You will also need to install the Python module via `pip install ffmpeg`.

## Steps

1. Extract audio from video:

```
cd sample
ffmpeg -i americas_library.mp4 -q:a 0 -map a americas_library.mp3
```

2. Run speech-to-text:

```
whisper americas_library.mp3 --model medium --output_format srt
```

3. Make any changes/corrections to the .srt file that is needed

4. Burn the subtitles onto the video

```
ffmpeg -i americas_library.mp4 -vf subtitles=americas_library.srt americas_library_captioned.mp4
```
