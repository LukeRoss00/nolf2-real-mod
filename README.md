![Banner](https://i.imgur.com/EgTMScZ.png)

---

# Quick setup

Start from a full install of No One Lives Forever 2 (English version), updated to v1.3 with the official patch. If your copy is not up to date, you can still download the patch from the Internet, for instance [here](http://www.moddb.com/games/no-one-lives-forever-2-a-spy-in-harm/downloads/no-one-lives-forever-2-v13-patch). Since the game uses its installation folder to save progress, config files and so on, it is important that you install to a directory for which you have full permissions, e.g. `C:\MyGames\NOLF2`, instead of the default in `Program Files (x86)`. When you install the base game, choose "Recommended" instead of "Minimum"; there is no need either to install DirectX 8.1 or to reboot.

Do NOT use the Widescreen Patch, as it will interfere with the VR conversion. For that matter, don't use any other mods together with the R.E.A.L. mod; many things have been changed, and old mods will probably no longer work or lead to visual corruption.

If you want to preserve your original installation, back up the following files somewhere safe: `autoexec.cfg`, `Lithtech.exe`, `ltmsg.dll`, `SndDrv.dll`, and the `Profiles` folder. The R.E.A.L. mod will not overwrite or delete your game saves.

Finally, you're ready for modding: unrar `NOLF2_REAL_mod_by_LukeRoss_r<N>.rar` into the main game folder (the one where `NOLF2.exe` is), confirm overwrite of existing files, and... that's it. You should be all set. Do not change the resolution from the default of 1280x960 which is set by the R.E.A.L. mod.

# Starting the game in VR

Just run `Lithtech.exe`. There is no need to specify any command line parameters, although you can if you want. You can also use the old launcher, `NOLF2.exe`, but it only leads to some additional, useless mouse clicks which must be done outside of VR.

If you have the Oculus Rift, after the first run the game should appear in your Oculus library as a third-party app, and you should then be able to launch it directly from your Home.

The mod will automatically fetch its command line parameters from the file `VRlaunchcmds.txt`. If you want, you can use a a text editor like Notepad before launching the game to tweak the options, although the only one that I expect people will find useful is the value of `VRSuperSampling`, which by default is set to `2.0`. Sensible values range from 1.0 to 2.0; past that you're going to get diminishing returns. Set supersampling to the highest possible value that your graphics card can manage without starting to drop frames: your eyes will thank you. Do not change the order in which the .rez files appear, and most importantly, be sure that `VR.rez` always comes last. Again, don't change `+ScreenWidth 1280` and `+ScreenHeight 960`: ScreenWidth and ScreenHeight do not control the resolution of the eye buffers, and those specific values are needed for the menus to display properly.

If you encounter problems with 3D sound, you can try deleting the `3DSoundProviderName` line (the game will put the whole contents of the command file on its command line, so you cannot comment out single lines in the file: you have to delete them altogether).

# But I have the Vive, not the Rift!

Since Release 2, the R.E.A.L. mod should be working fine with your HTC Vive thanks to the magic of [Revive](https://github.com/LibreVR/Revive). The game automatically detects whether you're using the Rift or the Vive, and if a Rift is not present, it loads an embedded copy of Revive (updated to [Version 1.2.1](https://github.com/LibreVR/Revive/releases/tag/1.2.1)). Revive in turn connects with SteamVR, and hopefully all this should make the game display correctly on your Vive. 

If the mod somehow fails to detect your Vive, you can try forcing its hand by adding the line `+VRRevive 1` at the end of your `VRlaunchcmds.txt` file. If instead you want to use your Rift but the game insists on launching SteamVR, specify `+VRRevive 0` to disable the internal copy of Revive. The default value if you don't pass anything is `+VRRevive -1` which will enable the auto-detection code.

In case you have a more recent version of Revive that you want to use with the mod, you can just drop your up-to-date copy of `LibRevive32_1.dll` into the `NOLF2Revive` folder, overwriting the one which was put there during installation.

If everything fails and you have Revive installed on your system, it might be worth a try to `Inject...` the executable with Revive manually from the system tray menu (at least one user reported success with this method): normally however that should be unnecessary, and it might even lead to conflicts.

WMR headsets will probably not work or have issues, as Windows Mixed Reality is not yet officially supported by Revive.       

# Controls

Being a true PC game, as opposed to console ports which sadly are so common nowadays, NOLF2 had a LOT of different controls, mapped to almost every key on the keyboard.

If you wish to play at your desk, you can still use the mouse and keyboard just like you would with the original game (of course you'll need some good muscle memory to remember where the keys are, or some frequent peeks through the headset nose gap). Most controls can be freely remapped in the options pages; F6 and F9 are hard-bound by the engine to QuickSave and QuickLoad, and I added F3 to toggle the in-game HUD on and off. 

However, if you want to play standing up and be free to experience VR fully, I have done my best to map all of the important commands onto the not-so-many buttons of the Xbox One controller. The Touch controllers or Vive wands are NOT supported for now, and most likely will never be: too few buttons for such a complex game.

If you decide to use the Xbox One controller, be sure to have it fully switched on and connected (the white light on the center Xbox button must be steady on and unblinking) before you start up the game, otherwise it will not be recognized.

Here are the default mappings. The abbreviations are: LS/RS for the Left Stick and Right Stick; LB/LT for the Left Bumper and Left Trigger; similarly RB/RT for the Right Bumper and Trigger; View is the button near the white Xbox button to the left, and Menu is the one near the Xbox button to the right. The Xbox button itself should work normally, bringing up the Oculus/Dash interface.

- In game:
```
  LS up/down   : Forward / Backward
  LS left/right: Step left / Step right
  LS click     : Toggle Sneak
  RS up/down   : Previous weapon / Next weapon
  RS left/right: Turn left / Turn right (Lean left / Lean right if LS is also pressed)
  RS click     : Zoom
  D-pad up     : Choose 1 or Next weapon 1 (Choose 5 or Next weapon 5 if LS is also pressed)
  D-pad right  : Choose 2 or Next weapon 2 (Choose 6 or Next weapon 6 if LS is also pressed)
  D-pad down   : Choose 3 or Next weapon 3
  D-pad left   : Choose 4 or Next weapon 4
  A            : Jump
  B            : Toggle Crouch
  X            : Action
  Y            : Keychain Light
  LB           : Move body/piece
  LT           : Holster weapon
  RB           : Change ammo
  RT           : Fire
  View         : Pause the game
  Menu         : Mission status
```
- In menus:
```
  D-pad: Emulates the cursor keys (used to navigate the menus)
  A    : Emulates the Enter key (used to select the highlighted option)
  B    : Emulates the Escape key (used to cancel/go back)
```
- In cutscenes:
```
  View    : Pause the cutscene
  B       : Emulates the Escape key (used to access the menu)
  RS click: Emulates the Space key (used to skip the cutscene)
```
- When the game is paused:
```
  LB: Emulates the F6 key (used to QuickSave)
```
- When the game is paused or in menus:
```
  RB: Emulates the F9 key (used to QuickLoad)
```

As you can see, when in game, the Left Stick button acts as a sort of "shift" to allow access to additional commands. If you keep it pressed, it will modify the actions mapped to D-pad up and right, and to Right Stick left/right. If instead you just click and release it, it will toggle the Sneak mode (i.e., change from "Always run" to "Walk" and back again).

If you're using the mod with the HTC Vive, and SteamVR has stolen your controller Menu button for its Dashboard, you have two possible workarounds: either double-click the button when you want to enter or exit the Mission status screen (a double click done quickly enough will not trigger the dashboard), or disable the dashboard altogether from the SteamVR developer settings.    

# Other controllers

In theory, any controller that has a similar button configuration to the Xbox One controller should work, as long as it's capable of sending its commands to Windows through DirectInput: the game is quite old and doesn't understand XInput. One user reported success with the wireless DualShock 4 as long as DS4Windows was not being used (DS4Windows will provide XInput emulation instead of passing the DirectInput commands untouched).

# Savegames

The R.E.A.L. mod saves are fully interchangeable with the original v1.3 version; a normal game can be loaded up and continued in VR, and vice versa. However, the R.E.A.L. mod extends NOLF2 to allow for 99 save slots, while the original only had 10; so, if your VR game is saved at a position from 11 on, you won't be able to continue it with the original version of NOLF2, which will only "see" the first 10 slots (a simple workaround is to save the game again from the R.E.A.L. mod into one of the first 10 slots, or even simpler, to do a quicksave).

# What about Multiplayer? It's grayed out!

Multiplayer is disabled for now. It might be possible to make it work in the future, but I would need more information, as the master server for the multiplayer game was shut down by Sierra back in November 2008, and mods that have come out during the following years to allow the community to continue playing online were not open source.

If you are ßahamutZero or URA, or you have access to the source code for the LivesForever / LivesForeverPlus mods, or you run a currently active server for NOLF2, I would very much like to hear from you.

# Help! Cutscenes make me barf!

I have added a full page of VR options to the game. You can tune the experience to your liking and adapt it to your tolerance of prerecorded camera movements, which will only become stronger and stronger over time if you allow your brain to train gradually.

My intent when writing the R.E.A.L. mod was to provide as close an experience as possibile to the original beauty of the game&mdash;except in VR. This means that I purposely decided to go against what is quickly becoming "common wisdom" in virtual reality, allowing smooth camera movements and even (perhaps a bit disorienting at first for some people) camera zoom.

If you have the stomach for it, set "Cinematic fidelity" to "Expert" and you will be able to see the cutscenes the way the director (or the **D**irector?) originally meant them to be seen, with scripted close-ups on people's faces and meaningful objects, but with the additional freedom of being able to turn your head and move around in roomscale. Be aware that turning your head while the camera is zoomed will lead to some apparent warping of the world. This is optically normal and unavoidable, and it is the same as would happen in real life when looking through binoculars, except that the effect is slightly more noticeable on the Rift due to the wider field of view.

I believe that in a few years everybody will get used to a fuller, stronger visual experience, and we will laugh at weird fixed-angle cameras in VR, the way we laugh today remembering that people used to flee out of theaters because they were terrified by the sight of an incoming train in a black and white movie.

However, if involuntary camera movements or zoom still make you sick, you can disable them by setting "Cinematic fidelity" to "Skilled" or lower, or by tweaking individual options.

# What does R.E.A.L. stand for?

That is clearly explained on page 381 of your Spy Training Manual, which I guess you haven't got around to read properly yet. Why, it's Reality Enhancement Augmentation Layer, of course!

# TL;DR

> **Arrrggghhh!** I just want to play the damn thing! I don't wanna read no stinkin' **manual**!

Oookay. Are you sure that No One Lives Forever 2 is the right choice for you? You're supposed to read lots of stuff during the game... Anyway: **1.** Install the original, unmodded English NOLF2 v1.3; **2.** Unpack the R.E.A.L. mod into the installation folder; **3.** Make sure that your Xbox One controller is on and connected; **4.** Play the game!
