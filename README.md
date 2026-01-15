# Pomodoro Timer

A minimalist Pomodoro Timer built with Svelte.

## What is the Pomodoro Technique?

The Pomodoro Technique is a time management method that uses a timer to break work into intervals, traditionally 25 minutes in length, separated by short breaks. This approach helps improve focus, reduce mental fatigue, and maintain consistent productivity throughout the day.

<img width="581" height="1025" alt="image" src="https://github.com/user-attachments/assets/38ae2cd2-ab54-4808-8e17-d5532646471e" />
<img width="1914" height="1014" alt="image" src="https://github.com/user-attachments/assets/1f2178f8-9fb1-49bf-93e1-cd72940aaf95" />

### Technology Stack

- **Svelte**: Reactive component framework
- **JavaScript**: Core timer logic
- **CSS**: Styling UI

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

Edit the constants in the script section to change the time durations!

Thanks!
