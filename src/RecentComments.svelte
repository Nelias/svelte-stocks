<script src="/src/worker.js" type="module">
  import { onMount } from "svelte";
  import brain from "brain.js";
  import * as model from "../models/brainjs-rate-comment-model.json";
 
  export let commentsTitle;
  export let commentsList;

  const network = new brain.recurrent.LSTM();
  network.fromJSON(model);
</script>

<div class="comments-wrapper">
<h3>{commentsTitle}</h3>
<div>
  {#if commentsList}
    <ul>
    {#each commentsList.comments as comment}
      <li>
        {@html comment.content}
        -----> BrainJS thinks this comment is: {network.run(comment.content) || "???"}
      </li>
    {/each}

    </ul>
  {/if}
</div>
</div>


<style>
  .comments-wrapper {
    text-align: left;
    padding: 40px;
  }

  li {
    padding: 8px 4px;
  }
</style>