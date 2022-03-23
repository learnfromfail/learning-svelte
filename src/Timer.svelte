<script>
    import ProgressBar from "./ProgressBar.svelte";
    const totalSeconds = 4;
    let isRunning = false;
    let secondLeft = totalSeconds;
    // let timer = setInterval(() => {
    //     secondLeft -= 1;
    //     if (secondLeft == 0){
    //         clearInterval(timer);
    //     }
    // }, 1000);
    $: progress = ((totalSeconds - secondLeft)/totalSeconds ) * 100;
    //let haha = ((totalSeconds - secondLeft)/totalSeconds ) * 100; failed, must with $:

    function startTimer(){
        isRunning = true;
        const timer = setInterval(() => {
        secondLeft -= 1;
        if (secondLeft == 0){
            clearInterval(timer);
            isRunning = false;
            secondLeft = totalSeconds;
        }
    }, 1000);
    }
</script>

<div class="border-hint">
    <h3>Timmer</h3>
    <div bp="grid">
        <h2 bp="offset-5@md 4@md 12@sm">Second Left:{secondLeft}, {progress}</h2>
    </div>
    <ProgressBar {progress}/>
    <!--ProgressBar progress={haha}/-->
    <div bp="grid">
        <!-- startTimer() -->
        <button disabled={isRunning} on:click={startTimer} bp="offset-5@md 4@md 12@sm" class="start">Start</button>
    </div>
</div>

<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: rgb(154, 73, 73);
        width: 100%;
        margin: 10px 0;
    }
    .start[disabled]{
        background-color: grey;
        cursor: not-allowed;
    }
</style>
