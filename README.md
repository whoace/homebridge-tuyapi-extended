# Homebridge TuyAPI Extended

This code is a forked and modified version of [tuyapi](https://github.com/codetheweb/tuyapi) by [codetheweb](https://github.com/codetheweb). Proceed as you wish.

Homebridge TuyaAPI Extended is a library for communicating with devices that use the [Tuya](http://tuya.com) cloud network. These devices are branded under many different names, but if port 6668 is open on your device chances are this library will work with it.
Currently only supports smart plugs, but it should be fairly trivial to add other types of devices.

## Installation

  `npm install homebridge-tuyapi-extended`

## Basic Usage
```javascript
const TuyaExtendedDevice = require('homebridge-tuyapi-extended');

let tuya = new TuyaExtendedDevice({
  id: 'xxxxxxxxxxxxxxxxxxxx',
  key: 'xxxxxxxxxxxxxxxx'});

tuya.resolveIds().then(() => {
  tuya.get().then(status => {
    console.log('Status: ' + status);

    tuya.set({set: !status}).then(result => {
      console.log('Result of setting status to ' + !status + ': ' + result);

      tuya.get().then(status => {
        console.log('New status: ' + status);
        return;
      });
    });
  });
});
```

This should report the current status, set the device to the opposite of what it currently is, then report the changed status.

See the [setup instructions](docs/SETUP.md) for how to find the needed parameters.

## 📓 Docs

See the [docs](docs/API.md).

**IMPORTANT**: Only one TCP connection can be in use with a device at once. If testing this, do not have the app on your phone open.

## TODO

1.  Add automated tests
2.  Document details of protocol

## Contributors

-   [codetheweb](https://github.com/codetheweb)
-   [blackrozes](https://github.com/blackrozes)
-   [clach04](https://github.com/clach04)
-   [jepsonrob](https://github.com/jepsonrob)


## Original Project:

-   [tuyapi](https://github.com/codetheweb/tuyapi)

## Related

-   [homebridge-tuya](https://github.com/codetheweb/homebridge-tuya-outlet): a [Homebridge](https://github.com/nfarina/homebridge) plugin for Tuya devices
-	[python-tuya](https://github.com/clach04/python-tuya) a Python port by [clach04](https://github.com/clach04)
-	[m4rcus.TuyaCore](https://github.com/Marcus-L/m4rcus.TuyaCore) a .NET port by [Marcus-L](https://github.com/Marcus-L)
