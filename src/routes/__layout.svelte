<script>
   import Header from "../components/Header.svelte";
  import "../app.css";
</script>


<Header />
<div class="container">
  <slot />
</div>


<style>
  .container {
    max-width: 36rem;
    padding: 0 1rem;
    margin: 6rem auto 6rem;
    display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  }
</style>
