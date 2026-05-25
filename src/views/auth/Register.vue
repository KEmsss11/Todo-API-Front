<script setup lang="ts">
import axios from 'axios';

axios.defaults.withCredentials = true; // Ensure cookies are sent with requests
axios.defaults.withXSRFToken = true; // Enable CSRF protection
axios.defaults.baseURL = 'http://localhost:8000'; // Set    



const register = async () => {
    console.log('Registering user...');
    await axios.get('/sanctum/csrf-cookie'); // Get CSRF token
    try { 
        const response = await axios.post('/api/register', {
            name: 'John Doe',
            email: 'john@doe.com',
            password: 'password',
            password_confirmation: 'password',
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
</template>