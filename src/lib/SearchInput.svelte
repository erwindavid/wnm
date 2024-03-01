<script>

	export let list
	export let selected = null
	export let reset
	export let elements

	let selection = list

	$: image = getImage(selected)
	$: reset && clear()

	const search = template => {
		selection = list.reduce((a,c) => {
			if (c.includes(template)) {
				a.push(c)
			}
		return a
		},[])
	}
	const top = e => e && e.slice(0, 4)
	const select = e => selected = e
	const handleChange = e => {select(e) ; search(e)}
	const clear = () => {select(null) ; selection = list}
	const getImage = selected => elements.filter(e=>selected==e.element).map(e=>e.img)

</script>


{#if selected}
<div class="d-flex flex-column align-items-center border rounded-top-2 bg-white">
	<img src={"../src/img/"+image} height="90px" alt="" class="p-2"/>
</div>
{/if}

<div class="dropdown">
	<input class="form-control dropdown-toggle border"
		type='text' 
		on:input={e=>handleChange(e.target.value)}
		on:focus={e=>handleChange(e.target.value)}
		value={selected}
		data-bs-toggle="dropdown"
		placeholder="something to compare"
	/>
	{#if selected}
	<button class="btn btn-close float-end offset" 
		type="button" 
		on:click={clear}>
	</button>
	{/if}
    <ul class="dropdown-menu">
		{#each top(selection) as value}
		<li>
			<a class="dropdown-item" 
				href="#" 
				on:click={e=>select(e.target.innerText)}
			>
			{value}
			</a>
		</li>
		{/each}
	</ul>
</div>

<style>

  .offset {
  	position: relative;
	top:-28px;
	right: 8px;
	padding-bottom:0;
  }

</style>