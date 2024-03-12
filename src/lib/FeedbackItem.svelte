<script>
  // imports
  import { createEventDispatcher } from "svelte";
  import Card from "./../ui/Card.svelte";

  export let item;
  const dispatch = createEventDispatcher();
  const handleDelete = (Id) => {
    dispatch("delete-feedback", Id);
  };
</script>

<Card>
  <div
    class="absolute bg-pink-500 rounded-full p-4 border border-[#e2e2e2] text-white font-bold -top-2 -left-4"
  >
    {item.rating}
  </div>
  <button
    on:click={() => handleDelete(item.id)}
    class="absolute hover:text-red-400 font-bold top-3 cursor-pointer right-5 text-lg"
  >
    x
  </button>
  <p>{item.comments}</p>
</Card>
