<script>
  // import { recurrent } from "brain.js/dist/src";
  export let commentsTitle;
  export let commentsList;

  // let network;

  // console.log(recurrent);

  // network.train([
  //   { input: "rising", output: "positive" },
  //   { input: "bored", output: "negative" },
  //   { input: ":) ;) :D", output: "positive" },
  //   { input: "we can't have nice things", output: "negative" },
  //   { input: "tempted", output: "negative" },
  //   { input: "happy", output: "positive" },
  //   { input: "good", output: "positive" },
  //   { input: "congratulations", output: "positive" },
  //   { input: "sucks", output: "negative" },
  //   { input: "bad", output: "negative" },
  // ]);

  // console.log(network.run("this is good"));
</script>

<h3>{commentsTitle}</h3>
<div>
  {#if commentsList}
    {@html JSON.parse(JSON.stringify(commentsList)).comments.map(
      (comment) =>
        comment.content +
        ` This comment is: ${
          "LSTM"
          // network.run(comment.content)
        }`
    )}
  {/if}
</div>
