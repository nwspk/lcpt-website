<script>
  import Spinner from "./Spinner.svelte";
</script>

<style>
  .loading {
    width: 100%;
    display:flex;
    flex-direction: row;
    justify-content: center;
  }
</style>

<div class="loading">
  <Spinner black={true} />
</div>
