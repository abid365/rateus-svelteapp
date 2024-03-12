<script>
  import { v4 as uuidv4 } from "uuid";
  import { createEventDispatcher } from "svelte";
  import Button from "../ui/Button.svelte";
  import Card from "../ui/Card.svelte";
  import RatingSelect from "../ui/RatingSelect.svelte";

  const dispatch = createEventDispatcher();

  let text = "";
  let btnDisbaled = true;
  let min = 10;
  let rating = 5;
  let message;

  const handleSelect = (e) => (rating = e.detail);

  const handleInput = () => {
    if (text.trim().length <= min) {
      message = `Text must be at least ${min} characters`;
      btnDisbaled = true;
    } else {
      message = null;
      btnDisbaled = false;
    }
  };

  const handleSubmit = () => {
    if (text.trim().length > min) {
      const newFeedback = {
        id: uuidv4(),
        rating: +rating,
        name: "Test User",
        comments: text,
      };
      dispatch("add-fb", newFeedback);
    }
  };
</script>

<Card>
  <header class="py-1 text-lg font-bold">
    How would you rate your service with us?
  </header>
  <RatingSelect on:rating-select={handleSelect} />
  <form on:submit|preventDefault={handleSubmit} class="flex flex-col gap-y-3">
    <input
      class="px-4 py-3 rounded-md border border-slate-600"
      type="text"
      on:input={handleInput}
      bind:value={text}
      placeholder="Tell us about what you think?"
    />
    {#if message}
      <p class="text-red-400 font-semibold text-sm">{message}</p>
    {/if}
    <Button disabled={btnDisbaled} type="submit">Send</Button>
  </form>
  <div class="absolute -top-14 -left-6 rotate-6">
    <img class="h-24 w-auto" src="/angry-birds.png" alt="angry bird" />
  </div>
</Card>
