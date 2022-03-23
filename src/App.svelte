<script>
	import HowTo from "./HowTo.svelte";
	import Timer from "./Timer.svelte";
	let audio;
	function timerEnds(e) {
		console.log(e);
		//audio.play();
	}
</script>

<h1>Test Serious</h1>
<Timer on:end={timerEnds}/>
<HowTo />
<audio bind:this={audio}>
	<source src="pikapika.mp3" />
</audio>
<style>
	h1,
	h3 {
		color: green;
		text-align: center;
	}
</style>
