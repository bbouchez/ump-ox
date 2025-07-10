# UMP-OX
Universal MIDI Packet (MIDI 1.0 and MIDI 2.0) toolbox and patchbay

UMP-OX is a tool for musicians, sound engineers, audio technician, etc... dealing with MIDI and its most rescent evolution : MIDI 2.0. UMP-OX was inspired by the MIDI-OX utility and started as a debugging tool for KissBox products during the development of Network MIDI 2.0 communication protocol.

**Note that UMP-OX is not related in any way to MIDI-OX. But I want to thank Jamie O'Connell (the programmer who created MIDI-OX) who gave me the authorization to use "UMP-OX" name for my software**

## UMP-OX functionalities
* Universal MIDI Packet (MIDI 1.0 / MIDI 2.0) 16x16  patchbay / matrix
* Full support of MIDI 2.0 protocol
* Integrated RTP-MIDI and NetworkUMP drivers (no system drivers needed)
* UMP message generators for easy testing of UMP setups
* Lua scripting on each output port
* Open Stage Control interface (allow to use Open Stage Control with UMP)


## Installing UMP-OX
### Windows
Download the installer executable from the Releases page and launch it.
The installer normally installs automatically the MS Visual C runtime libraries required by UMP-OX. On some Windows machines, it can happen that one of the runtime (for pthreads) fails during installation. In that case, simply go into the installation directory of ump-ox. You will find the two runtime installers, which can be launcher manually from here (you need to launch them as administrator)

### MacOS
Download the zip from the Releases page and simply unzip the content on the Mac disk drive. The zip file contains the complete application which should appear as it in MacOS once the zip file content is copied.
The first time ump-ox is launched under MacOS, you will probably get a warning from MacOS telling that application was downloaded from Internet and is not safe. Just follow indications from here to allow ump-ox : https://support.apple.com/en-us/102445

Once the app is authorized a first time, it becomes automatically valid for your system and the safety warning will not be displayed again.

## Routers configuration
The key concept of UMP-OX is that all messages processed internally are in Universal MIDI Packet format. UMP-OX must then translate messages coming from/to MIDI 1.0 and RTP-MIDI system interfaces. This task is performed by the **__port routers_**.

Before using UMP-OX, you have to configure the routers for each UMP port of the matrix, using "Configuration / UMP Routers" menu, which opens the following dialog

![001](https://github.com/user-attachments/assets/0ba3a48f-76c4-4ee4-b0e6-f8982a142d05)

In this dialog, double-click on a line to edit the corresponding router properties. First select the "Profile" for the router, as this will provide access to the associated selection/edition boxes. The following screenshot shows a practical example of a router configured for RTP-MIDI device (a QY700 sequencer connected to a KissBox MIDI2TR)

![002](https://github.com/user-attachments/assets/4c8316e4-956a-492d-a869-b2e739d4e1e3)

Once the router is configured, click on Apply to activate the router.

## Connecting routers to configure the patchbay
Once the routers are configured, they become available on the main patchbay

![003](https://github.com/user-attachments/assets/8ca8ebb8-44a7-4d9c-af70-5c874500f945)

The left side of the patchbay show the UMP sources (routers producing UMP messages). The right side of the patchbay show the output ports (going to MIDI /UMP devices). To connect a source to an output port, simply click on the intersection between the source "wire" and the destination "wire" (the colors of the wires are made to identify each of them more easily). A red square will appear to show the connection between the two. You can remove any connection by clicking it again.

The UMP message generator is an internal source which can produce many different UMP messages (for MIDI 1.0 and MIDI 2.0) : Note On/Off, Control Change, Program Change, etc... You can find the various generators in the "View" menu.

For example, the screenshot shows that messages produced by source MKC20, QY700 and the internal UMP generator are sent to the Zynthian V5 port. The messages from internal generator are also sent to QY700 MIDI input.

## Managing profiles
A complete configuration of UMP-OX (routers configuration, patchbay connections, position of windows, etc...) can be stored in a profile. You can create as many profiles as needed, with different connection schemes for example.

To save a profile, just Ctrl+S or go to "File / Save" menu. A profile can be reloaded at any moment using Ctrl+L or "File / Load profile" menu.
