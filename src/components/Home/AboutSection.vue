<script setup lang="ts"></script>

<script>
import config from '@/config.vue';
import axios from 'axios';

export default {
  data() {
    return {
      tentang_diri: "",
    }
  },
  async created() {
    const response = await axios.get(`${config.apiTarget}/api/programmers?id_programmers=${this.$route.query.id_programmers}`);
    this.tentang_diri = response.data.tentang_diri
    console.log(this.tentang_diri);
  }
}
</script>

<template>
  <!-- start of about section -->
  <div id="about" class="about-section section" tabindex="-1">
    <div class="container">
      <div class="section-content row">
        <!-- about image -->
        <div class="about-img col-lg-6">
          <div v-clone class="layer">
            <img src="@/assets/about-img.png" alt="User Name" />
          </div>
        </div>

        <!-- text box -->
        <div class="about-text col-lg-6">
          <div class="text-box-inline">
            <span class="subtitle">about me</span>

            <h2>
              Need a Creative Product?
              <br />
              I can Help You!
            </h2>

            <p>
              My name is Muhamad Oskhar Mubarok and I am a student at the State
              Islamic University 🎓 Jakarta in the process being educated
              Computer Science study program😊, with a great passion for
              starting a career in programming world like back-end developer,
              and data scientist.
            </p>

            <div class="btns-container">
              <router-link to="#contact" class="btn btn-primary">
                Hire Me
              </router-link>

              <router-link download to="#" class="btn btn-outline-light">
                Download CV
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- end of about section -->
</template>

<style lang="scss" scoped>
</style>
