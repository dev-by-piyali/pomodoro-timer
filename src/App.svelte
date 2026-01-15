<script>
    import PomodoroTimer from "./lib/PomodoroTimer.svelte";
</script>

<main>
    <div>
        <h1>Pomodoro Timer</h1>
        <PomodoroTimer />
    </div>
    <img src="/image.png" alt="focus" />
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1.2rem;
    }

    h1 {
        color: #3b3654;
        font-weight: bolder;
        text-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
    }

    img {
        opacity: 0.85;
        filter: saturate(0.9) blur(0.2px);
        width: 450px;
    }

    @media (min-width: 900px) {
        main {
            flex-direction: row;
            justify-content: space-evenly;
            align-items: center;
        }

        img {
            width: 600px;
        }
    }
</style>
