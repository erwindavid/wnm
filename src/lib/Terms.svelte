<script>
	export let app
	export let company
	export let toprivacy
	export let location
	export let agree
</script>

<div class="modal fade" id="termsModal" tabindex="-1" aria-labelledby="termsModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-dialog-scrollable">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">Terms of service</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
		<p>
        Please read these terms and conditions ("terms and conditions", "terms") carefully before using {app} mobile application (“app”, "service") operated by {company} ("us", 'we", "our").</p>
		<h5>Conditions of use</h5>
		<p>By using this app, you certify that you have read and reviewed this Agreement and that you agree to comply with its terms. If you do not want to be bound by the terms of this Agreement, you are advised to stop using the app accordingly. {company} only grants use and access of this app, its products, and its services to those who have accepted its terms.</p>
		<h5>Privacy policy</h5>
		<p>Before you continue using our app, we advise you to read our privacy policy {toprivacy} regarding our user data collection. It will help you better understand our practices.</p>
		<h5>Age restriction</h5>
		<p>You must be at least 18 (eighteen) years of age before you can use this app. By using this app, you warrant that you are at least 18 years of age and you may legally adhere to this Agreement. {company} assumes no responsibility for liabilities related to age misrepresentation.</p>
		<h5>Intellectual property</h5>
		<p>You agree that all materials, products, and services provided on this app are the property of {company}, its affiliates, directors, officers, employees, agents, suppliers, or licensors including all copyrights, trade secrets, trademarks, patents, and other intellectual property. You also agree that you will not reproduce or redistribute the {company}’s intellectual property in any way, including electronic, digital, or new trademark registrations.<br>You grant {company} a royalty-free and non-exclusive license to display, use, copy, transmit, and broadcast the content you upload and publish. For issues regarding intellectual property claims, you should contact the company in order to come to an agreement.</p>
		<h5>User accounts</h5>
		<p>As a user of this app, you may be asked to register with us and provide private information. You are responsible for ensuring the accuracy of this information, and you are responsible for maintaining the safety and security of your identifying information.<br>You are also responsible for all activities that occur under your account or password.<br>If you think there are any possible issues regarding the security of your account on the app, inform us immediately so we may address them accordingly.<br>We reserve all rights to terminate accounts, edit or remove content and cancel orders at our sole discretion.</p>
		<h5>Applicable law</h5>
		<p>By using this app, you agree that the laws of the {location}, without regard to principles of conflict laws, will govern these terms and conditions, or any dispute of any sort that might come between {company} and you, or its business partners and associates.</p>
		<h5>Disputes</h5>
		<p>Any dispute related in any way to your use of this app or to products you purchase from us shall be arbitrated by state or federal court {location} and you consent to exclusive jurisdiction and venue of such courts.</p>
		<h5>Indemnification</h5>
		<p>You agree to indemnify {company }and its affiliates and hold {company} harmless against legal claims and demands that may arise from your use or misuse of our services. We reserve the right to select our own legal counsel.</p>
		<h5>Limitation on liability</h5>
		<p>{company} is not liable for any damages that may occur to you as a result of your misuse of our app. {company} reserves the right to edit, modify, and change this Agreement at any time. We shall let our users know of these changes through electronic mail. This Agreement is an understanding between {company} and the user, and this supersedes and replaces all prior agreements regarding the use of this app.
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" data-bs-dismiss="modal" on:click={agree()}>I agree</button>
      </div>
    </div>
  </div>
</div>