<script>
    const DEFAULT_WORK_TIME = 25 * 60;
    const DEFAULT_SHORT_BREAK = 5 * 60;
    const DEFAULT_LONG_BREAK = 15 * 60;
    const WORK_SESSIONS_BEFORE_LONG_BREAK = 4;

    let time = DEFAULT_WORK_TIME;
    let timer = null;
    let isRunning = false;
    let isBreak = false;
    let isLongBreak = false;
    let workSessionsCompleted = 0;

    function startTimer() {
        if (isRunning) return;
        isRunning = true;
        timer = setInterval(() => {
            if (time > 0) {
                time--;
            } else {
                handleTimerComplete();
            }
        }, 1000);
    }

    function handleTimerComplete() {
        pauseTimer();
        if (isBreak) {
            // Break finished, start work session
            startWorkSession();
        } else {
            // Work session finished, start break
            workSessionsCompleted++;
            if (workSessionsCompleted >= WORK_SESSIONS_BEFORE_LONG_BREAK) {
                startLongBreak();
            } else {
                startShortBreak();
            }
        }
    }

    function startWorkSession() {
        isBreak = false;
        isLongBreak = false;
        time = DEFAULT_WORK_TIME;
        startTimer();
    }

    function startShortBreak() {
        isBreak = true;
        isLongBreak = false;
        time = DEFAULT_SHORT_BREAK;
        startTimer();
    }

    function startLongBreak() {
        isBreak = true;
        isLongBreak = true;
        time = DEFAULT_LONG_BREAK;
        workSessionsCompleted = 0; // Reset counter after long break
        startTimer();
    }

    function pauseTimer() {
        if (timer) {
            clearInterval(timer);
            timer = null;
        }
        isRunning = false;
    }

    function resetTimer() {
        pauseTimer();
        isBreak = false;
        isLongBreak = false;
        workSessionsCompleted = 0;
        time = DEFAULT_WORK_TIME;
    }

    $: minutes = String(Math.floor(time / 60)).padStart(2, "0");
    $: seconds = String(time % 60).padStart(2, "0");
    $: sessionType = isBreak
        ? isLongBreak
            ? "Long Break"
            : "Short Break"
        : "Work";
</script>

<div class="timer">
    <div class="session-type">{sessionType}</div>
    <div class="display">{minutes}:{seconds}</div>
    <div class="controls">
        <button class="btn" onclick={startTimer} disabled={isRunning}
            >Start</button
        >
        <button class="btn" onclick={pauseTimer} disabled={!isRunning}
            >Pause</button
        >
        <button class="btn" onclick={resetTimer}>Reset</button>
    </div>
</div>

<style>
    .timer {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .session-type {
        font-size: 1.5rem;
        text-transform: uppercase;
    }

    .display {
        font-size: 6rem;
    }

    .controls {
        display: flex;
        gap: 1rem;
    }

    .btn:disabled {
        opacity: 0.4;
        cursor: not-allowed;
    }
</style>
