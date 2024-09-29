<script lang="ts">
   let counter = 0;
    let message = ''
 $: doubled = counter*2;
 $: counterClass = counter%2===0 ? 'red' : 'blue';
 $: {
    if (counter === 10) {
            message = 'You have achived 10!'
    }
 }

 let value = 'Svelte'
 let checked = false;

const ngModel = (event: any) =>  {
    value = event.target.value
 }

 let textarea = ''
</script>

<style lang="scss">
 * {
    font-family: Roboto;
 }
    .red {
        color: red;
    }
    .blue {
        color: blue;
    }
</style>

<pre>{message}</pre>
<h1 class={counterClass}>Counter:{counter} *2 => {doubled}</h1>
<button on:click={()=>counter++}> +1 </button>
<button on:click={()=>counter--}> -1 </button>

<hr/>

<i>{value}</i>
<input value={value} on:input={ngModel}/>
<input  bind:value={value}/>

<hr/>

<input type="checkbox" bind:checked={checked}/>
<pre>{checked}</pre>

<hr/>

<textarea bind:value={textarea}/>
<div style="white-space: pre-wrap">{textarea}</div>