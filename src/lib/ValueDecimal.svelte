<script>
    export let value;
    export let min;
    export let max;
    export let precision;

    const handleChange = (e) => {
        if ( !isNaN(e.target.value) ){   
            let formattedValue = parseFloat(e.target.value);
            
            if (max && value > max) {
                formattedValue = max;
            }else if(min && value < min){
                formattedValue = min;
            }
            value = formattedValue;
        }
    }
</script>
<div class="tooltip tooltip-right" data-tip= "Max: {max ?? 'none'} |  Min: {min ?? 'none'} | Precision: {precision ?? 'none'}">
    <input
        type="number"
        step=0.001
        min="{min ?? ''}"
        max="{max ?? ''}"
        bind:value
        on:change ="{handleChange}"
        class="input input-bordered w-full border-accent"
    />
</div>
