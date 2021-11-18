<script>
  export let commentsTitle;
  export let commentsList;
</script>

<h3>{commentsTitle}</h3>
<div>
  {#if commentsList}
    {@html JSON.parse(JSON.stringify(commentsList)).comments.map(
      (comment) => comment.content
    )}
  {/if}
</div>
