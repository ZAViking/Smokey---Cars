<template>
  <div class="login-container">
    <div class="form-container">
      <h1>{{ isLogin ? 'Login' : 'Create Account' }}</h1>
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="username">Username</label>
          <input
            type="text"
            id="username"
            v-model="form.username"
            placeholder="Enter your username"
          />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input
            type="password"
            id="password"
            v-model="form.password"
            placeholder="Enter your password"
          />
        </div>
        <button type="submit" class="submit-button">
          {{ isLogin ? 'Log In' : 'Create Account' }}
        </button>
      </form>
      
      <!-- Button to bypass login and navigate to the dashboard -->
      <button @click="goToDashboard" class="bypass-button">
        Go to Dashboard
      </button>

      <button @click="toggleMode" class="toggle-button">
        {{ isLogin ? 'Create an Account' : 'Already have an account? Log In' }}
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        isLogin: true,
        form: {
          username: '',
          password: '',
        },
      };
    },
    methods: {
      toggleMode() {
        this.isLogin = !this.isLogin;
      },
      handleSubmit() {
        if (this.isLogin) {
          console.log('Logging in with:', this.form);
        } else {
          console.log('Creating account with:', this.form);
        }
      },
      // Method to navigate to the dashboard without login
      goToDashboard() {
        this.$router.push('/dashboard'); // Programmatically navigate to the dashboard
      },
    },
  };
</script>

<style scoped>
  /* Add custom styling here for the bypass button */
  .bypass-button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    width: 100%;
    margin-top: 10px;
  }

  .bypass-button:hover {
    background-color: #45a049;
  }
</style>
