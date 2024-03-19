<script>
  import { onMount } from "svelte";
  import { goto } from '$app/navigation';
  import Header from "../lib/Header.svelte";

  onMount(() => {
    if (
      (localStorage.getItem("id") &&
        localStorage.getItem("name") &&
        localStorage.getItem("surname")) === null
    ) {
        goto("/login")
    }
  });
</script>
<main class="app">
<Header/>
</main>

<style>
    .app {
        width: 100%;
        display: flex;
        flex-direction: column;
    }

</style>