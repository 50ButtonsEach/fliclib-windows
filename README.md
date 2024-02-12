# fliclib-windows

This is the Flic TCP socket server program. This server supports a simple, well-documented, API over a TCP socket to allow you to add new clients that can scan and connect Flic buttons and receive their button events. Application developers can go ahed and start creating their own applications communicating with this server application.

Note: Alternatively, instead of using this application, the button can be configured as a Keyboard (HID over BLE device) directly in the Flic app and can then be paired to the Windows system using Bluetooth to perform standard key commands without the need to write any code.

**Running**

This application needs to be started on the command line (from cmd or PowerShell) with two arguments: the IP address and port to bind the TCP socket.

If you want to be able to access the server only from your local computer on port 5551, execute it with:

```
.\FlicSDK.exe 127.0.0.1 5551
```

If you want to be able to access the server also from the rest of your network on port 5551, execute it with:
```
.\FlicSDK.exe 0.0.0.0 5551
```

The data storage is located in the Windows Registry at HKEY_CURRENT_USER\Software\Shortcut Labs\Flicd.

**Compatibility**

This application requires Windows 10/11 desktop for x86_64 (ARM / Windows IOT is not supported) with the latest update running on a machine that has Bluetooth Low Energy, either built into the computer or with a separate Bluetooth USB dongle. You must also install the Visual Studio 2017 C++ Redistributable (https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170, vc_redist.x64.exe), if it isn't already installed. Bluetooth controllers we have tried out ourselves can be found here: https://github.com/50ButtonsEach/fliclib-linux-hci#bluetooth-controllers.

Currently, Flic 1 and Flic 2 buttons are supported. Flic Twist is not supported.

**Documentation**

This application uses the same protocol as first introduced with our fliclib-linux-hci release. The documentation can be found in the [ProtocolDocumentation.md](https://github.com/50ButtonsEach/fliclib-linux-hci/blob/master/ProtocolDocumentation.md) file.

There are however a few things in that protocol that have not been implemented in this application and those are:

The following fields in the EvtGetInfoResponse:

* `max_pending_connections`
* `max_concurrently_connected_buttons`
* `currently_no_space_for_new_connection`

For now you can ignore those fields.

Battery listener is only supported for Flic 2.

**Clients**

A few client libs are available [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/clientlib).

A simple client implementation can be found [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/simpleclient).
