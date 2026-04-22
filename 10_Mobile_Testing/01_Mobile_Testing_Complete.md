# Module 10: Mobile Testing

## Mobile Application Testing Complete Guide

**Last Updated:** January 2026  
**Reading Time:** 2.5 hours  
**Level:** Intermediate

---

## 📋 Table of Contents

1. [Mobile Testing Fundamentals](#mobile-fundamentals)
2. [Android vs iOS Testing](#android-ios)
3. [Mobile-Specific Test Scenarios](#mobile-scenarios)
4. [Orientation & Responsive Testing](#orientation-testing)
5. [Battery & Performance Testing](#battery-performance)
6. [Network Testing](#network-testing)
7. [Mobile Testing Tools](#mobile-tools)
8. [Real Mobile Testing Scenarios](#real-scenarios)
9. [Best Practices & Common Issues](#best-practices)
10. [20+ Interview Questions](#interview-questions)

---

## <a name="mobile-fundamentals"></a>Mobile Testing Fundamentals

### Mobile Testing क्या है?

**Mobile Testing = Mobile applications को test करना**

```
TYPES OF MOBILE APPS:

1. NATIVE APPS
   └─ Platform-specific (Android/iOS)
   └─ Play Store/App Store से download
   └─ Example: WhatsApp, Instagram, Gmail
   └─ Languages: Kotlin/Swift

2. WEB APPS
   └─ Mobile browser में चलते हैं
   └─ URL से access
   └─ Example: m.facebook.com
   └─ Languages: HTML, CSS, JS

3. HYBRID APPS
   └─ Native + Web combination
   └─ WebView में web code
   └─ Example: Twitter Lite, Uber
   └─ Languages: React Native, Flutter
```

### Mobile Testing क्यों Different है?

```
DESKTOP/MOBILE COMPARISON:

┌────────────────────────────────────────────────────────────┐
│ Factor          │ Desktop/Laptop    │ Mobile              │
├────────────────────────────────────────────────────────────┤
│ Screen Size     │ Fixed, Large      │ Small, Varies       │
│ Input           │ Mouse + Keyboard  │ Touch, Gestures     │
│ Network         │ Stable WiFi       │ 4G/5G/WiFi (vary)   │
│ Battery         │ Always plugged    │ Limited battery     │
│ Interruptions   │ Rare              │ Calls, SMS, Alerts  │
│ Orientation     │ Fixed             │ Portrait/Landscape  │
│ Hardware        │ Consistent        │ Various devices     │
│ OS Versions     │ Few               │ Many versions       │
│ Storage         │ Abundant          │ Limited             │
└────────────────────────────────────────────────────────────┘

MOBILE TESTING CHALLENGES:
✓ Multiple devices test करने हैं
✓ Multiple OS versions test करने हैं
✓ Network variations test करने हैं
✓ Battery impact test करना है
✓ Interruptions handle test करने हैं
```

### Mobile Testing Types

```
┌────────────────────────────────────────────────────────────┐
│              MOBILE TESTING TYPES                          │
├────────────────────────────────────────────────────────────┤
│ 1. FUNCTIONAL TESTING                                     │
│    └─ App features work कर रही हैं                       │
│    └─ User flows test करना                               │
│    └─ Forms, buttons, navigation                         │
├────────────────────────────────────────────────────────────┤
│ 2. COMPATIBILITY TESTING                                  │
│    └─ Different devices पर test                         │
│    └─ Different OS versions पर test                     │
│    └─ Different screen sizes पर test                    │
├────────────────────────────────────────────────────────────┤
│ 3. USABILITY TESTING                                      │
│    └─ User experience                                   │
│    └─ Easy to use                                       │
│    └─ Intuitive navigation                               │
├────────────────────────────────────────────────────────────┤
│ 4. PERFORMANCE TESTING                                    │
│    └─ App speed                                         │
│    └─ Battery consumption                               │
│    └─ Data usage                                        │
├────────────────────────────────────────────────────────────┤
│ 5. SECURITY TESTING                                       │
│    └─ Data protection                                   │
│    └─ Secure communication                              │
│    └─ Authentication                                     │
├────────────────────────────────────────────────────────────┤
│ 6. INSTALLATION TESTING                                   │
│    └─ Install/uninstall test                            │
│    └─ Update testing                                    │
│    └─ First launch testing                               │
├────────────────────────────────────────────────────────────┤
│ 7. INTERRUPTION TESTING                                   │
│    └─ Calls के दौरान app behavior                      │
│    └─ SMS/Notifications behavior                        │
│    └─ Low battery behavior                               │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="android-ios"></a>Android vs iOS Testing

### Platform Differences

```
┌────────────────────────────────────────────────────────────┐
│              ANDROID vs iOS TESTING                        │
├────────────────────────────────────────────────────────────┤
│ Aspect            │ Android           │ iOS                │
├────────────────────────────────────────────────────────────┤
│ Devices           │ Many manufacturers│ Apple only         │
│ Screen Sizes      │ Many variations   │ Few variations     │
│ OS Versions       │ Fragmented        │ Unified            │
│                   │ (4, 5, 6, 7+)     │ (Latest + 2-3)     │
│ App Store         │ Play Store        │ App Store          │
│ Review Process    │ Automated         │ Manual review      │
│ Update Time       │ Fast              │ Slow (review)      │
│ Back Button       │ System back       │ App specific       │
│ Permissions       │ Runtime           │ Runtime            │
│ File System       │ Open              │ Sandboxed          │
└────────────────────────────────────────────────────────────┘
```

### Device Fragmentation Challenge

```
ANDROID DEVICE FRAGMENTATION:

Manufacturers: Samsung, Xiaomi, OnePlus, OPPO, Vivo, Realme, etc.

Screen Sizes:
- Small: 4-5 inches
- Normal: 5-6 inches
- Large: 6-7 inches
- Tablet: 7-13 inches

Resolutions:
- HD: 1280x720
- Full HD: 1920x1080
- 2K: 2560x1440
- 4K: 3840x2160

OS Versions in Use (2026):
- Android 15 (Latest) - 15%
- Android 14 - 25%
- Android 13 - 20%
- Android 12 - 15%
- Android 11 - 10%
- Older - 15%

TESTING IMPLICATION:
कम से कम 10-15 device combinations पर test करना पड़ता है!
```

### iOS Testing Considerations

```
iOS DEVICES (2026):

iPhones:
- iPhone 16 Pro Max (6.9")
- iPhone 16 Pro (6.3")
- iPhone 16 (6.1")
- iPhone 15/14 (6.1")
- iPhone SE (4.7")

OS Versions:
- iOS 19 (Latest)
- iOS 18
- iOS 17

TESTING FOCUS:
✓ Latest 3 iOS versions
✓ Different screen sizes
✓ Notch/Dynamic Island handling
✓ Home indicator (no home button)
```

### Cross-Platform Testing

```
HYBRID/FLUTTER/REACT NATIVE APPS:

CHALLENGES:
✗ Platform-specific bugs
✗ Native feature access issues
✗ Performance variations
✗ UI inconsistencies

TESTING APPROACH:
✓ Both platforms पर test करो
✓ Native features test करो (camera, GPS)
✓ Performance compare करो
✓ UI consistency check करो
```

---

## <a name="mobile-scenarios"></a>Mobile-Specific Test Scenarios

### Touch & Gesture Testing

```
TOUCH GESTURES TO TEST:

1. TAP
   └─ Single tap on buttons
   └─ Double tap to zoom
   └─ Long press for context menu

2. SWIPE
   └─ Swipe left/right (navigation)
   └─ Swipe up/down (refresh, dismiss)
   └─ Swipe to delete/archive

3. PINCH
   └─ Pinch to zoom in
   └─ Pinch out to zoom out
   └─ Images, maps में test करो

4. SCROLL
   └─ Vertical scroll
   └─ Horizontal scroll
   └─ Pull to refresh
   └─ Infinite scroll

5. DRAG
   └─ Drag and drop
   └─ Reorder lists
   └─ Slider controls

TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC001: Tap button → Action trigger                       │
│ TC002: Double tap image → Zoom in                        │
│ TC003: Long press item → Context menu                    │
│ TC004: Swipe left → Next page/delete                     │
│ TC005: Swipe down → Refresh                              │
│ TC006: Pinch → Zoom in/out                               │
│ TC007: Scroll fast → Smooth scrolling                    │
│ TC008: Scroll stop → Momentum stops properly             │
│ TC009: Drag item → Reorder works                         │
│ TC010: Multi-touch → Pinch + rotate                      │
└───────────────────────────────────────────────────────────┘
```

### Keyboard Testing

```
KEYBOARD SCENARIOS TO TEST:

1. KEYBOARD APPEARS
   └─ Focus on input field
   └─ Keyboard type correct है? (email, number, text)
   └─ Keyboard overlaps तो नहीं कर रहा?

2. KEYBOARD BEHAVIOR
   └─ Screen resize होती है?
   └─ Content scroll होता है?
   └─ Focused field visible रहता है?

3. KEYBOARD DISMISSED
   └─ Tap outside → Keyboard close
   └─ Submit button → Keyboard close
   └─ Back button → Keyboard close

4. KEYBOARD TYPES
   └─ Email keyboard (@ symbol)
   └─ Number keyboard (numeric pad)
   └─ Phone keyboard (tel)
   └─ Default keyboard

TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC011: Tap input → Keyboard appears                      │
│ TC012: Email field → @ symbol visible                    │
│ TC013: Number field → Numeric keypad                     │
│ TC014: Keyboard open → Content visible                   │
│ TC015: Submit button → Keyboard closes                   │
│ TC016: Tap outside → Keyboard dismisses                  │
│ TC017: Landscape mode → Keyboard fits                    │
│ TC018: Multiple inputs → Focus switch                    │
│ TC019: Autocorrect → Works/disabled                      │
│ TC020: Emoji keyboard → Supported                        │
└───────────────────────────────────────────────────────────┘
```

### Notification Testing

```
NOTIFICATION TYPES:

1. PUSH NOTIFICATIONS
   └─ Server से आते हैं
   └─ App बंद होने पर भी आते हैं
   └─ Lock screen पर दिखते हैं

2. LOCAL NOTIFICATIONS
   └─ App के andar से trigger
   └─ Reminder, alarm type

3. IN-APP NOTIFICATIONS
   └─ App open होने पर
   └─ Banner, toast messages

TEST SCENARIOS:
┌───────────────────────────────────────────────────────────┐
│ TC021: App background → Notification आया → Tap → Open   │
│ TC022: App closed → Notification आया → Tap → Launch     │
│ TC023: App open → Notification आया → Banner दिखा         │
│ TC024: Notification tap → Correct screen open हुआ       │
│ TC025: Multiple notifications → All show properly        │
│ TC026: Notification dismiss → Clears properly            │
│ TC027: Notification settings → Enable/disable works     │
│ TC028: Do Not Disturb → Notifications silent             │
│ TC029: Lock screen → Notification shows/hides            │
│ TC030: Notification action → Reply/Action works          │
└───────────────────────────────────────────────────────────┘
```

---

## <a name="orientation-testing"></a>Orientation & Responsive Testing

### Orientation Testing

```
PORTRAIT vs LANDSCAPE:

PORTRAIT (Vertical):
┌─────────┐
│         │
│         │
│         │
│         │
└─────────┘
- Default mode
- Reading, browsing
- One-hand use

LANDSCAPE (Horizontal):
┌─────────────────┐
│                 │
│                 │
└─────────────────┘
- Videos, games
- Typing
- Two-hand use

ORIENTATION CHANGE TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC031: Portrait → Landscape → UI adjusts                │
│ TC032: Landscape → Portrait → UI adjusts                │
│ TC033: Video playing → Rotate → Fullscreen              │
│ TC034: Form filling → Rotate → Data retained            │
│ TC035: Game playing → Rotate → Continues                │
│ TC036: Image gallery → Rotate → Images fit              │
│ TC037: Chat screen → Rotate → Messages visible          │
│ TC038: Map view → Rotate → Map rotates                  │
│ TC039: Rapid rotation → App doesn't crash               │
│ TC040: Locked orientation → Rotate → No change          │
└───────────────────────────────────────────────────────────┘
```

### Responsive Design Testing

```
SCREEN SIZE TESTING:

Small Phones (< 5"):
┌─────────────┐
│ Compact UI  │
│ Less content│
│ One column  │
└─────────────┘

Normal Phones (5-6"):
┌───────────────┐
│ Standard UI   │
│ Normal content│
│ One column    │
└───────────────┘

Large Phones (6-7"):
┌─────────────────┐
│ Spacious UI     │
│ More content    │
│ May use 2 cols  │
└─────────────────┘

Tablets (7"+):
┌──────────────────────┐
│ Multi-column layout  │
│ Side panels          │
│ Desktop-like         │
└──────────────────────┘

RESPONSIVE TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC041: Small screen → All content visible               │
│ TC042: Large screen → No empty space issues             │
│ TC043: Text → Readable on all sizes                     │
│ TC044: Buttons → Tappable on all sizes                  │
│ TC045: Images → Scale properly                          │
│ TC046: Tables → Scroll or adapt                         │
│ TC047: Navigation → Accessible on all sizes             │
│ TC048: Forms → Input fields usable                      │
│ TC049: Popups → Fit on screen                           │
│ TC050: Bottom nav → Reachable on large phones           │
└───────────────────────────────────────────────────────────┘
```

### Notch & Cutout Testing

```
MODERN PHONE CHALLENGES:

┌─────────────────────────┐
│  ┌───┐  Camera/Sensors │  ← Notch/Dynamic Island
│  │ 📷 │                 │
└──┴─────┴────────────────┘

TESTING CONSIDERATIONS:
✓ App content notch के नीचे तो नहीं?
✓ Status bar visible है?
✓ Fullscreen apps (videos, games) handle कर रहे हैं?
✓ Safe areas defined हैं?

TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC051: Status bar → Fully visible                        │
│ TC052: Content → Not under notch                         │
│ TC053: Video fullscreen → Notch handled                  │
│ TC054: Game → Notch area used properly                   │
│ TC055: Splash screen → Notch covered                     │
│ TC056: Bottom indicator → Home bar visible               │
│ TC057: Landscape → Notch on side handled                 │
│ TC058: Custom ROM → Different cutouts                    │
└───────────────────────────────────────────────────────────┘
```

---

## <a name="battery-performance"></a>Battery & Performance Testing

### Battery Consumption Testing

```
BATTERY DRAIN CAUSES:

1. BACKGROUND PROCESSES
   └─ Location tracking
   └─ Sync operations
   └─ Push notifications

2. SCREEN USAGE
   └─ Bright screen
   └─ Long screen-on time

3. NETWORK USAGE
   └─ Constant data sync
   └─ Poor signal (more power)

4. MEDIA
   └─ Video playback
   └─ Camera usage

5. GPS/LOCATION
   └─ Continuous location
   └─ High accuracy mode

BATTERY TESTING APPROACH:
┌───────────────────────────────────────────────────────────┐
│ MEASURE BATTERY IMPACT:                                   │
│                                                           │
│ 1. Install battery monitor app                            │
│ 2. Note baseline battery drain                           │
│ 3. Use app for 30 minutes                                 │
│ 4. Measure additional drain                              │
│ 5. Compare with competitors                               │
│                                                           │
│ ACCEPTABLE DRAIN:                                         │
│ - Light usage: < 5% per hour                             │
│ - Moderate usage: 5-10% per hour                         │
│ - Heavy usage: 10-15% per hour                           │
│ - Gaming/Video: 15-20% per hour                          │
└───────────────────────────────────────────────────────────┘

TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC059: Idle app → Background drain < 1%/hour            │
│ TC060: Browsing → Battery drain acceptable               │
│ TC061: Video playback → Drain within limits              │
│ TC062: GPS usage → Drain monitored                       │
│ TC063: Camera usage → Drain monitored                    │
│ TC064: Background sync → Drain acceptable                │
│ TC065: Push notifications → Minimal impact               │
│ TC066: Low battery mode → App works                      │
│ TC067: Battery saver → App adapts                        │
│ TC068: Charging → Fast features enabled                  │
└───────────────────────────────────────────────────────────┘
```

### Performance Testing

```
MOBILE PERFORMANCE METRICS:

1. APP LAUNCH TIME
   └─ Cold start: < 3 seconds
   └─ Warm start: < 2 seconds
   └─ Hot start: < 1 second

2. SCREEN RENDERING
   └─ Frame rate: 60 FPS
   └─ Jank (dropped frames): < 1%

3. RESPONSE TIME
   └─ Button tap → response: < 100ms
   └─ Page load: < 2 seconds
   └─ Search results: < 1 second

4. MEMORY USAGE
   └─ RAM consumption: Within limits
   └─ No memory leaks

5. CPU USAGE
   └─ Average: < 20%
   └─ Peaks: < 80% (short duration)

PERFORMANCE TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC069: Cold launch → < 3 seconds                         │
│ TC070: Screen transition → Smooth (< 16ms/frame)         │
│ TC071: Scroll → 60 FPS maintained                        │
│ TC072: Image load → Progressive/placeholder              │
│ TC073: Search → Results < 1 second                       │
│ TC074: Submit → Response < 2 seconds                     │
│ TC075: Memory → No continuous increase                   │
│ TC076: CPU → Spikes return to normal                     │
│ TC077: Long session → Performance consistent             │
│ TC078: Multitasking → Switch smooth                      │
└───────────────────────────────────────────────────────────┘
```

### Data Usage Testing

```
DATA CONSUMPTION TESTING:

APPROXIMATE DATA USAGE:
┌──────────────────────────────────────────────────────────┐
│ Activity              │ Data per minute │ Per hour      │
├──────────────────────────────────────────────────────────┤
│ Browsing              │ 0.5-1 MB        │ 30-60 MB      │
│ Social Media          │ 1-2 MB          │ 60-120 MB     │
│ Video (SD)            │ 3-5 MB          │ 180-300 MB    │
│ Video (HD)            │ 10-15 MB        │ 600-900 MB    │
│ Music Streaming       │ 1-2 MB          │ 60-120 MB     │
│ GPS Navigation        │ 0.5-1 MB        │ 30-60 MB      │
│ VoIP Call             │ 0.5-1 MB        │ 30-60 MB      │
└──────────────────────────────────────────────────────────┘

DATA USAGE TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC079: App download → Size reasonable                    │
│ TC080: First launch → Data usage acceptable              │
│ TC081: Browsing → Data optimized                         │
│ TC082: Images → Compressed/lazy loaded                   │
│ TC083: Videos → Quality options available                │
│ TC084: Background sync → Minimal data                    │
│ TC085: Offline mode → Works without data                 │
│ TC086: Data saver → Respects system setting              │
│ TC087: WiFi vs Mobile → Different behaviors              │
│ TC088: Cache → Efficient, not excessive                  │
└───────────────────────────────────────────────────────────┘
```

---

## <a name="network-testing"></a>Network Testing

### Network Conditions Testing

```
NETWORK TYPES:

2G (EDGE):
- Speed: ~100 Kbps
- Use: Basic browsing, text
- Test: App usable है?

3G:
- Speed: 1-5 Mbps
- Use: Social media, email
- Test: Images load हो रही हैं?

4G (LTE):
- Speed: 10-50 Mbps
- Use: Video, heavy apps
- Test: Performance optimal है?

5G:
- Speed: 100+ Mbps
- Use: 4K video, AR/VR
- Test: High-speed features

WiFi:
- Speed: Varies (10-500 Mbps)
- Use: All activities
- Test: Seamless experience
```

### Network Transition Testing

```
NETWORK HANDOFF SCENARIOS:

┌───────────────────────────────────────────────────────────┐
│ TRANSITION SCENARIOS TO TEST                              │
├───────────────────────────────────────────────────────────┤
│ TC089: WiFi → 4G → Download continues                    │
│ TC090: 4G → WiFi → Video doesn't buffer                  │
│ TC091: 4G → 3G → Quality adjusts                         │
│ TC092: 3G → 2G → Graceful degradation                    │
│ TC093: Network → Airplane mode → Error handled           │
│ TC094: Airplane mode → Network → Auto-reconnect          │
│ TC095: Weak signal → Strong → Improves smoothly          │
│ TC096: Elevator → Signal loss → Recovery                 │
│ TC097: Moving vehicle → Tower handoff                    │
│ TC098: Dual SIM → Switch between SIMs                    │
└───────────────────────────────────────────────────────────┘
```

### Offline Testing

```
OFFLINE SCENARIOS:

1. NO NETWORK
   └─ App launch होता है?
   └─ Cached data दिखता है?
   └─ Error message clear है?

2. OFFLINE MODE
   └─ Cached content accessible है?
   └─ Offline actions queue होते हैं?
   └─ Sync on reconnect?

3. PARTIAL OFFLINE
   └─ Some features work?
   └─ Clear indication of what works?

OFFLINE TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC099: No network → App launches                         │
│ TC100: No network → Cached data shows                    │
│ TC101: No network → Clear error message                  │
│ TC102: Offline reading → Content available               │
│ TC103: Offline actions → Queue for sync                  │
│ TC104: Reconnect → Auto-sync happens                     │
│ TC105: Partial content → What works indicated            │
│ TC106: Offline maps → Downloaded areas work              │
│ TC107: Offline music → Downloaded songs play             │
│ TC108: Flight mode → All offline features work           │
└───────────────────────────────────────────────────────────┘
```

### Network Speed Testing

```
SLOW NETWORK SCENARIOS:

┌───────────────────────────────────────────────────────────┐
│ SLOW NETWORK TEST CASES                                   │
├───────────────────────────────────────────────────────────┤
│ TC109: Page load → Loading indicator shows               │
│ TC110: Image load → Placeholder → Progressive            │
│ TC111: Timeout → Retry option available                  │
│ TC112: Partial load → Available content shows            │
│ TC113: Video → Quality auto-adjusts                      │
│ TC114: Upload → Progress indicator                       │
│ TC115: Failed request → Clear error                      │
│ TC116: Request timeout → Configurable limit              │
│ TC117: Queue requests → Retry when back                  │
│ TC118: Low bandwidth mode → Data saver                   │
└───────────────────────────────────────────────────────────┘
```

---

## <a name="mobile-tools"></a>Mobile Testing Tools

### Emulators vs Simulators vs Real Devices

```
┌────────────────────────────────────────────────────────────┐
│         EMULATOR vs SIMULATOR vs REAL DEVICE              │
├────────────────────────────────────────────────────────────┤
│ Type          │ Pros                  │ Cons              │
├────────────────────────────────────────────────────────────┤
│ Emulator      │ ✓ Free               │ ✗ Not real hardware│
│ (Android)     │ ✓ Easy setup         │ ✗ Slow             │
│               │ ✓ Many configurations│ ✗ Battery/network  │
│               │                      │   simulate नहीं    │
├────────────────────────────────────────────────────────────┤
│ Simulator     │ ✓ Free               │ ✗ Mac only         │
│ (iOS)         │ ✓ Fast               │ ✗ Not real iOS     │
│               │ ✓ Xcode integrated   │ ✗ Limited hardware │
│               │                      │   simulation       │
├────────────────────────────────────────────────────────────┤
│ Real Device   │ ✓ 100% accurate      │ ✗ Expensive        │
│               │ ✓ Real hardware      │ ✗ Limited quantity │
│               │ ✓ Real network       │ ✗ Setup effort     │
│               │ ✓ Real battery       │                    │
└────────────────────────────────────────────────────────────┘

RECOMMENDED APPROACH:
70% Real Devices + 30% Emulators/Simulators
```

### Android Emulator Setup

```
ANDROID STUDIO EMULATOR:

SETUP:
1. Android Studio download करो
2. AVD Manager open करो
3. Create Virtual Device करो
4. Select device (Pixel, Nexus, etc.)
5. Select system image (Android version)
6. Finish!

FEATURES:
✓ Multiple device profiles
✓ Multiple Android versions
✓ GPS simulation
✓ Network simulation
✓ Battery simulation
✓ Camera input
✓ Multi-touch simulation

COMMAND LINE:
adb devices  -- Connected devices list
adb shell    -- Device shell access
adb install app.apk  -- Install app
adb logcat   -- View logs
```

### iOS Simulator Setup

```
XCODE SIMULATOR:

SETUP:
1. Xcode download करो (Mac only)
2. Xcode → Preferences → Components
3. Simulator download करो
4. Run → Simulator opens

FEATURES:
✓ Multiple iPhone models
✓ Multiple iOS versions
✓ Location simulation
✓ Shake gesture
✓ Rotation
✓ Notifications

LIMITATIONS:
✗ Mac only
✗ No Android
✗ Not real hardware
```

### Real Device Cloud Services

```
CLOUD DEVICE FARMS:

┌────────────────────────────────────────────────────────────┐
│ Service          │ Devices      │ Pricing    │ Features   │
├────────────────────────────────────────────────────────────┤
│ BrowserStack   │ 3000+        │ $29-299/mo │ Real devices │
│ Sauce Labs     │ 2000+        │ Custom     │ Real + Virtual│
│ LambdaTest     │ 3000+        │ $15-99/mo  │ Affordable   │
│ AWS Device Farm│ 100s         │ Pay per use│ AWS integrated│
│ Firebase Test  │ 100s         │ Free tier  │ Google cloud  │
│ Lab            │              │            │              │
└────────────────────────────────────────────────────────────┘

RECOMMENDED FOR:
✓ Small teams: LambdaTest (affordable)
✓ Enterprise: BrowserStack (best features)
✓ AWS users: AWS Device Farm
✓ Google users: Firebase Test Lab
```

### Mobile Testing Tools Comparison

```
┌────────────────────────────────────────────────────────────┐
│                  MOBILE TESTING TOOLS                      │
├────────────────────────────────────────────────────────────┤
│ Tool              │ Type          │ Platform │ Cost       │
├────────────────────────────────────────────────────────────┤
│ Android Studio    │ Emulator      │ Android  │ Free       │
│ Xcode             │ Simulator     │ iOS      │ Free       │
│ Appium            │ Automation    │ Both     │ Free       │
│ Espresso          │ Automation    │ Android  │ Free       │
│ XCTest            │ Automation    │ iOS      │ Free       │
│ Detox             │ Automation    │ Both     │ Free       │
│ Charles Proxy     │ Network       │ Both     │ $50        │
│ Fiddler           │ Network       │ Both     │ Free       │
│ Android Debug     │ Debugging     │ Android  │ Free       │
│ Bridge (ADB)      │               │          │            │
│ iOS Instruments   │ Performance   │ iOS      │ Free       │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="real-scenarios"></a>Real Mobile Testing Scenarios

### Scenario 1: E-commerce App Testing

```
APP: Shopping App (Amazon/Flipkart type)

CRITICAL FLOWS:

1. PRODUCT BROWSING
   └─ Search products
   └─ Filter/sort
   └─ Product details
   └─ Image zoom

2. CART MANAGEMENT
   └─ Add to cart
   └─ Update quantity
   └─ Remove items
   └─ Save for later

3. CHECKOUT
   └─ Address selection
   └─ Payment method
   └─ Order review
   └─ Place order

4. ORDER TRACKING
   └─ Order status
   └─ Delivery tracking
   └─ Cancel order
   └─ Return/replace

MOBILE-SPECIFIC TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC119: Product images → Swipe gallery                    │
│ TC120: Add to cart → Button tappable                     │
│ TC121: Checkout form → Keyboard doesn't hide fields      │
│ TC122: Payment → Network loss handled                    │
│ TC123: Order confirm → Notification आया                 │
│ TC124: Delivery tracking → Map works                     │
│ TC125: Rotate → Cart data retained                       │
│ TC126: Low battery → Checkout works                      │
│ TC127: Incoming call → Order not lost                    │
│ TC128: App background → Session retained                 │
└───────────────────────────────────────────────────────────┘
```

### Scenario 2: Social Media App Testing

```
APP: Social Media (Instagram/Facebook type)

CRITICAL FLOWS:

1. FEED
   └─ Scroll posts
   └─ Like/comment
   └─ Share posts
   └─ Load more

2. STORIES
   └─ View stories
   └─ Swipe next/prev
   └─ Reply to story
   └─ Story expires

3. POST CREATION
   └─ Select photo
   └─ Add caption
   └─ Add tags
   └─ Post

4. MESSAGING
   └─ Send message
   └─ Receive message
   └─ Media share
   └─ Voice notes

MOBILE-SPECIFIC TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC129: Feed scroll → Smooth 60 FPS                       │
│ TC130: Pull to refresh → New posts load                  │
│ TC131: Story swipe → Next/prev works                     │
│ TC132: Photo upload → Progress shown                     │
│ TC133: Video autoplay → On WiFi only (setting)           │
│ TC134: Notification → New message alert                  │
│ TC135: Camera access → Permission works                  │
│ TC136: Location tag → GPS permission                     │
│ TC137: Dark mode → System setting follows                │
│ TC138: Background → Message notification                 │
└───────────────────────────────────────────────────────────┘
```

### Scenario 3: Banking App Testing

```
APP: Banking/Finance App

CRITICAL FLOWS:

1. LOGIN & SECURITY
   └─ Biometric login
   └─ MPIN
   └─ OTP verification
   └─ Device binding

2. TRANSACTIONS
   └─ Fund transfer
   └─ Bill payment
   └─ Recharge
   └─ Transaction history

3. ACCOUNT SERVICES
   └─ Balance check
   └─ Mini statement
   └─ FD/RD booking
   └─ Checkbook request

MOBILE-SPECIFIC SECURITY TEST CASES:
┌───────────────────────────────────────────────────────────┐
│ TC139: Screenshot → Blocked in app (security)            │
│ TC140: App switcher → Sensitive data masked              │
│ TC141: Rooted device → App blocks/warns                  │
│ TC142: Biometric → Fingerprint/face works                │
│ TC143: Session timeout → Auto-logout                     │
│ TC144: Network change → Transaction secure               │
│ TC145: OTP auto-read → Works (SMS permission)            │
│ TC146: Secure keyboard → Randomized layout               │
│ TC147: App tamper → Detection works                      │
│ TC148: Uninstall → Device unbound                        │
└───────────────────────────────────────────────────────────┘
```

---

## <a name="best-practices"></a>Best Practices & Common Issues

### Mobile Testing Best Practices

```
1. TEST ON REAL DEVICES
   ✓ Emulators development के लिए
   ✓ Real devices production testing के लिए

2. PRIORITIZE DEVICES
   ✓ Analytics से top devices identify करो
   ✓ Top 10 devices पर test करो
   ✓ बाकी cloud पर test करो

3. AUTOMATE REGRESSION
   ✓ Smoke tests automate करो
   ✓ Critical flows automate करो
   ✓ हर build पर run करो

4. TEST INTERRUptions
   ✓ Calls, SMS, notifications
   ✓ Network changes
   ✓ Battery scenarios

5. MONITOR PERFORMANCE
   ✓ App size track करो
   ✓ Launch time track करो
   ✓ Crash rate monitor करो

6. BETA TESTING
   ✓ TestFlight (iOS)
   ✓ Play Console beta (Android)
   ✓ Real user feedback लो

7. CONTINUOUS TESTING
   ✓ CI/CD में integrate करो
   ✓ हर commit पर test
   ✓ Fast feedback loop
```

### Common Mobile App Issues

```
┌────────────────────────────────────────────────────────────┐
│              COMMON MOBILE APP ISSUES                      │
├────────────────────────────────────────────────────────────┤
│ Issue              │ Symptoms          │ Prevention       │
├────────────────────────────────────────────────────────────┤
│ App Crash          │ Force close       │ Error handling,  │
│                    │                   │ Testing edge cases│
├────────────────────────────────────────────────────────────┤
│ ANR (Not           │ App frozen        │ Async operations,│
│ Responding)        │                   │ Background tasks  │
├────────────────────────────────────────────────────────────┤
│ Memory Leak        │ Slow over time    │ Proper cleanup,  │
│                    │                   │ Memory profiling  │
├────────────────────────────────────────────────────────────┤
│ Battery Drain      │ Fast battery      │ Background limit,│
│                    │                   │ Optimize processes│
├────────────────────────────────────────────────────────────┤
│ UI Overlapping     │ Text/button cut   │ Test all screen  │
│                    │                   │ sizes             │
├────────────────────────────────────────────────────────────┤
│ Network Timeout    │ Loading forever   │ Timeout handling,│
│                    │                   │ Retry mechanism   │
├────────────────────────────────────────────────────────────┤
│ Permission Issues  │ Features don't    │ Request properly,│
│                    │ work              │ Handle denial     │
├────────────────────────────────────────────────────────────┤
│ Orientation Bugs   │ UI broken on      │ Test both        │
│                    │ rotate            │ orientations      │
├────────────────────────────────────────────────────────────┤
│ Keyboard Issues    │ Fields hidden     │ Adjust pan/scroll│
├────────────────────────────────────────────────────────────┤
│ Notification Bugs  │ Not showing/      │ Test all states  │
│                    │ wrong action      │ (open/bg/closed)  │
└────────────────────────────────────────────────────────────┘
```

### Mobile Testing Checklist

```
┌────────────────────────────────────────────────────────────┐
│           MOBILE TESTING CHECKLIST                         │
├────────────────────────────────────────────────────────────┤
│ INSTALLATION:                                              │
□ Install on different devices                              │
□ Install on different OS versions                          │
□ Update from previous version                              │
□ Uninstall and reinstall                                   │
□ Permissions granted/denied scenarios                      │
├────────────────────────────────────────────────────────────┤
│ FUNCTIONAL:                                                │
□ All features work on all devices                          │
□ Touch gestures work properly                              │
□ Navigation works (back, home, app switch)                 │
□ Forms validation works                                    │
□ Error messages display properly                           │
├────────────────────────────────────────────────────────────┤
│ UI/UX:                                                     │
□ All screens render on all devices                         │
□ Text readable on all screens                              │
□ Buttons tappable (min 44x44 dp)                           │
□ Images scale properly                                     │
□ Orientation changes handled                               │
□ Notch/cutout handled                                      │
├────────────────────────────────────────────────────────────┤
│ PERFORMANCE:                                               │
□ App launch < 3 seconds                                    │
□ Smooth scrolling (60 FPS)                                 │
□ No memory leaks                                           │
□ Battery consumption acceptable                            │
□ Data usage optimized                                      │
├────────────────────────────────────────────────────────────┤
│ NETWORK:                                                   │
□ Works on WiFi, 4G, 3G, 2G                                 │
□ Network transitions handled                               │
□ Offline mode works                                        │
□ Timeout and retry works                                   │
├────────────────────────────────────────────────────────────┤
│ INTERRUPTIONS:                                             │
□ Incoming call handled                                     │
□ SMS/Notifications handled                                 │
□ Low battery handled                                       │
□ App background/foreground works                           │
├────────────────────────────────────────────────────────────┤
│ SECURITY:                                                  │
□ Biometric authentication works                            │
□ Sensitive data not in logs                                │
□ Secure communication (HTTPS)                              │
□ Session timeout works                                     │
□ Rooted/jailbroken device handling                         │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="interview-questions"></a>20+ Interview Questions

### Fundamentals (1-5)

**Q1. Mobile testing में सबसे बड़ी challenges क्या हैं?**
```
A:
1. Device Fragmentation - Especially Android में hundreds of devices
2. OS Versions - Multiple versions simultaneously use में
3. Screen Sizes - 4" से 13" तक vary करते हैं
4. Network Conditions - 2G से 5G तक, frequent changes
5. Battery Constraints - Limited battery, optimization needed
6. Interruptions - Calls, SMS, notifications frequent आते हैं
```

**Q2. Emulator, Simulator और Real Device में difference?**
```
A:
Emulator (Android):
- Software जो hardware को simulate करता है
- Free, easy setup
- But slow और real hardware behavior नहीं

Simulator (iOS):
- iOS devices को simulate करता है
- Mac only, Xcode के साथ
- Fast लेकिन real iOS behavior नहीं

Real Device:
- Actual physical device
- 100% accurate testing
- Expensive लेकिन production जैसा environment
```

**Q3. Mobile app का installation testing कैसे करते हैं?**
```
A:
- Fresh install test करो
- Update install test करो (old version से)
- Uninstall और reinstall test करो
- Interrupted installation test करो
- Low storage पर installation test करो
- Different locations पर install (internal, SD card)
```

**Q4. Interruption testing क्या है?**
```
A: App use कर रहे समय जो interruptions आते हैं उनको test करना:
- Incoming calls
- SMS/Notifications
- Low battery alerts
- Network loss
- Alarm triggers
- Other app launches

App को gracefully handle करना चाहिए और resume होना चाहिए।
```

**Q5. Mobile app performance metrics क्या हैं?**
```
A:
- App launch time (cold, warm, hot)
- Frame rate (60 FPS target)
- Memory usage (no leaks)
- CPU usage (average < 20%)
- Battery consumption (per hour %)
- Data usage (MB per session)
- Network response time
```

### Technical (6-12)

**Q6. Different network conditions कैसे test करते हैं?**
```
A:
Emulator में:
- Network type select करो (2G/3G/4G/WiFi)
- Network speed limit करो
- Network profile create करो

Real device पर:
- Airplane mode use करो
- WiFi/mobile data toggle करो
- Elevator/basement में test करो
- Network throttling tools use करो (Charles, Fiddler)
```

**Q7. Battery testing कैसे करते हैं?**
```
A:
- Battery monitor app install करो
- Baseline drain measure करो
- App use करके additional drain measure करो
- Background processes monitor करो
- Location, camera, network usage track करो
- Compare with competitors
```

**Q8. Orientation testing के scenarios?**
```
A:
- Portrait ↔ Landscape transitions
- UI elements properly adjust होते हैं
- Content reflows properly
- Images/videos scale होते हैं
- Form data retain रहता है
- Videos fullscreen होते हैं
- Rapid rotation पर crash नहीं होता
```

**Q9. Mobile app security testing में क्या check करते हो?**
```
A:
- Data encryption (at rest और in transit)
- Biometric authentication
- Session management
- Rooted/jailbroken device detection
- Screenshot blocking (banking apps)
- App tampering detection
- Secure keychain/keystore usage
- Certificate pinning
```

**Q10. Push notification testing कैसे करते हैं?**
```
A:
- App open/closed/background में notifications test करो
- Tap action सही screen पे ले जाती है verify करो
- Notification content correct है check करो
- Multiple notifications handle होती हैं
- Dismiss/clear works
- Settings से enable/disable works
- Do Not Disturb mode respect होता है
```

**Q11. Keyboard testing में क्या देखते हो?**
```
A:
- Keyboard type correct है (email, number, text)
- Keyboard open hone पर UI adjust होता है
- Focused field visible रहता है
- Keyboard close होता है (submit, tap outside)
- Landscape mode में keyboard fits
- Autocorrect/auto-capitalization works
```

**Q12. Mobile app crash कैसे debug करते हो?**
```
A:
- Crash logs collect करो (Logcat for Android, Crashlytics)
- Stack trace analyze करो
- Reproduce steps find करो
- Device/OS version note करो
- Memory/CPU usage check करो
- Fix के बाद regression test करो
```

### Scenario-Based (13-18)

**Q13. App background में चला गया और memory low हो गई। क्या test करोगे?**
```
A:
- App properly state save करता है
- Background में minimal resources use करता है
- Foreground में आने पर properly restore होता है
- Data loss नहीं होता
- Crash नहीं होता
- User को seamless experience मिलता है
```

**Q14. User ने video download की और network चला गया। क्या test करोगे?**
```
A:
- Download pause होता है
- Progress saved रहता है
- Network वापस आने पर resume होता है
- Partial download handle होता है
- User को clear notification मिलता है
- Retry mechanism works
```

**Q15. Payment करते समय app crash हो गया। कैसे test करोगे fix?**
```
A:
- Same payment flow multiple times test करो
- Different payment methods test करो
- Network interruption simulate करो
- App kill और reopen करो
- Transaction status verify करो (double charge तो नहीं)
- Error recovery test करो
- Rollback mechanism test करो
```

**Q16. App slow है loading में। कैसे identify और fix करवाओगे?**
```
A:
- Network calls measure करो (time ले रहे हैं)
- Image sizes check करो (large तो नहीं)
- Database queries optimize करो
- Caching implement करो
- Lazy loading use करो
- Background tasks minimize करो
- CDN use करो for static content
```

**Q17. Different devices पर app अलग-अलग दिखता है। कैसे handle?**
```
A:
- Responsive design implement करो
- Density-independent pixels (dp) use करो
- Multiple screen size layouts बनाओ
- Constraint layouts use करो
- Real devices पर test करो
- Design system follow करो
```

**Q18. iOS और Android में behavior different है। कैसे test करोगे?**
```
A:
- Platform-specific test cases बनाओ
- Native features अलग-अलग test करो
- Design guidelines follow (Human Interface/Material)
- Both platforms पर parallel test करो
- Platform-specific bugs track करो
- Cross-platform framework में bugs report करो
```

### Advanced (19-22)

**Q19. Mobile automation के लिए कौन से tools use करते हो?**
```
A:
- Appium - Cross-platform, open source
- Espresso - Android native
- XCTest - iOS native
- Detox - React Native apps
- Maestro - Modern, easy to use

Choice depends on:
- App type (native/hybrid)
- Team skills
- Budget
- CI/CD requirements
```

**Q20. CI/CD में mobile testing कैसे integrate करते हो?**
```
A:
- Git commit पर build trigger
- Unit tests run
- UI tests on emulator/simulator
- Critical flows on real device cloud
- Performance tests
- Generate reports
- Block deploy if tests fail
```

**Q21. A/B testing कैसे करते हो mobile apps में?**
```
A:
- Feature flags use करो
- Users को segments में divide करो
- Different versions show करो
- Metrics track करो (engagement, conversion)
- Statistical significance check करो
- Winning version deploy करो
```

**Q22. Mobile app accessibility कैसे test करते हो?**
```
A:
- Screen reader testing (TalkBack/VoiceOver)
- Font size adjustments
- Color contrast check
- Touch target sizes (min 44x44 dp)
- Keyboard navigation
- Caption/subtitle support
- Reduce motion support
```

---

## 🎯 Quick Reference: Mobile Testing Cheat Sheet

```
KEY TESTING AREAS:
✓ Functionality - Features work
✓ UI/UX - Looks good, easy to use
✓ Performance - Fast, smooth
✓ Battery - Efficient
✓ Network - Works everywhere
✓ Security - Data safe
✓ Interruptions - Handles calls, SMS

MUST-TEST SCENARIOS:
- Install/Update/Uninstall
- First launch & onboarding
- Login & authentication
- All core features
- Offline mode
- Network transitions
- Orientation change
- Low battery
- Incoming calls
- Notifications

DEVICE COVERAGE:
- Top 5 Android devices
- Top 3 iOS devices
- Multiple OS versions
- Different screen sizes
```

---

*Module 10 Complete ✅*
