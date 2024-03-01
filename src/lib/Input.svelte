<script>

	import SearchInput from './SearchInput.svelte'
	
	export let selected1
	export let selected2
	export let quantity
	export let result

	const combinations = [
		{'element1': 'sugar cube', 'element2': 'bottle of wine', 'combination': 'sugar rate', 'ratio': 10.67},
		{'element1': 'chinese yuan', 'element2': 'us dollar', 'combination': 'change rate', 'ratio':  7.1867},
		{'element1': 'chinese yuan', 'element2': 'euro', 'combination': 'change rate', 'ratio':  7.77387}
	]

	const elements = [
		{'element': 'sugar cube', 'img': 'sugar-cube.png'},
		{'element': 'bottle of wine', 'img': 'wine-bottle.png', 'unit': 0.75},
		{'element': 'euro', 'img': 'cur-eur.png'},
		{'element': 'us dollar', 'img': 'cur-usd.png'},
		{'element': 'chinese yuan', 'img': 'cur-cny.png'},
	]

	let list1 = combinations.reduce((a,c)=>{
		if (!a.includes(c.element1) ){ 
			a.push(c.element1)
		}
		return a
	},[])

	$: list2 = selected1?combinations.filter(e=>selected1==e.element1).map(e=>e.element2):[]

	Array.prototype.merge = function(t2,k) {
		let k1 = k.split('=')[0]
		let k2 = k.includes('=')?k.split('=')[1]:k
		return this.map(itm => ({
	        ...t2.find((item) => (eval('item.'+k1) === eval('itm.'+k2)) && item),
	        ...itm
	    }))
	};



	const increase = e => {
		quantity++
		calculate()
	}

	const decrease = e => {
		quantity--
		calculate()
	}

	const nvl = (val, df) => val ? val : df;

	Array.prototype.renameKeys = function(suffix) {
		return this.reduce( (a,c) => {
			let o = {}	
			Object.entries(c).map(e=>{
				o[e[0]+suffix] = e[1]
			})
			a.push(o)
			return a
		},[])
	};
	

	const calculate = () => {
		result = Math.round(combinations.merge(elements.renameKeys(1),'element1').merge(elements.renameKeys(2), 'element2').filter(e=>selected1==e.element1 && selected2==e.element2).map(e=>e.ratio*quantity*nvl(e.unit2,1)))
		console.log(result)
		// full = combinations.merge(elements.renameKeys(1),'element1').merge(elements.renameKeys(2), 'element2').find(e=>selected1==e.element1 && selected2==e.element2)
		// full['quantity'] = quantity
		// full['calculated'] = full['ratio']*full['quantity']*nvl(full['unit2'],1)
	}

	
</script>


<form class="vh-100 bg-light d-flex flex-column justify-content-between align-items-center" novalidate>
  <div></div>
  <div class="col-md-12 fst-italic">How many ...</div>
  <div class="col-md-12">
	<SearchInput 
		elements={elements}
		list={list1}
		bind:selected={selected1}
		reset={false}
	/>
  </div>
  <div class="col-md-12 fst-italic">... is there in ...</div>
  <div class="col-md-12 d-flex flex-row">
	<input class="form-control w-50"
		type="text" 
		bind:value={quantity}
	/>
	<button class="btn btn-primary" type="button" on:click={increase}>+</button>
	<button class="btn btn-primary" type="button" on:click={decrease}>-</button>
  </div>
  <div class="col-md-12">
	<SearchInput 
		elements={elements}
		list={list2}
		bind:selected={selected2}
		reset={selected1?false:true}
	/>
  </div>
  <div class="col-md-12">
    <button class="btn btn-primary" type="submit" on:click={calculate}>Convert</button>
  </div>
  <div class="bg-primary text-white w-100 text-center">Threaten your friends to use Facebook</div>
</form>
