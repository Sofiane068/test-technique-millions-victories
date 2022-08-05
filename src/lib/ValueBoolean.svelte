<script>
    export let value;
  
    function toggle() {
        value= !value;
        console.log(value);
    }

</script>

{#if value}
	<input id="input" type="checkbox" bind:value={value} checked on:click ="{toggle}" class="toggle toggle-accent toggle-lg"/>
{:else}
    <input id="input" type="checkbox" bind:value={value} on:click ="{toggle}" class="toggle toggle-accent toggle-lg"/>
{/if}