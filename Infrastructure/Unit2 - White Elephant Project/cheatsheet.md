### Cheatsheet

#### Exercise 4


```
<script>
	let name = 'Bill Dinger';
	let data = [];
  let count = 0;
	async function handleClick() {
        const response = await fetch("https://aws.random.cat/meow");
        const json = await response.json();
        data = json;
				count = count + 1;
		    console.log(data);
		    console.log(count);
	}

</script>

<style>
	.text {
		color: purple;
		font-family: 'Comic Sans MS';
		font-size: 2em;
	}
    .great {
        color: orange;
        font-family: verdana;
        font-size: 4em;
    }
</style>

<h1 class="great">Hello {name}!</h1>
<button class="text" on:click={handleClick}>
	Retrieve Cat
</button>
{#if count > 0}
<p class="purple">
	Your count is {count}
</p>
{/if}
{#if data.file}
<img src={data.file} alt="Cat pictures please"/>
{/if}
```