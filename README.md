# seriald

seriald is a high performance deamon which manage a serial port as well as provides the OpenWrt ubus interface for IPC.

## Usage

### Read from serial port

Command:

```
ubus listen serial
```

Result:

```
{ "serial": {"data":"<incoming message>"} }
```

`<incoming message>` is a line read from the serial port. All the `CR` (`\r`) and `LF` (`\n`) characters will be eliminated from it.

### Write to serial port

```
ubus call serial send '{"data": "<outgoing message>"}'
```

`data` is a fixed attribute. To send a message to the serial port, replace `<outgoing message>` with the message you want to send.
An `<outgoing message>` will be appended an `LF` (`\n`) character at the end before seriald passes it to the serial port.

## License

Except where otherwise noted, all parts of this software is licensed under [GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html).
This work is based on [picocom](https://github.com/npat-efault/picocom), which is licensed under [GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html).
