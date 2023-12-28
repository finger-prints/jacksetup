# Jack Setup

## Requirement
You need a virtual cable that I'm pretty sure you already have. 

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
4. Set your `Frames/Period` to either `512` or `1024` (those are the standard ones - I have mine on 1024, pup has 512 - not sure if it would matter for your mic)

![](./assets/jack_settings_1.png)

(If there's an issue with your Sample Rate or Frames/Period - you'll probably hear like little clips in your voice - basically
Windows/Jack would be going at one rate while your mic is doing another so it ends up with the kinda taking a video of a helicopter
effect where the camera sample rate is way slower than helicopter blades so you can't really see the helicopter blades
spinning properly (but in audio form)) (If that happens, I'd swap `512`/`1024` and/or change sample rate to like `44100`)

5. Go over to the `Advanced` tab
6. Set your `Input Device` to your Scarlett interface (I use the Windows DirectSound:: one)
7. Set your `Output Device` to your virtual cable (Windows DirectSound:: again)

(If you start your server later and it pops up with a message about input/output devices, cycle through the other versions)

8. Set `Channels I/O` to `1` on both input and output

This is what mine looks like:

![](./assets/jack_advanced_settings.png)
9. Apply all the settings

You'll have to come back during Carla so leave this open

## Configuring Carla
1. Start your jack server
2. Launch Carla
3. Click `Settings` then `Configure Carla`
4. Go to the `Engine` tab and make it look like mine:

![](./assets/carla_engine_tab.png)

5. Go to the `Plugin Paths` tab
6. Choose VST2 in the dropdown and make sure that the `C:\Program Files\Common Files\VST2` folder is there:

![](./assets/carla_vst_path.png)

7. Do the same thing for VST3
8. Save/close settings (I think just press `Ok`)
9. Click `Engine` then click `Start`

**I could be mucking up the order of this in my memory - if Carla doesn't want to start try setting up the graph in steps 10-13 with Carla open but the Engine stopped, then start Carla**

10. In Jack, click the `Graph` button

![](./assets/jack_graph_button.png)

11. Hopefully, your graph should have `system` blocks on the right and left and a `Carla` block somewhere

Left `system` is your input device and right `system` is your output device. You can make connections/wires by clicking by the edge of the `capture_1` and drag a wire out to other blocks...

12. Wire the left `system`'s `capture_1` so that it has 2 wires going to Carla's `audio-in1` and `audio-in2`
13. Wire Carla's `audio-out1` and `audio-out2` to the right `system`'s `playback_1`

Hopefully, it should look like this now:

![](./assets/jack_graph.png)

## Configuring VSTs in Carla
1. Go to the `Patchbay` tab in Carla

![](./assets/carla_patchbay_tab.png)

2. To make sure everything's working so far, try wiring the left and right Audio input blocks to the output blocks. If you listen to your virtual cable now, you should hear yourself.
3. Now click `Add Plugin` and refresh the `plugins` - hopefully all those VST's you downloaded should load.

![](./assets/carla_add_plugin.png)

4. Add each of the plugins and wire them up to be in the order of mine (or however you want if you know better than me)

**Again prefer VST3 and 64 bit if there are multiple**

**I have an EQ I paid for, so yours will probably be different**

![](./assets/carla_vsts.png)
