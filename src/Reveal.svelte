<script>
  export let openText = "Read More";
  export let closeText = "Read Less";
  export let isOpen = false;
</script>

<style>
  button {
    background-color: #333;
    border:none;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
    color: #f2f2f2 !important;
    padding: 30px 50px 10px 20px !important;
    display: inline-block;
    margin-bottom: 50px;
  }
</style>

<slot name="less" />
{#if isOpen}
  <slot name="more" />
  <button on:click={() => (isOpen = !isOpen)}>{closeText} &#8593;</button>
{:else}
  <button on:click={() => (isOpen = !isOpen)}>{openText} &#8595;</button>
{/if}
