<script lang="ts">
    import Person from "../components/person.svelte";
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

 let sex = ''

 let select = 'Option 1'

 let people = [{
    id: 1,
    name: 'Alex',
    age: 23
 },

 {
    id: 2,
    name: 'Linus',
    age: 41
 }]
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
<button class:red={counter%2} on:click={()=>counter++}> +1 </button>
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
<hr/>

<pre>You have selected: {select}</pre>
<select bind:value={select}>
    <option value="Option 1">Option 1</option>
    <option value="Option 2">Option 2</option>
    <option value="Option 3">Option 3</option>
</select>

<hr/>

<pre>Your sex is {sex}</pre>
<input type="radio" value="male" bind:group={sex}/>Male
<input type="radio" value="female" bind:group={sex}/>Female

{#if sex === 'male'}
<h1>Congrats, you're a male!</h1>
{:else if sex === 'female'}
<h3>Congrats, female</h3>
{:else}
<pre>Choose your sex</pre>
{/if}

<hr/>

<Person name={'Daniel'}/>

{#each people as person, i (person.id)}
<b>{i}</b><Person name={person.name} person={person}/>
{:else}
<pre>Nothing</pre>
{/each}