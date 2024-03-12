<script>
  import "./app.css";
  import "./../public/global.css";
  import FeedbackList from "./lib/FeedbackList.svelte";
  import FeedbackStats from "./lib/FeedbackStats.svelte";
  import FeedbackForm from "./lib/FeedbackForm.svelte";

  let feedback = [
    {
      id: 1,
      rating: 4.5,
      name: "John",
      comments: ["Great work!", "Keep it up!"],
    },
    {
      id: 2,
      rating: 3.9,
      name: "Alice",
      comments: ["Interesting project.", "Looking forward to updates."],
    },
    {
      id: 3,
      rating: 4.6,
      name: "Bob",
      comments: ["Impressive!", "I have some suggestions."],
    },
    {
      id: 4,
      rating: 4.8,
      name: "Eva",
      comments: ["Nice presentation.", "I'd like to collaborate."],
    },
  ];

  const deleteFb = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id !== itemId);
  };

  const addFeedBack = (e) => {
    const data = e.detail;
    feedback = [...feedback, data];
  };

  $: count = feedback.length;
  $: average = feedback.reduce((a, { rating }) => a + rating, 0) / count;
</script>

<main class="container">
  <FeedbackForm on:add-fb={addFeedBack} />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFb} />
</main>
