<script>
  import ProgressBar from "./ProgressBar.svelte";
  import { createEventDispatcher } from "svelte";

  const totalSeconds = 20;
  let secondsLeft = totalSeconds;
  let isRunning = false;
  $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100;
  const dispatch = createEventDispatcher();

  function startTimer() {
    isRunning = true;
    const timer = setInterval(() => {
      secondsLeft -= 1;
      if (secondsLeft == 0) {
        clearInterval(timer);
        isRunning = false;
        secondsLeft = totalSeconds;
        dispatch("end");
      }
    }, 1000);
  }
</script>

<div bp="grid">
  <h2 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsLeft}</h2>
</div>

<ProgressBar {progress} />

<div bp="grid">
  <button
    disabled={isRunning}
    on:click={startTimer}
    class="start"
    bp="offset-5@md 4@md 12@sm">Start</button
  >
</div>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: red;
    width: 100%;
    margin: 10px 0;
  }
  .start[disabled] {
    background-color: grey;
    cursor: not-allowed;
  }
</style>
