<script setup lang="ts">
import {
  TestimonialsAnonymousUserAvatar,
  TestimonialsAvatar1,
} from '@/assets/testimonials'
</script>

<script lang="ts">
export default defineComponent({
  data() {
    return {
      // list of testimonials items to loop through it
      testimonialsItems: [
        {
          imgUrl: TestimonialsAvatar1,
          quoteContent: {
            en: 'Website simply provides amazing web development service. Their team is extremely professional and the easiest to meet I have ever worked with. I would recommend Website to anyone.',
            ar: 'محمد يقدم خدمات مذهلة في تطوير الويب، ولديه فريق محترف يجعل التعامل معهم مطمئن للغاية. أوصي بفريقهم للجميع.',
          },

          quoteAuthor: { en: 'Terrell Grimes', ar: 'جابر العواني' },
          jobTitle: { en: 'Photographer', ar: 'مصور فوتوغرافي' },
        },
      ],
    }
  },
})
</script>

<template>
  <!-- start of testimonials section -->
  <div id="testimonials" class="testimonials-section section" tabindex="-1">
    <div class="container">
      <div class="section-title">
        <span class="subtitle">testimonials</span>
        <h2 class="title">
          Check What's My Clients
          <br />
          Say About Me
        </h2>
      </div>
    </div>

    <div class="section-content">
      <ul v-staggerdelay="500" class="testimonials-items">
        <li
          v-for="item in testimonialsItems"
          :key="item.quoteAuthor.en"
          class="has-ultimate-tooltip"
          tabindex="0"
        >
          <div class="testimonials-item">
            <div class="testimonial-author-img">
              <img
                :src="item.imgUrl || TestimonialsAnonymousUserAvatar"
                :alt="item.quoteAuthor.en"
              />
            </div>
            <div class="ultimate-tooltip">
              <p>{{ item.quoteContent.en }}</p>
              <h4 class="ultimate-tooltip-title">
                {{ item.quoteAuthor.en }}
              </h4>
              <h5 class="ultimate-tooltip-subtitle">
                {{ item.jobTitle.en }}
              </h5>
            </div>
            <div class="ultimate-tooltip-arrow"></div>
          </div>
        </li>
      </ul>
    </div>
  </div>
  <!-- end of testimonials section -->
</template>

<style lang="scss" scoped></style>
