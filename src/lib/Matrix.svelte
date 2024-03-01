<script>
	
	import Mini from './Mini.svelte'

	let a = 'sugar cube'
	let b = 'bottle of wine'
	let c = 'euro'
	let d = 'us dollar'
	let e = 'chinese yuan'

	export let selected1 = a
	export let selected2 = d
	export let quantity = 1
	export let result = 3

	const range = (val) => {
		let a = []
		for (let i=0; i<val; i++) {
			a.push(i)
		}
		return a
	}

	$: iter1 = range(result)
	$: iter2 = range(quantity)
	$: width = document.body.clientWidth*0.4
	$: height = document.body.clientWidth*0.5


</script>

<div class="d-flex flex-wrap bg-warning justify-content-center align-items-center" style={"width: "+width+"px; height:"+height+"px"}>
{#each iter1 as val}
	<Mini selected={selected1} nb={result} frameWidth={width} frameHeight={height}/>
 {/each}
</div>
