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
  </div>
</template>

<script>
export default {
  name: "RegistrationForm",
  data() {
    return {
      firstName: "",
      password: "",
    };
  },
  computed: {
    isValid() {
      return this.firstName.length > 0 && this.password.length >= 8;
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
