<script>
  import Header from "./Header.svelte";
  import RecentComments from "./RecentComments.svelte";
  import { onMount } from "svelte";

  document.querySelector("body").style.padding = 0;

  let commentsList;

  async function hashchange() {
    commentsList = await fetch(
      `https://node-hnapi.herokuapp.com/item/${1}`
    ).then((result) => result.json());
  }

  onMount(hashchange);
</script>

<Header />
<main>
  <h1>Hello!</h1>

  <RecentComments
    commentsTitle={"A list of most recent comments: "}
    {commentsList}
  />
</main>

<style>
  main {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
