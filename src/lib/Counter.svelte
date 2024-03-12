<script>
  let count = 0
  const increment = () => {
    count += 1
  }
</script>

<button class="border border-slate-400 px-3 py-2 rounded-md bg-purple-400" on:click={increment}>
  count is {count}
</button>
