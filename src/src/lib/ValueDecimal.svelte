<script>
    export let value;
    export let min;
    export let max;
    export let precision;

    const handleChange = (e) => {
        if ( !isNaN(e.target.value) ){   
            let formattedValue = parseFloat(e.target.value);
            
            if (precision){
                let power = Math.pow(10, precision)
                let step = Math.trunc(value * power) / power ;
                formattedValue = step;
            }
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
        step="{precision && Math.pow(10, - precision) || 0.1}"
        min="{min ?? ''}"
        max="{max ?? ''}"
        bind:value
        on:change ="{handleChange}"
        class="input input-bordered w-full border-accent"
    />
</div>
