<template>
  <!-- component -->
  <header class="bg-white dark:bg-gray-800">
    <nav class="bg-white dark:bg-gray-800">
      <div class="container p-6 mx-auto">
        <div
          class="flex items-center justify-center mt-6 text-gray-600 capitalize dark:text-gray-300"
        >
          <a
            class="block text-2xl font-bold text-center text-gray-800 dark:text-white lg:text-3xl hover:text-gray-700 dark:hover:text-gray-300"
            href="#"
          >
            <img
              class="mx-auto h-20 w-auto"
              src="../assets/logo.png"
              alt="Workflow"
          /></a>

          <a
            href="/login"
            class="border-b-2 border-transparent hover:text-gray-800 dark:hover:text-gray-200 hover:border-blue-500 mx-1.5 sm:mx-6"
            >Log in</a
          >

          <a
            href="/register"
            class="border-b-2 border-transparent hover:text-gray-800 dark:hover:text-gray-200 hover:border-blue-500 mx-1.5 sm:mx-6"
            >Sign up</a
          >
        </div>
      </div>
    </nav>

    <div
      class="container flex flex-col px-6 py-4 mx-auto space-y-6 md:h-128 md:py-16 md:flex-row md:items-center md:space-x-6"
    >
      <div class="flex flex-col items-center w-full md:flex-row md:w-1/2">
        <div class="max-w-lg md:mx-12 md:order-2">
          <h1
            class="NewSize text-3xl font-medium tracking-wide text-gray-800 dark:text-white md:text-4xl"
          >
            ChatBox
          </h1>
          <h2 class="NewSizeMedium text-gray-800 dark:text-white">
            Stay in touch
          </h2>
          <p class="mt-4 text-gray-600 dark:text-gray-300">
            With ChatBox, chat with your friends and relatives easily and
            frequently, create a group for your team
          </p>
          <div class="mt-6">
            <a
              href="/login"
              class="block px-3 py-2 font-semibold Newbackground text-center text-white transition-colors duration-200 transform bg-blue-500 rounded-md md:inline hover:bg-blue-400"
              >START CHAT</a
            >
          </div>
        </div>
      </div>

      <div class="flex items-center justify-center w-full h-96 md:w-1/2">
        <img
          class="object-cover w-full h-full max-w-2xl rounded-md"
          src="../assets/HomeImg.png"
          alt="apple watch photo"
        />
      </div>
    </div>
  </header>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
  components: {},
};
</script>

<style scoped>
.NewSize {
  font-size: 5rem;
  color: red;
}

.NewSizeMedium {
  font-size: 4rem;
  color: #1685d6;
}
.Newbackground {
  background-color: #1685d6;
}
</style>
