<script>

	import Mini from './Mini.svelte'

	export let selected1
	export let selected2
	export let quantity
	export let result
	
	const range = (val) => {
		let a = []
		for (let i=0; i<val; i++) {
			a.push(i)
		}
		return a
	}

	$: iter1 = range(result)
	$: iter2 = range(quantity)

	// const size = () => {
	// // setTimeout(()=>{
	// 	let o = document.getElementById("frame");
	// 	if (o) {
	// 		let d = o.getBoundingClientRect();
	// 		console.log(d,[d.width, d.height])
	// 		return [d.clientWidth, d.clientHeight]
	// 	}
	// 	// }, 100);
	// 	//return [200, 200]
	// }

	$: width =  document.body.clientWidth*0.3
	$: height = document.body.clientWidth*0.5

	console.log(width, height)

</script>

<div class="vh-100 bg-light d-flex flex-column justify-content-between align-items-center">
	<div></div>
	<div class="w-75 text-center">
		<h1 style="font-size: 40px">{result}</h1>
		<div class="fs-5">{selected1+" are in "}<br><span class="fw-bold">{quantity}</span>{" "+selected2}</div>
	</div>
	<div class="bg-white border rounded-2 d-flex flex-row justify-content-center align-items-center" style={"width: "+width*2+"px; height:"+height+"px"}>
		<div class="d-flex flex-wrap bg-warning justify-content-center align-items-center" style={"width: "+width+"px; height:"+height+"px"}>
		{#each iter2 as val}
			<Mini selected={selected2} nb={quantity} frameWidth={width} frameHeight={height}/>
		{/each}
		</div>
		<div class="d-flex flex-wrap bg-success justify-content-center align-items-center" style={"width: "+width+"px; height:"+height+"px"}>
		{#each iter1 as val}
			<Mini selected={selected1} nb={result} frameWidth={width} frameHeight={height}/>
		{/each}
		</div>
	</div>
	<div class="border p-3 rounded-3 bg-body-secondary">
		<h6>Calculation details</h6>
		<ul>
			<li>{selected1}</li>
			<li>{selected2}</li>
			<li></li>
		</ul>
	</div>
	<div></div>
</div>