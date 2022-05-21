# buttplug-osc

Thanks to [buttplug.io](https://buttplug.io/), and the original project and creator [buttplug-osc](https://github.com/AlexanderPavlenko/buttplug-osc).

## Usage

```shell
buttplug-osc 0.1.0
Control https://buttplug.io/ devices via OSC

USAGE:
    buttplug-osc [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
        --intiface-connect <intiface-connect>     [default: ws://127.0.0.1:12345]
        --osc-listen <osc-listen>                 [default: udp://0.0.0.0:9000]
        --log-level <rust-log>                    [env: RUST_LOG=]  [default: debug]
```

### VRchat OSC messages / Paramter namess
#### /devices/`<name>`/`<command>`/`<argument>`

  * Device `<name>`
    * full name as in the log output: `INFO buttplug_osc: [XBoxXInputCompatibleGamepad] added`
    * `<name>` as a prefix; may be used to address the multiple devices or ones with a very long name
    * `last` is an alias for the recently (re)connected device
    * `all` is an alias for all connected devices
  * Command `vibrate`
    * Argument `speed`: from 0.0 to 1.0 ([details](https://docs.rs/buttplug/3.0.0/buttplug/client/device/enum.VibrateCommand.html#variant.Speed))
  * Command `stop`

## Features

* Reconnects if device or server temporarily disconnected
* OSC receiver
* Control multiple devices
* Build for Windows 10 in realse folder for now
* to start it for vrchat run "buttplug-osc.exe --intiface-connect ws://127.0.0.1:12345 --osc-listen udp://127.0.0.1:9001"

## Vrchat set up

vrchat parameters should be named 
devices/all/vibrate/speed
devices/all/vibrate/stop
devices/all/vibratepattern/index (int of pattern you want to trigger)
devices/all/vibratesingle/1/speed (flaot of speed you want, 1 or 0 for motor select)
devices/all/vibratesingle/0/speed (flaot of speed you want, 1 or 0 for motor select)
/avatar/parameters/devices/all/vibratepattern/index (int of pattern you want to run)
