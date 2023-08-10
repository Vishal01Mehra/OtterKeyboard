# OtterKeyboard
![](https://github.com/Vishal01Mehra/OtterKeyBoard/blob/main/Resource/otterKeyBoard.jpg)

This Library is based on [ESP32-BLE-Keyboard](https://github.com/T-vK/ESP32-BLE-Keyboard) and impliments BLE(Bluetooth-Low-Energy) Keyboard for the OtterBoard. Send Keystrokes, Commands, Media Controls, etc to your device with OtterBoard.

## Features

 - [x] Send key strokes
 - [x] Send text
 - [x] Press/release individual keys
 - [x] Media keys are supported
 - [ ] Read Numlock/Capslock/Scrolllock state
 - [x] Set battery level (basically works, but doesn't show up in Android's status bar)
 - [x] Compatible with Android
 - [x] Compatible with Windows
 - [x] Compatible with Linux
 - [x] Compatible with MacOS X (not stable, some people have issues, doesn't work with old devices)
 - [x] Compatible with iOS (not stable, some people have issues, doesn't work with old devices)

## Example

``` C++
/**
 * This example turns the OtterBorad into a Bluetooth Low Energy keyboard that writes the words, presses Enter, presses a media key, and then Ctrl+Alt+Delete
 */
#include <OtterKeyboard.h>

OtterKeyboard OtterKeyboard;

void setup() {
  Serial.begin(115200);
  Serial.println("Starting BLE work!");
  OtterKeyboard.begin();
}

void loop() {
  if(OtterKeyboard.isConnected()) {
    Serial.println("Sending 'Hello world'...");
    OtterKeyboard.print("Hello world");

    delay(1000);

    Serial.println("Sending Enter key...");
    OtterKeyboard.write(KEY_RETURN);

    delay(1000);

    Serial.println("Sending Play/Pause media key...");
    OtterKeyboard.write(KEY_MEDIA_PLAY_PAUSE);

    delay(1000);
    
   //
   // Below is an example of pressing multiple keyboard modifiers 
   // which by default is commented out. 
   // 
   /* Serial.println("Sending Ctrl+Alt+Delete...");
    OtterKeyboard.press(KEY_LEFT_CTRL);
    OtterKeyboard.press(KEY_LEFT_ALT);
    OtterKeyboard.press(KEY_DELETE);
    delay(100);
    OtterKeyboard.releaseAll();
    */

  }
  Serial.println("Waiting 5 seconds...");
  delay(5000);
}
```
## License
This product is open source!

Please review the LICENSE.md [MIT](https://choosealicense.com/licenses/mit/) file for license information.

Please use, reuse, and modify these files as you see fit. Please maintain attribution to Mehra Autonomous systems and release under the same license.

## Contributing
Contributions are welcome. For major changes, please open an issue first to discuss what you would like to change.

## Base Library 
[ESP32-BLE-Keyboard](https://github.com/T-vK/ESP32-BLE-Keyboard)

