<template>
  <div
    class="min-h-full flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8"
  >
    <div class="max-w-md w-full space-y-8">
      <div>
        <a href="/">
          <img
            class="mx-auto h-20 w-auto"
            src="../assets/logo.png"
            alt="Workflow"
          />
        </a>

        <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
          Sign in to your account
        </h2>

        <br />
      </div>
      <div class="mt-8 space-y-6" method="POST">
        <input type="hidden" name="remember" value="true" />
        <div class="rounded-md shadow-sm -space-y-px">
          <div>
            <label for="email-address" class="sr-only">Username</label>
            {{ error.username }}
            <input
              v-model="username"
              id="username"
              name="username"
              type="text"
              autocomplete="username"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
              placeholder="Username"
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
        </div>
        <div class="flex items-center justify-between">
          <div class="text-sm">
            <p>
              You don’t have an account ?
              <a
                href="/register"
                class="font-medium NewColor hover:text-indigo-500"
              >
                Register</a
              >
            </p>
          </div>
        </div>
        <div>
          <a href="/choose">
            <button
              @click="verification()"
              type="submit"
              class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white NewBackground hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
            >
              <span class="absolute left-0 inset-y-0 flex items-center pl-3">
                <!-- Heroicon name: solid/lock-closed -->
              </span>
              Sign in
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
  name: "LoginView",
  props: {},
  data() {
    return {
      username: "",
      email: "",
      password: "",
      confirmpassword: "",
      channels: [],
      show: true,
      error: {
        username: "",
        email: "",
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
    verification() {
      this.error.username =
        this.username === "" ? "The Input field is required" : "";

      this.error.password =
        this.password === "" ? "The Input field is required" : "";

      const login = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          username: this.username,

          password: this.password,
        }),
      };

      fetch("http://localhost:8081/wp-json/jwt-auth/v1/token", login)
        .then((response) => response.json())
        .then((data) => {
          if (!data.message) {
            console.log(data);
            localStorage.setItem("token", data.token);
            this.$router.push("/choose");
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
