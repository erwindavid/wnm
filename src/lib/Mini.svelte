<script>

	const elements = [
		{'element': 'sugar cube', 'img': 'sugar-cube.png'},
		{'element': 'bottle of wine', 'img': 'wine-bottle.png', 'unit': 0.75},
		{'element': 'euro', 'img': 'cur-eur.png'},
		{'element': 'us dollar', 'img': 'cur-usd.png'},
		{'element': 'chinese yuan', 'img': 'cur-cny.png'},
	]

	export let selected
	export let nb
	export let frameWidth
	export let frameHeight

	// const sqrtceil = n =>
	// 	Math.ceil ( Math.sqrt ( n , 2 ) )

	const imgUrl = s => "../src/img/"+elements.find(e=>s==e.element).img

	const imgSize = e => {
		const img = document.createElement('img');
		img.src = e;
		const width = img.naturalWidth;
		const height = img.naturalHeight;
		// console.log(frame, width, height)
		return ([width, height])
	}


	// const toHeight = (e, n) => {
	// 	let c = Math.sqrt(frameWidth*frameHeight/n*e[1]/e[0],2)
	// 	console.log('Height:', frameWidth*frameHeight/n, e[1], e[0], e[1]/e[0], c)
	// 	return c
	// }

	// const toWidth = (e, n) => {
	// 	let c = Math.sqrt(frameWidth*frameHeight/n*e[0]/e[1],2)
	// 	console.log('Width:', frameWidth*frameHeight/n , e[0]/e[1], c)
	// 	return c
	// }

	const arbitrer = (e, n) => {
		let all = []
		for ( let i = 1; i <= n; i++ ) {
			let widthLead = frameWidth / i
			let heightDep = widthLead * ( e[1] / e[0] )
			let widthSurface = frameWidth * frameHeight - ( widthLead * heightDep*n)
			let widthLimit = widthLead * i
			all.push({i: "1/" + i + "W", width: widthLead, height: heightDep, surface: widthSurface, ooo: widthLead * n > frameWidth && Math.ceil( nb / i ) * heightDep > frameHeight})
			let heightLead = frameHeight / i
			let widthDep = heightLead * ( e[0] / e[1] )
			let heightSurface = frameWidth * frameHeight - ( heightLead * widthDep * n )
			let heightLimit = heightLead * i
			all.push({i: "1/" + i + "H", width: widthDep, height: heightLead, surface: heightSurface, ooo: heightLead * n > frameHeight && Math.ceil( nb / i ) * widthDep > frameWidth })
		}
		console.log(all.filter(e=>e.surface>0 && !e.ooo).sort((a,b) => (a.surface > b.surface) ? 1 : ((b.surface > a.surface) ? -1 : 0)))
		return all.filter(e=>e.surface>0 && !e.ooo).sort((a,b) => (a.surface > b.surface) ? 1 : ((b.surface > a.surface) ? -1 : 0))[0]
	}

	// console.log(arbitrer(imgSize(imgUrl(selected)), nb))


// <div class="d-flex flex-wrap align-items-center justify-items-center" style={"width: "+frameWidth/sqrtceil(nb)+"px; height: "+frameHeight/sqrtceil(nb)+"px"}>
// 	<img src={"../src/img/"+image} alt="" class="responsive"/>
// </div>

// <div class="d-flex flex-wrap align-items-center justify-items-center border no" style={"width: "+toWidth(imgSize(imgUrl(selected)), nb)+"px; height: "+toHeight(imgSize(imgUrl(selected)), nb)+"px"}>
// 	<img src={imgUrl(selected)} alt="" class="responsive"/>
// </div>

// <div class="no" style={"width: "+arbitrer(imgSize(imgUrl(selected)), nb).width+"px; height: "+arbitrer(imgSize(imgUrl(selected)), nb).height+"px"}>
// 	<img src={imgUrl(selected)} alt="" class="responsive"/>
// </div>


</script>
{#if selected && nb}
<div style={"width: "+arbitrer(imgSize(imgUrl(selected)), nb).width+"px; height: "+arbitrer(imgSize(imgUrl(selected)), nb).height+"px"}>
	<img src={imgUrl(selected)} alt="" class="responsive"/>
</div>
{/if}
<style>
	.responsive {
		max-width: 100%;
		max-height: 100%;
	}

</style>