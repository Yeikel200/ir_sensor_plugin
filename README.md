# ir_sensor_plugin

This plugin allows Flutter applications to make use of the Infrared Sensor.

## Usage
Support only for Android. If the plugin is invoked on iOS, it will crash your app.
Added permission in the Manifests:
``` 
    <uses-permission android:name="android.permission.TRANSMIT_IR" />
``` 
## How to use the methods

Check whether the device has an infrared emitter.
Returns `"true"` if the device has an infrared emitter, else `"false"` .
``` 
final bool hasIrEmitter = await IrSensorPlugin.hasIrEmitter;
``` 
Query the infrared transmitter's supported carrier frequencies in `Hertz`.
``` 
final String getCarrierFrequencies = await IrSensorPlugin.getCarrierFrequencies;
``` 

Change the frequency with which it is transmitted. Default is **38020 Hz**
``` 
final String result = await IrSensorPlugin.setFrequencies(40000);
``` 


Transmit an infrared pattern, return a String `"Emitting"` if there was no problem in the process.

The value `pattern` has to be a string that contains the behavior in `HEX`, example:
```  
static const TV_POWER_HEX = "0000 006d 0022 0003 00a9 00a8 0015 003f 0015 
003f 0015 003f 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 003f 
0015 003f 0015 003f 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 
0015 0015 003f 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 0015 
0015 0040 0015 0015 0015 003f 0015 003f 0015 003f 0015 003f 0015 003f 0015 
003f 0015 0702 00a9 00a8 0015 0015 0015 0e6e";

final String result = await IrSensorPlugin.transmitString(pattern: TV_POWER_HEX);
```

The value `list` has to be a list of Int, for example:
```
var power = [169,168,21,63,21,63,21,63,21,63,21,63,21,63,21,63,21,1794,169,168,21,21,21,3694];

final String result = await IrSensorPlugin.transmitListInt(list: power);
```

## Getting Started

This project is a starting point for a Flutter
[plug-in package](https://flutter.dev/developing-packages/),
a specialized package that includes platform-specific implementation code for
Android and/or iOS.

For help getting started with Flutter, view our 
[online documentation](https://flutter.dev/docs), which offers tutorials, 
samples, guidance on mobile development, and a full API reference.
