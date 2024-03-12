<script>
  export let count;
  export let average;
</script>

<div class="flex justify-between itens-center px-5 py-2 font-bold">
  <h1>{count} Reviews</h1>
  <h1>Ratings Average: {average.toFixed(2)}</h1>
</div>
