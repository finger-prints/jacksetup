# Jack Setup

## Software Downloads
1. [Jack](https://jackaudio.org/downloads/)
2. [Carla](https://kx.studio/Applications:Carla#Download)

## VSTs
**Some of these make you make an account, if you want I can just send you the VST to make that less annoying**
1. [Renegate](https://www.auburnsounds.com/products/Renegate.html)
2. [RNNoise](https://github.com/werman/noise-suppression-for-voice/releases)
3. [Equalizer](https://www.kvraudio.com/product/qrange-by-lkjb/downloads) (you can use whatever equalizer VST you want)
4. [TDR Feedback Compressor II](https://www.tokyodawn.net/tdr-feedback-compressor-2/)
5. [T-De-Esser](https://techivation.com/t-de-esser/)

### Rough Guide for installing VSTs
1. Prefer VST3 and always do 64 bit - 32 bit just doesn't work on modern Windows
2. Make sure they all install to `C:\Program Files\Common Files\<VST2 or VST3>` depending on whether it's a VST2 or VST3

## Configuring Windows
I'm not 100% sure what this looks like in Windows 11, but I'm sure you can get it.
1. Find your microphone/sound settings
2. Choose a sample rate for your Scarlett interface - it shouldn't really matter but I think you're generally gonna go for `2 ch, 24bit, 48000 kHz`

## Configuring Jack
1. When you install jack, you should get a program called `QjackCtl` - run that
2. Before you start the server, go to `Setup`

![](./assets/jack_setup.png)

3. Set your `Sample Rate` to the same one you set in Windows settings
4. Set your `Frames/Period` to either `512` or `1024`