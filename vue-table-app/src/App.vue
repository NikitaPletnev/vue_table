<template>
  <MainContainer />
</template>

<script lang="ts">
import MainContainer from "@/components/MainContainer.vue";
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {
    MainContainer
  }
});
</script>

<style>
/* Global Styles for Dark Theme */
body, html {
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #121212; /* Dark background */
  color: #E4E6E7; /* Light text */
}

/* Text elements */
h1, h2, h3, h4, h5, h6 {
  color: #FFFFFF;
}

p, li, a, span {
  color: #E4E6E7;
}

/* Links */
a {
  color: #BB86FC; /* Slightly purple tint for links */
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

/* Buttons */
button {
  background-color: #333333;
  color: #FFFFFF;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #444444;
}

/* Form Elements */
input, select, textarea {
  background-color: #333333;
  color: #E4E6E7;
  border: 1px solid #555555;
  padding: 10px;
  margin-top: 5px;
}

/* Utility Classes */
.text-center {
  text-align: center;
}

.mt-20 {
  margin-top: 20px;
}

.mb-20 {
  margin-bottom: 20px;
}

/* Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

/* Card Style */
.card {
  background-color: #1E1E1E;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Table styles, if not already defined */
.dynamic-table-container {
  overflow-x: auto;
}

.dynamic-table {
  width: 100%;
  border-collapse: collapse;
}

.dynamic-table th,
.dynamic-table td {
  padding: 10px;
  border: 1px solid #3C3F41;
}

</style>
