<script>
  import Timer from "./Timer.svelte";
  import HowTo from "./HowTo.svelte";
  let audio;

  function timerEnds(event) {
    audio.play();
  }
</script>

<h1>Handwashing App</h1>

<Timer on:end={timerEnds} />
<HowTo />

<h3>
  <a href="http://www.who.int/gpsc/clean_hands_protection/en/">
    Picture Source
  </a>
</h3>

<h3>
  <a href="http://www.freesound.org"> Sound Source </a>
</h3>

<p>
  FYI, I never took the time to style this site so that's why it looks so bad.
</p>

<audio bind:this={audio}>
  <source src="airhorn.mp3" />
</audio>

<style>
  h1,
  h3 {
    text-align: center;
  }

  p {
    font-size: 10px;
  }
</style>
