<script lang="ts">
export default defineComponent({ name: '404Page' })
</script>

<template>
  <!-- start of 404 page -->
  <div class="not-found-page page">
    <div class="not-found-content">
      <div class="container">
        <div class="not-found-img">
          <img src="@/assets/404.png" alt="404" />
        </div>

        <div class="not-found-text">
          <h2 class="title">Oops! That page can’t be found</h2>

          <p class="desc">
            We're sorry, we couldn't find the page you requested.
          </p>
        </div>
      </div>

      <router-link to="/" class="btn btn-primary m-3">
        Back to Home
      </router-link>

      <button class="btn btn-secondary m-3" @click="$router.back()">
        Go Back
      </button>
    </div>
  </div>
  <!-- end of 404 page -->
</template>

<style lang="scss" scoped></style>
