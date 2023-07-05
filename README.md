# JPSVolumeButtonHandler

Features:

* Run blocks whenever a hardware volume button is pressed
* Volume button presses don't affect system audio
* Hide the HUD typically displayed on volume button presses
* Works even when the system audio level is at its maximum or minimum, even when muted

## Installation

### Swift Package Manager (SPM)

Add: `https://github.com/jpsim/JPSVolumeButtonHandler.git` (`master` branch) to your "Package Dependencies" in XCode.

Or add: `.package(url: "https://github.com/jpsim/JPSVolumeButtonHandler.git", branch: "master")` to your swift package file.

### From CocoaPods

Add `pod 'JPSVolumeButtonHandler'` to your Podfile.

### Manually

Drag the `JPSVolumeButtonHandler` folder into your project and link the MediaPlayer and AVFoundation frameworks to your project.

## Usage

Set your blocks to be run when the volume buttons are pressed:

```objective-c
self.volumeButtonHandler = [JPSVolumeButtonHandler volumeButtonHandlerWithUpBlock:^{
	// Volume Up Button Pressed
} downBlock:^{
	// Volume Down Button Pressed
}];
```

To enable/disable the handler:

```objective-c
// Start
[self.volumeButtonHandler startHandler:YES]; 
// Stop
[self.volumeButtonHandler stopHandler];
```

To change audio session category (by default `AVAudioSessionCategoryPlayAndRecord`):

```objective-c
// Set category
self.volumeButtonHandler.sessionCategory = AVAudioSessionCategoryAmbient; 
```

To change the audio session category options (by default `AVAudioSessionCategoryOptionMixWithOthers`):

```objective-c
self.volumeButtonHandler.sessionOptions = AVAudioSessionCategoryOptionAllowBluetooth|AVAudioSessionCategoryOptionMixWithOthers;
```

Note that not all options are compatible with all category options. See `AVAudioSession` documentation for details.

## License

This project is under the MIT license.
