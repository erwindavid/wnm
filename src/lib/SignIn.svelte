<script>

import Terms from './Terms.svelte'

let agreed = false

function agree(){
	agreed = true
	console.log(agreed)
}
function disagree(){
	agreed = false
}


function validate() {
  //'use strict'

  // Fetch all the forms we want to apply custom Bootstrap validation styles to
  const forms = document.querySelectorAll('.needs-validation')

  // Loop over them and prevent submission
  Array.from(forms).forEach(form => {
    form.addEventListener('submit', event => {
      if (!form.checkValidity()) {
        event.preventDefault()
        event.stopPropagation()
      }
		// alert('validation')
      form.classList.add('was-validated')
    }, false)
  })
}

setTimeout(validate,1)

</script>

<form class="g-3 needs-validation vh-100 d-flex flex-column justify-content-evenly align-items-center" novalidate>
  <h2 class="text-center">Sign up</h2>
  <div>
  <div class="col-md">
    <label for="validationCustom01" class="form-label" value="">User</label>
    <input type="text" class="form-control" id="validationCustom01" required>
    <div class="valid-feedback">
      Looks good!
    </div>
  </div>
  <br>
  <div class="col-md-12">
    <label for="validationCustom02" class="form-label" value="">Password</label>
    <input type="text" class="form-control" id="validationCustom02" required>
    <div class="valid-feedback">
      Looks good!
    </div>
  </div>
  <br>
  <div class="col-md-12">
    <div class="form-check">
	  {#if agreed == true}
      <input class="form-check-input" type="checkbox" value="" id="invalidCheck" required checked on:click={disagree}>
	  {:else}
    <input class="form-check-input" type="checkbox" value="" id="invalidCheck" required on:click={agree}>
	  {/if}
      <label class="form-check-label" for="invalidCheck">
        Agree to <a href="#" data-bs-toggle="modal" data-bs-target="#termsModal"> terms and conditions</a>
      </label>
      <div class="invalid-feedback">
        You must agree before submitting.
      </div>
     </div>
    </div>
  </div>
  <div class="col-md-6">
    <button class="btn btn-primary" type="submit">Sign Up</button>
  </div>
</form>

<Terms
	app="Weights & Measures"
	company="Ed Corp, Ltd"
	location="Veuzoul"
	toprivacy="https://www.google.com/bites"
	agree={agree}
/>
