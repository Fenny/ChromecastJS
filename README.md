<p align="center">
  <img src="https://i.imgur.com/SE0fwqV.jpg" alt="Castjs" width="100%">
</p>

<h4 align="center">Javascript library for the complex chromecast SDK</h4>

<p align="center">
  <b>Castjs</b> provides simple events and functions to communicate with chromecast devices from the browser.
  <br>
  This library works in chrome, opera, brave and vivaldi, see it in action and check out the <a href="https://castjs.io/demo/">online demo</a>.
</p>

# Getting Started

Include the `cast.min.js` from [cdnjs](https://cdnjs.com/libraries/castjs):
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/castjs/4.1.2/cast.min.js"></script>
```

# Getting Started

Casting a media source to your chromecast device.

```html
<button id="cast">Cast</button>

<script src="https://castjs.io/cast.min.js"></script>
<script>
// Create new Castjs instance
const cjs = new Castjs();

// Wait for user interaction
document.getElementById('cast').addEventListener('click', function() {
    // Check if casting is available
    if (cjs.available) {
        // Initiate new cast session
        cjs.cast('https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/Sintel.mp4');
    }
});
</script>
```

# Supported Browsers
Almost any [Chromium]() based browser supports cast framework out of the box.
<a href="https://vivaldi.com/"><img src="https://vivaldi.com/favicon.ico" height="13"> Vivaldi</a>
<a href="https://brave.com/"><img src="https://brave.com/static-assets/images/brave-favicon.png" height="15"> Brave</a>

##### API Documentation:

```javascript
// Default instance
const cc = new Castjs();

// Custom receiver or joinpolicy
const cc = new Castjs({
    receiver  : 'CC1AD845',              // default
    joinpolicy: 'tab_and_origin_scoped', // default
//  joinpolicy: 'custom_controller_scoped',
//  joinpolicy: 'origin_scoped',
//  joinpolicy: 'page_scoped',
});

// Castjs Events
cjs.on('available',    ()  => {});  // Casting is available
cjs.on('connect',      ()  => {});  // Connected with device
cjs.on('disconnect',   ()  => {});  // Disconnected with device
cjs.on('statechange',  ()  => {});  // Device state
cjs.on('timeupdate',   ()  => {});  // Current time changed
cjs.on('volumechange', ()  => {});  // Volume changed
cjs.on('mute',         ()  => {});  // Muted state changed
cjs.on('unmute',       ()  => {});  // Muted state changed
cjs.on('playing',      ()  => {});  // Media is playing
cjs.on('pause',        ()  => {});  // Media is paused
cjs.on('end',          ()  => {});  // Media ended
cjs.on('buffering',    ()  => {});  // Media is buffering / seeking
cjs.on('event',        (e) => {});  // Catch all events except 'error'
cjs.on('error',        (e) => {});  // Catch any errors

// Castjs functions
cjs.cast(source, [metadata]); // Create session with media
cjs.volume(0.7);              // Change volume
cjs.play();                   // Play media
cjs.pause();                  // Pause media
cjs.mute();                   // Mutes media
cjs.unmute();                 // Unmutes media
cjs.subtitle(2);              // Change active subtitle index
cjs.seek(15);                 // Seek 15 seconds
cjs.seek(15.9, true);         // Seek 15.9% percentage
cjs.disconnect();             // Disconnect session

// Castjs properties
cjs.version          // Castjs Version
cjs.receiver         // Receiver ID
cjs.available        // Casting is available
cjs.connected        // Connected with cast device
cjs.device           // Cast device name
cjs.src              // Media source
cjs.title            // Media title
cjs.description      // Media description
cjs.poster           // Media poster image
cjs.subtitles        // Media subtitles
cjs.volumeLevel      // Volume level
cjs.muted            // If muted
cjs.paused           // If paused
cjs.time             // Time in seconds
cjs.timePretty       // Time formatted in time hh:mm:ss
cjs.duration         // Duration in seconds
cjs.durationPretty   // Duration formatted in hh:mm:ss
cjs.progress         // Progress in percentage 0 - 100
cjs.state            // State of cast device
```

##### TODO

```
- Add local media and stream support after google fixes service worker crash
- Add name space messaging support for custom receivers
- Maybe add video element support: new Castjs($('#video'))

// Suggestions? Let me know!
```

<p align="center">
  Do you want to support my work, feel free to donate a <a href="https://www.buymeacoffee.com/fenny" target="_blank">☕ Hot Beverage</a>
</p>
