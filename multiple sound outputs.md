# Use Multiple Sound outputs.

Using pulse audio (https://www.freedesktop.org/wiki/Software/PulseAudio/) it is possible to route sound to multiple output devices.
Setting of the preferences can be done with the gui for pulse audio preferences called papref: https://freedesktop.org/software/pulseaudio/paprefs/
Ubuntu automatically includes pulse audio that package does not need to be installed.  The papref gui can be installed with
```bash
sudo apt-get install paprefs
```
Start the gui paprefs:
```bash
paprefs
```
Look though the options.  Select the tab for "Simultaneous Output."

It appears the sound server needs to be stopped.  Then it automatically restarts itself.  It appears this is needed for the 
preferences set using papref to take effect.
```bash
pulseaudio -k
```
Much of this is documented at the askubuntu site: https://askubuntu.com/questions/78174/play-sound-through-two-or-more-outputs-devices

