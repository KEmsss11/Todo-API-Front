<script setup lang="ts">
import axios from "axios";

axios.defaults.withCredentials = true; // Ensure cookies are sent with requests
axios.defaults.withXSRFToken = true; // Enable CSRF protection
axios.defaults.baseURL = "http://localhost:8000"; // Set

const register = async () => {
  console.log("Registering user...");
  await axios.get("/sanctum/csrf-cookie"); // Get CSRF token
  try {
    const response = await axios.post("/api/register", {
      name: "John Doe",
      email: "john@doe.com",
      password: "password",
      password_confirmation: "password",
    });
    console.log(response.data);
  } catch (error) {
    console.log(error);
  }
};

register();
</script>
<template>
  <h1>Register</h1>

 
<form class="max-w-sm mx-auto">
   <div class="mb-5">
    <label for="name" class="block mb-2.5 text-sm font-medium text-heading">Your name</label>
    <input type="text" id="name" class="bg-neutral-secondary-medium border border-default-medium text-heading text-sm rounded-base focus:ring-brand focus:border-brand block w-full px-3 py-2.5 shadow-xs placeholder:text-body" placeholder="John Doe"/>
  </div>  
    
  <div class="mb-5">
    <label for="email" class="block mb-2.5 text-sm font-medium text-heading">Your email</label>
    <input type="email" id="email" class="bg-neutral-secondary-medium border border-default-medium text-heading text-sm rounded-base focus:ring-brand focus:border-brand block w-full px-3 py-2.5 shadow-xs placeholder:text-body" placeholder="name@flowbite.com" required />
  </div>
  <div class="mb-5">
    <label for="password" class="block mb-2.5 text-sm font-medium text-heading">Your password</label>
    <input type="password" id="password" class="bg-neutral-secondary-medium border border-default-medium text-heading text-sm rounded-base focus:ring-brand focus:border-brand block w-full px-3 py-2.5 shadow-xs placeholder:text-body" placeholder="••••••••" required />
  </div>
  <div class="mb-5">
    <label for="password_confirmation" class="block mb-2.5 text-sm font-medium text-heading">Confirm your password</label>
    <input type="password" id="password_confirmation" class="bg-neutral-secondary-medium border border-default-medium text-heading text-sm rounded-base focus:ring-brand focus:border-brand block w-full px-3 py-2.5 shadow-xs placeholder:text-body" placeholder="••••••••" required />
  </div>
 
  <button type="submit" class="text-white bg-brand box-border border border-transparent hover:bg-brand-strong focus:ring-4 focus:ring-brand-medium shadow-xs font-medium leading-5 rounded-base text-sm px-4 py-2.5 focus:outline-none">Submit</button>
</form>

</template>
