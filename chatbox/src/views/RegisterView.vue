<template>
  <!--
  This example requires Tailwind CSS v2.0+ 
  
  This example requires some changes to your config:
  
  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
  <!--
  This example requires updating your template:

  ```
  <html class="h-full bg-gray-50">
  <body class="h-full">
  ```
-->
  <div
    class="min-h-full flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8"
  >
    <div class="max-w-md w-full space-y-10">
      <div>
        <a href="/">
          <img
            class="mx-auto h-20 w-auto"
            src="../assets/logo.png"
            alt="Workflow"
          />
        </a>

        <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
          Create your account
        </h2>
      </div>
      <div class="mt-8 space-y-6" method="POST">
        <input type="hidden" name="remember" value="true" />
        <div class="rounded-md shadow-sm -space-y-px">
          <div>
            <label for="username" class="sr-only">User name</label>
            {{ error.username }}
            <input
              v-model="username"
              id="username"
              name="username"
              type="username"
              autocomplete="username"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Username"
            />
          </div>
          <br />
          <br />
          <div>
            <label for="email-address" class="sr-only">Email address</label>
            {{ error.email }}
            <input
              v-model="email"
              id="email-address"
              name="email"
              type="email"
              autocomplete="email"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Email address"
            />
          </div>
          <br />
          <br />
          <div>
            <label for="password" class="sr-only">Password</label>
            {{ error.password }}
            <input
              v-model="password"
              id="password"
              name="password"
              type="password"
              autocomplete="current-password"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Password"
            />
          </div>
          <br />
          <br />
          <div>
            <label for="password" class="sr-only">Confirm Password</label>
            {{ error.confirmpassword }}
            <input
              v-model="confirmpassword"
              id="password"
              name="password"
              type="password"
              autocomplete="current-password"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Confirm Password"
            />
          </div>
        </div>
        <div class="flex items-center justify-between">
          <div class="text-sm">
            <p>
              You already have an account ?
              <a
                href="/login"
                class="font-medium NewColor hover:text-indigo-500"
              >
                Login</a
              >
            </p>
          </div>
        </div>
        <div>
          <a href="/login">
            <button
              @click="validation()"
              type="submit"
              class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white NewBackground hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
            >
              <span class="absolute left-0 inset-y-0 flex items-center pl-3">
                <!-- Heroicon name: solid/lock-closed -->
              </span>
              Sign up
            </button>
          </a>
          <br />
          <br />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegisterView2",
  props: {},
  data() {
    return {
      username: "",
      email: "",
      //sex: "",
      password: "",
      confirmpassword: "",
      channels: [],
      show: true,
      error: {
        username: "",
        email: "",
        sex: "",
        password: "",
        confirmpassword: "",
      },
    };
  },
  beforeMount() {},
  /*mounted() {
    this.list();
  },*/
  methods: {
    validation() {
      this.error.username =
        this.username === "" ? "The Input field is required" : "";

      this.error.email = this.email === "" ? "The Input field is required" : "";

      //this.error.sex = this.sex === "" ? "The Input field is required" : "";

      this.error.password =
        this.password === "" ? "The Input field is required" : "";

      this.error.confirmpassword =
        this.confirmpassword === "" ? "The Input field is required" : "";

      const users = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          AuthoriZation:
            "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9sb2NhbGhvc3Q6ODA4MSIsImlhdCI6MTY1NDYxMDA1MywibmJmIjoxNjU0NjEwMDUzLCJleHAiOjE2NTUyMTQ4NTMsImRhdGEiOnsidXNlciI6eyJpZCI6IjEifX19.617PGEBy2o9F7DShra-CLdTDxYBshkr6chEASaRhUy8",
        },
        body: JSON.stringify({
          username: this.username,
          email: this.email,
          password: this.password,
        }),
      };

      fetch("http://localhost:8081/wp-json/wp/v2/users", users)
        .then((response) => response.json())
        .then((data) => {
          if (!data.message) {
            console.log(data);
            localStorage.setItem("token", data.token);
            this.$router.push("/login2");
          }
        })
        .catch((error) => {
          this.errorMessage = error;
          console.error("There was an error!", error);
        });
    },
  },
};
</script>

<style scoped>
.NewColor {
  color: #1685d6;
}
.NewBackground {
  background-color: #1685d6;
}
</style>
