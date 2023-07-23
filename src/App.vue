<template>
<div>
<h1>{{ message }}</h1>
<label for="first-name">First name </label>
<input v-model="firstName" type="text" id="first-name">
</div>

<div>
<label for="last-name">Last name </label>
<input v-model="lastName" type="text" id="last-name">
</div>

<div>
<label for="dob">Date of birth </label>
<input v-model="dateOfBirth" type="date" id="dob">
</div>

<button @click="proceed">PROCEED</button>

<p v-if="isError" class="error-message"> Please fill in all the fields</p>
<p v-if="numberInput" class="error-message">First name and last name cannot have numbers</p>
</template>

<script setup>
import { ref, computed} from 'vue';


const message = ref('Student Application Page');
const firstName = ref ('');
const lastName = ref ('');
const dateOfBirth = ref ('');
const isError = computed (() => !firstName.value || !lastName.value || !dateOfBirth.value);
const numberInput = computed (() => /\d/.test(firstName.value) || /\d/.test(lastName.value));

const proceed = () => {
if (isError.value || numberInput.value) {
return;
};

alert('Proceeding to Bio Data page...');

console.log('First name:', firstName.value);
console.log('Last name:', lastName.value);
console.log('Date of birth', dateOfBirth.value);

};
</script>

<style>
.error-message {
font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
font-size: 16px;
font-style: italic;
color: red;
}
</style>