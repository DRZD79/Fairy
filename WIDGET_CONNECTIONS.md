# FaerAI - Widget Interconnection Map

This document outlines all the intelligent connections between widgets in the FaerAI system.

## Core Interconnections

### 🔋 Energy Management System

**Energy Modes:**
- **ECO Mode** (🌿): Conserves battery
  - Limits seat warmer to max level 1
  - Limits fan speed to max level 2
  - Reduces max volume to 60%
  - Auto-activates when battery < 20%

- **NORMAL Mode** (⚡): Balanced performance
  - No restrictions
  - Standard power consumption

- **SPORT Mode** (🏎️): Performance oriented
  - Ensures minimum fan speed of 2
  - Optimized for responsiveness

**Battery Drain Calculation:**
```
Battery Drain = 
  (seatWarmer × 0.5) + 
  (fanSpeed × 0.3) + 
  (volume × 0.01) + 
  (isPlaying ? 0.5 : 0) + 
  (activeCall ? 0.3 : 0) + 
  (isNavigating ? 0.4 : 0)
```

### 📞 Phone ↔ 🎵 Music Interactions

1. **Call starts → Music pauses**
   - Active call automatically pauses music playback
   - Volume reduced to 30% for call clarity

2. **Music starts → Call ends**
   - Starting music playback ends active calls
   - Ensures single audio source

3. **Entertainment Widget**
   - Shows "Muted" indicator during calls
   - Content grid opacity reduced (50%) during calls
   - Play buttons disabled during calls

### 🧭 Navigation ↔ Audio

1. **Navigation active → Volume adjustment**
   - Auto-reduces volume to 40% when navigating
   - Allows clear navigation voice instructions

2. **Navigation active → Speed simulation**
   - Vehicle speed increases realistically (up to 65 MPH)
   - Speed displayed in navigation widget
   - Speed shown in vehicle status banner

3. **Music Widget indicator**
   - Shows navigation badge when GPS active
   - "Auto" label indicates automatic volume adjustment

### 🌡️ Climate ↔ Environment

1. **Temperature → Window Tint (Auto-adjust)**
   - Temp > 78°F → Window tint darkens to level 3
   - Temp < 68°F → Window tint lightens to level 1
   - Marked with "Auto" badge in climate widget

2. **Seat Warmer ↔ Fan Speed (Energy Management)**
   - High seat warmer (level 3+) → Reduces fan speed to level 1
   - Prevents excessive simultaneous heating

3. **Window Tint → Display Brightness**
   - Level 1 (light) → 90% brightness
   - Level 2 → 70% brightness
   - Level 3 → 50% brightness
   - Level 4 (dark) → 30% brightness

4. **Ambient Light → Brightness**
   - Low ambient light (<30%) → Further reduces display brightness by 20%
   - Simulates automatic day/night adjustment

### ⚡ Energy Mode → Multiple Systems

1. **ECO Mode enforces:**
   - Seat warmer buttons disabled above level 1
   - Fan speed buttons disabled above level 2
   - Max volume capped at 60%
   - Green energy usage indicator

2. **SPORT Mode:**
   - Minimum fan speed of 2
   - Orange energy usage indicator

3. **Visual Feedback:**
   - Energy mode shown in status banner
   - Climate widget shows "Eco Limited" badge
   - Quick Settings shows "Low Battery - Eco Mode Active" when critical

### 🔆 Ambient Light (Simulated)

- Randomly fluctuates to simulate changing light conditions
- Affects display brightness when combined with window tint
- Displayed in Quick Settings header
- Updates every 3 seconds

## Widget-Specific Displays

### Vehicle Status Banner
Shows real-time data from ALL systems:
- Speed (from navigation)
- Temperature (from climate)
- Volume (from audio)
- Brightness (from display)
- Activity (call/music/navigation/idle)
- Window Tint level
- Battery level with color coding
- Energy mode selector

### Quick Settings
Displays cross-system alerts:
- "Auto-adjusted" when call/music affects volume
- "Low Battery - Eco Mode Active" when battery critical
- Ambient light percentage
- All system controls in one place

### Music Widget
Shows external influences:
- "Paused" badge during calls
- "Auto" badge during navigation
- Volume controlled by multiple sources

### Call Widget
Shows system impact:
- Volume percentage during active calls
- Auto-volume adjustment indicator

### Climate Widget
Shows intelligent automation:
- "Auto" badge when temp-based tint adjustment
- "Eco Limited" when energy mode restricts functions
- Energy usage meter (Watts)
- Real-time power consumption display

### Navigation Widget
Shows speed and route:
- Real-time speed display (only when navigating)
- Start/Stop button affects multiple systems
- Traffic warnings

### Entertainment Widget
Shows playback restrictions:
- "Muted" during calls
- Content grid dimmed when calls active
- Volume slider affects all audio
- Play controls disabled during calls

## System-Wide Status Bar

Bottom status bar shows unified state:
- All Systems Connected indicator
- Energy mode badge (color-coded)
- Volume, Temperature, Tint levels
- Battery percentage
- Current activity status

## Real-Time Simulation

1. **Battery Drain**: Updates every 5 seconds based on active systems
2. **Speed**: Updates every 2 seconds when navigating
3. **Ambient Light**: Fluctuates every 3 seconds
4. **Call Duration**: Updates every second during calls

## Auto-Protection Features

1. **Low Battery (< 20%)**: Automatic ECO mode activation
2. **Energy Conflicts**: Seat warmer/fan coordination
3. **Audio Conflicts**: Only one audio source at a time
4. **Brightness**: Auto-adjusts for comfort and battery

---

**All widgets are fully interconnected and responsive across mobile, tablet, and desktop layouts.**
