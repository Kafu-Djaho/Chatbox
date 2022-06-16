<template>
  <!---
	You may need jQuery
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
	--->

  <div class="all">
    <nav
      id="nav"
      class="fixed inset-x-0 top-0 flex flex-row justify-between z-10 text-white bg-transparent"
    >
      <div>
        <a href="/">
          <img
            class="mx-10 h-20 w-auto"
            src="../assets/logo.png"
            alt="Workflow"
          />
        </a>
      </div>
      <!-- Nav Items Working on Tablet & Bigger Sceen -->
      <div class="p-4 hidden md:flex flex-row justify-between font-bold"></div>

      <!-- Burger Nav Button on Mobile -->
      <div id="nav-open" class="p-4 md:hidden"></div>
    </nav>

    <!-- Opened Nav in Mobile, you can use javascript/jQuery -->
    <div
      id="nav-opened"
      class="fixed left-0 right-0 hidden bg-white mx-2 mt-16 rounded-br rounded-bl shadow z-10"
    ></div>

    <!-- Overlay Background + Center Control -->
    <div
      class="h-screen bg-opacity-50 bg-black flex items-center justify-center"
      style="background: rgba(0, 0, 0, 0.5)"
    >
      <div class="mx-2 text-center">
        <h1
          class="text-gray-100 font-extrabold text-4xl xs:text-5xl md:text-6xl"
        >
          <span class="text-white">Right</span> Place To
        </h1>

        <div class="inline-flex">
          <a href="/user"
            ><button
              class="NewColor p-2 my-5 mx-2 bg-indigo-700 hover:bg-indigo-800 font-bold text-white rounded border-2 border-transparent hover:border-indigo-800 shadow-md transition duration-500 md:text-xl"
            >
              Start a chat
            </button></a
          >
          <a href="/user"
            ><button
              class="NewColor p-2 my-5 mx-2 bg-indigo-700 hover:bg-indigo-800 font-bold text-white rounded border-2 border-transparent hover:border-indigo-800 shadow-md transition duration-500 md:text-xl"
            >
              Create a group
            </button></a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "ChooseView",
  components: {},
};
</script>

<style scoped>
/*
		You may need this for responsive background
		header {
			background: url('bg-425.jpg');
		}

		@media only screen and (min-width:640px) {
			header {
				background: url('bg-640.jpg');
			}
		}

		@media only screen and (min-width:768px) {
			header {
				background: url('bg-768.jpg');
			}
		}

		@media only screen and (min-width:1024px) {
			header {
				background: url('bg-1024.jpg');
			}
		}

		@media only screen and (min-width:1025px) {
			header {
				background: url('bg-max.jpg');
			}
		} */
/* Default background by https://www.pexels.com/@knownasovan */
.all {
  background: url("../assets/ChooseImg.png");
}

.NewColor {
  background-color: #1685d6;
}
</style>
