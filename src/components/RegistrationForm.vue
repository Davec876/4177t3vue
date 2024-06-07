<template>
  <div>
    <h1>Registration Form</h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="firstName">First Name:</label>
        <input type="text" id="firstName" v-model="firstName" required />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />
        <p v-if="password && password.length < 8">
          Password must be at least 8 characters long.
        </p>
      </div>
      <button type="submit" :disabled="!isValid">Submit</button>
    </form>
    <div>
      <h2>Examples from Slide Deck</h2>
      <p>Text Interpolation: {{ greeting }}</p>
      <p>Computed Property: {{ reversedGreeting }}</p>
      <p>
        Conditional Rendering:
        <span v-if="isValid">Form is valid!</span>
        <span v-else>Form is invalid!</span>
      </p>
      <div>
        <h3>List Rendering</h3>
        <ul>
          <li v-for="item in items" :key="item">{{ item }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegistrationForm",
  data() {
    return {
      firstName: "",
      password: "",
      greeting: "Welcome to Vue.js",
      items: ["Item 1", "Item 2", "Item 3"],
    };
  },
  computed: {
    isValid() {
      return this.firstName.length > 0 && this.password.length >= 8;
    },
    reversedGreeting() {
      return this.greeting.split("").reverse().join("");
    },
  },
  methods: {
    submitForm() {
      alert(`Registered with First Name: ${this.firstName}`);
    },
  },
};
</script>

<style scoped>
input {
  display: block;
  margin-bottom: 10px;
  align-items: center;
}
</style>
