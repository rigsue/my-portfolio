<template>
	<section id="contact">	
    	<div class="container-fluid justify-content-center text-center my-5" id="contacts">
    		<h2 id="section-titles" class="mt-5 pt-5">Contact</h2>
				  <div class="row">
					<div class="col-md-6 mb-4">
						<!-- <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d61762.5330839029!2d121.06342378804648!3d14.646952920341842!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3397b9a2777a00f9%3A0x6d36c8f429a12fc6!2sMarikina%2C%20Metro%20Manila!5e0!3m2!1sen!2sph!4v1751528385994!5m2!1sen!2sph" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe> -->
						<iframe
						src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d193102.30307894878!2d120.93807694623151!3d14.599512416073491!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3397c8b2c33ef6d7%3A0xffc4ee5878843c0!2sMetro%20Manila%2C%20Philippines!5e0!3m2!1sen!2sph!4v1751529000000!5m2!1sen!2sph" 
						width="600" 
						height="450" 
						style="border:0;" 
						allowfullscreen="" 
						loading="lazy" 
						referrerpolicy="no-referrer-when-downgrade"></iframe>
					</div>
					<div @submit.prevent="submitForm" class=" card col-md-5 mb-3">
						<form class="p-3 text-start">

							<div class="mb-3" id="form-col"></div>

							<div class="mb-3">
								<input type="text" v-model="name" class="form-control" id="formName" placeholder="First Name, M.I., Last Name"/>
							</div>
								
							<div class="mb-3">
								<input type="email" v-model="email" class="form-control" id="formEmail" placeholder="Email"/>
							</div>
								
							<div class="mb-3">
								<textarea v-model="message" class="form-control" id="formMessage" rows="3" placeholder="Message"></textarea>
							</div>

							<div class="d-flex flex-row">
								<div>
									<img src="/images/linkedin-com.svg" width="50"/>
									<img src="/images/gitlab-com.svg" width="50"/>
									<img src="/images/github-com.svg" width="50"/>
								</div>
							</div>

							<div class="text-md-end text-center">
								<button type="submit" class="submit-btn pl-5 pr-5" :disabled="isLoading" id="button-contact">{{ isLoading? "Sending..." : "Submit" }}</button>
						  </div>
						</form>
					</div>
				</div>
			</div>		
		</section>
</template>

<script setup>
	import { ref } from "vue";

	import { Notyf } from "notyf";
	import 'notyf/notyf.min.css';

	const notyf = new Notyf();

	const WEB3FORMS_ACCESS_KEY = "bac7d642-f555-40fc-833f-18d2f0e174eb";

	const subject = "New message from Portfolio Contact Form";

	const name = ref("")
	const email = ref("")
	const message = ref("")
	const isLoading = ref(false);

	const submitForm = async () => {
		isLoading.value = true;
		try {
			const response = await fetch(" https://api.web3forms.com/submit", {
				method: "POST",
				headers: {
					"Content-Type": "application/json",
					Accept: "application/json",
				},
				body: JSON.stringify({
					access_key: WEB3FORMS_ACCESS_KEY,
					subject: subject,
					name: name.value,
					email: email.value,
					message: message.value
				}),
			});
			const result = await response.json();

			if (result.success){
				console.log(result);
				isLoading.value = false;
				notyf.success("Message Sent!")
			}
		} catch (error) {
			console.log(error)
			isLoading.value = false;
			notyf.error("Failed to send message");
		}
	}

</script>