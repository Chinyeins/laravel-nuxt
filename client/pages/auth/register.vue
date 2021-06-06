<template>
  <div class="container mx-auto mt-16 sm:px-6 lg:px-8">
    <form
      @submit.prevent="register"
      class="bg-teal-500 rounded mx-auto px-6 py-6 w-1/2"
      ref="registerform"
    >
      <div class="flex flex-col">
        <label for="name" class="text-white text-xl">Name</label>
        <input
          type="text"
          v-model="form.name"
          class="px-2 py-1 rounded"
          placeholder="Name"
        />
        <span class="text-red-200 italic" v-if="errors.name">{{
          errors.name[0]
        }}</span>
      </div>
      <div class="flex flex-col mt-3">
        <label for="username" class="text-white text-xl">Username</label>
        <input
          type="text"
          v-model="form.username"
          class="px-2 py-1 rounded"
          placeholder="Username"
        />
        <span class="text-red-200 italic" v-if="errors.username">{{
          errors.username[0]
        }}</span>
      </div>
      <div class="flex flex-col mt-3">
        <label for="email" class="text-white text-xl">Email</label>
        <input
          type="email"
          v-model="form.email"
          class="px-2 py-1 rounded"
          placeholder="Email"
        />
        <span class="text-red-200 italic" v-if="errors.email">{{
          errors.email[0]
        }}</span>
      </div>
      <div class="flex flex-col mt-3">
        <label for="password" class="text-white text-xl">Password</label>
        <input
          type="password"
          v-model="form.password"
          class="px-2 py-1 rounded"
          placeholder="Password"
        />
        <span class="text-red-200 italic" v-if="errors.password">{{
          errors.password[0]
        }}</span>
      </div>
      <div class="flex flex-col mt-3">
        <label for="password_confirmation" class="text-white text-xl"
          >Confirm Password</label
        >
        <input
          type="password"
          v-model="form.password_confirmation"
          class="px-2 py-1 rounded"
          placeholder="Confirm Password"
        />
      </div>
      <div class="text-center mt-3">
        <teal-button type="submit">Register</teal-button>
      </div>
    </form>
  </div>
</template>

<script>
import TealButton from "../../components/TealButton.vue";
import Axios from "axios";

export default {
  components: {
    TealButton,
  },
  data: () => ({
    form: {
      name: "",
      username: "",
      email: "",
      password: "",
      password_confirmation: "",
    },
    errors: [],
  }),
  methods: {
    async login() {
      return this.$auth.loginWith("laravelSanctum", { data: this.form });
    },
    register() {
      this.$axios.$get("api/sanctum/csrf-cookie").then((response) => {
        this.$axios
          .$post("/register", this.form)
          .then((res) => {
            console.log("register successfull",res);
          })
          .catch((err) => {
            let errorData = err.response;
            if ((errorData.status = 422)) {
              this.errors = errorData.data.errors;
              console.error(this.errors);
            }
          });
      });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
