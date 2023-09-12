<script>
  export let initialCount;
  export let maxCount;
  let count = initialCount;

  function increment() {
    if (count === maxCount) return;
    count += 1;
  }
</script>


<button type="button" on:click={increment}>Click {count}</button>
