<script setup lang="ts">
import { gsap } from 'gsap'
import { isDark } from '@/logic'
</script>

<script lang="ts">
export default defineComponent({
  name: 'MotionBlurCursor',

  data() {
    return {
      // cursor elements
      cursorRefs: [] as Element[],

      // cursor pos relative to screen
      cursorX: 0,
      cursorY: 0,

      // scrolled amount relative to document
      scrollX: 0,
      scrollY: 0,
    }
  },

  mounted() {
    if (window.innerWidth >= 992) {
      document.documentElement.setAttribute('data-custom-cursor', '')
      // initialize circle cursor
      this.initMotionBlurCursor()
    }
  },

  methods: {
    // initialize circle cursor
    initMotionBlurCursor() {
      const app = this.$root?.$el
      const collection = document.getElementsByClassName('blur-cursor')
      this.cursorRefs = [...collection]

      app.addEventListener('mousemove', (e: MouseEvent) => {
        this.cursorX = e.clientX
        this.cursorY = e.clientY
        this.moveCursor()
      })
    },

    moveCursor() {
      this.cursorRefs.forEach((val, index) => {
        const posX = this.scrollX + this.cursorX
        const posY = this.scrollY + this.cursorY

        gsap.to(val, {
          duration: 0.05,
          css: { left: posX, top: posY },
          delay: 0 + index / 750,
        })
      })
    },
  },
})
</script>

<template>
  <div class="cursor-canvas">
    <div
      v-for="i in 30"
      :key="i"
      class="blur-cursor"
      :style="isDark ? 'background: #fff1;' : 'background: #0001;'"
    />
  </div>
</template>

<style lang="scss">
html[data-custom-cursor] {
  .blur-cursor {
    opacity: 1;
  }
  * {
    cursor: none;
  }
}

.blur-cursor {
  z-index: 999999;
  position: absolute;
  width: 25px;
  height: 25px;
  top: 50%;
  left: 50%;
  margin: -12.5px 0 0 -12.5px;
  border-radius: 50px;
  opacity: 0;
  user-select: none;
  pointer-events: none;
}

.cursor-canvas {
  position: fixed;
  inset: 0;
  z-index: 999998;
  width: 100vw;
  height: 100vh;
  user-select: none;
  pointer-events: none;
}
</style>
