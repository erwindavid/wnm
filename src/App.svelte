<script>
	import SignIn from './lib/SignIn.svelte'
	import Modal from './lib/Modal.svelte'
	import Home from './lib/Home.svelte'
	import Input from './lib/Input.svelte'
	import Output from './lib/Output.svelte'
	import Matrix from './lib/Matrix.svelte'

	let selected1
	let selected2
	let quantity = 1
	let result

	let home

	function hide(page) {
		page.classList.add('fade')
		page.addEventListener('transitionend',()=> {
			page.classList.add('d-none')
		})
	}

	setTimeout(()=>{hide(home)}, 1000)

</script>

<!--
<div class="container-sm">
	<Home bind:home={home}/>
	<SignIn/> 
</div>
<SignIn/> 

-->
<Matrix />

<!--
<div id="carouselExampleCaptions" class="carousel slide">
  <div class="carousel-indicators">
    <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Input"></button>
    <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1" aria-label="Output"></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
		<Home bind:home={home}/>
		<Input
			bind:selected1={selected1}
			bind:selected2={selected2}
			bind:quantity={quantity}
			bind:result={result}
		/>      
    </div>

    <div class="carousel-item">
		<Output
			bind:selected1={selected1}
			bind:selected2={selected2}
			bind:quantity={quantity}
			bind:result={result}
		/>      
    </div>
  </div>

  <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>

</div>
-->