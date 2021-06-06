<template>
  <div class="bg-teal-500 text-white text-md">
    <nav class="container flex justify-between items-center mx-auto py-5">
      <span class="font-semibold text-2x1"> Good Wave Lab </span>
      <div class="space-x-2">
        <template>
          <span
            >Salut,
            <nuxt-link to="#" class="hover:text-teal-200"> USERNAME </nuxt-link>
          </span>
          <span>
            <nuxt-link to="#" class="hover:text-teal-200"> FRIENDS </nuxt-link>
          </span>
          <span>
            <nuxt-link to="#" class="hover:text-teal-200"> USERS </nuxt-link>
          </span>
          <span>
            <nuxt-link to="/dashboard" class="hover:text-teal-200">
              DASHBOARD
            </nuxt-link>
            <a href="#" class="">LOGOUT</a>
          </span>
        </template>
        <template>
          <nuxt-link to="/auth/register" class="hover:text-teal-200">
            REGISTER
          </nuxt-link>
          <nuxt-link to="/auth/login" class="hover:text-teal-200">
            LOGIN
          </nuxt-link>
        </template>
      </div>
    </nav>
  </div>
</template>

<script>
export default {};
</script>
