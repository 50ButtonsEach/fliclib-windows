# fliclib-windows

This is a Beta release of the Flic TCP socket server program that will later be integrated in the final Flic app for Windows. This server supports a simple, well-documented, API over a TCP socket to allow you to add new clients that can scan and connect Flic buttons and receive their button events. We decided to release a Beta version of this so that application developers can go ahed and start creating their own applications at this time.

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

**Compatibility**

This application requires Windows 10 desktop for x86 or x86_64 (ARM / Windows IOT is not supported) with the latest update running on a machine that has Bluetooth Low Energy, either built into the computer or with a separate Bluetooth USB dongle. You must also install the Visual Studio 2015 C++ Redistributable (https://www.microsoft.com/en-us/download/details.aspx?id=48145, vc_redist.x86.exe), if it isn't already installed. Bluetooth controllers we have tried out ourselves can be found here: https://github.com/50ButtonsEach/fliclib-linux-hci#bluetooth-controllers.

**Documentation**

This application uses the same protocol as first introduced with our fliclib-linux-hci release. The documentation can be found in the [ProtocolDocumentation.md](https://github.com/50ButtonsEach/fliclib-linux-hci/blob/master/ProtocolDocumentation.md) file.

There are however a few thing in that protocol that have not been implemented in this application and those are:

The following fields in the EvtGetInfoResponse:

* `max_pending_connections`
* `max_concurrently_connected_buttons`
* `currently_no_space_for_new_connection`

For now you can ignore those fields.

**Clients**

A few client libs are available [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/clientlib).

A simple client implementation can be found [here](https://github.com/50ButtonsEach/fliclib-linux-hci/tree/master/simpleclient).






