# Pomodoro Timer

A minimalist Pomodoro Timer built with Svelte.

## 🍅 What is the Pomodoro Technique?

The Pomodoro Technique is a time management method that uses a timer to break work into intervals, traditionally 25 minutes in length, separated by short breaks. This approach helps improve focus, reduce mental fatigue, and maintain consistent productivity throughout the day.

## 🎯 How It Works

### Timer Flow

1. **Work Session** (25 minutes)
   - Start your focused work period
   - Timer counts down from 25:00 to 00:00

2. **Short Break** (5 minutes)
   - After completing a work session, take a 5-minute break
   - Timer automatically starts counting down

3. **Long Break** (15 minutes)
   - After completing 4 work sessions, enjoy a longer 15-minute break
   - Session counter resets after the long break

### Session Cycle

```
Work (25 min) → Short Break (5 min) → 
Work (25 min) → Short Break (5 min) → 
Work (25 min) → Short Break (5 min) → 
Work (25 min) → Long Break (15 min) → 
[Cycle repeats]
```

## 🎮 Usage

### Controls

- **Start Button**: Begins the timer countdown
  - Disabled when timer is already running
  - Automatically starts after breaks

- **Pause Button**: Pauses the current timer
  - Disabled when timer is not running
  - Allows you to resume from where you left off

- **Reset Button**: Resets the timer to initial state
  - Stops the timer if running
  - Resets to 25-minute work session
  - Clears session counter

### Session Types

The timer displays the current session type at the top:
- **WORK**: Active work/focus session
- **SHORT BREAK**: 5-minute rest period
- **LONG BREAK**: 15-minute extended rest period

## ⚙️ Configuration

The timer uses the following default values (in seconds):

```javascript
DEFAULT_WORK_TIME = 25 * 60        // 25 minutes
DEFAULT_SHORT_BREAK = 5 * 60       // 5 minutes
DEFAULT_LONG_BREAK = 15 * 60       // 15 minutes
WORK_SESSIONS_BEFORE_LONG_BREAK = 4 // 4 work sessions
```
### Changing Timer Durations

Edit the constants in the script section:

```javascript
const DEFAULT_WORK_TIME = 30 * 60;        // Change to 30 minutes
const DEFAULT_SHORT_BREAK = 10 * 60;      // Change to 10 minutes
const DEFAULT_LONG_BREAK = 20 * 60;       // Change to 20 minutes
```

### Technology Stack

- **Svelte**: Reactive component framework
- **JavaScript**: Core timer logic
- **CSS**: Styling and animations

### Key Features

- **Reactive State**: Uses Svelte's reactive statements (`$:`) for automatic UI updates
- **Interval Management**: Properly manages `setInterval` to prevent memory leaks
- **State Tracking**: Maintains separate flags for break type and session state
- **Automatic Transitions**: Handles session transitions without user intervention


### Running the Timer

1. Click **Start** to begin your work session
2. Focus on your task for 25 minutes
3. When the timer reaches 00:00, a break will automatically start
4. Use **Pause** if you need to temporarily stop the timer
5. Use **Reset** to return to the initial state
