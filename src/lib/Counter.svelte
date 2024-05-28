<script>
  let count = 0;
  export let initialCount;
  export let maxCount;
  count = initialCount;

  function increment(){
    if (count === maxCount) return;
    count += 1;
  }

$: string = `you clicked ${count} times`

$: {
  console.log(`you have clickerd ${count} times`)
}
</script>

<h3>{string}</h3>
<button on:click={increment}> Click {count} </button>