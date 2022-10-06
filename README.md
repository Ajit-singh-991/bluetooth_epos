# bluetooth_epos

Flutter plugin that allows to find bluetooth devices & send raw bytes data.
Supports both Android and iOS.




## Main Features
* Android and iOS support
* Scan for bluetooth devices
* Send raw `List<int> bytes` data to a device


## Getting Started

Here are only the most important parts of the code to illustrate how to use the library.

```dart
BluetoothManager bluetoothManager = BluetoothManager.instance;
BluetoothDevice _device;

bluetoothManager.startScan(timeout: Duration(seconds: 4));
bluetoothManager.state.listen((state) {
    switch (state) {
    case BluetoothManager.CONNECTED:
        // ...
        break;
    case BluetoothManager.DISCONNECTED:
        // ...
        break;
    default:
        break;
    }
});


await bluetoothManager.connect(_device);

List<int> bytes = latin1.encode('Hello world!\n').toList();
await bluetoothManager.writeData(bytes);

await bluetoothManager.disconnect();
```


