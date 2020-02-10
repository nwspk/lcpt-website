<script>
  export let openText = "Read More";
  export let closeText = "Read Less";
  export let isOpen = false;
</script>

<slot name="less" />
{#if isOpen}
  <slot name="more" />
  <button on:click={() => (isOpen = !isOpen)}>{closeText}</button>
{:else}
  <button on:click={() => (isOpen = !isOpen)}>{openText}</button>
{/if}
