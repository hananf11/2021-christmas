<template>
  <div id="wrapper">
    <div id="svg-wrapper">
      <santa-svg height="200px" />
    </div>
    <div id="title" class="card-part">
      <h2>{{ not ? 'Not so' : '' }} Merry Christmas</h2>
    </div>
    <div id="message" class="card-part">
      <slot />
    </div>
    <div id="from" class="card-part">
      {{ credit }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import SantaSvg from '@/static/santa.svg'
import "@fontsource/spirax/400.css"
import "@fontsource/caveat/400.css"

export default Vue.extend({
  components: {
    SantaSvg
  },
  props: ['message', 'not'],
  data: () => {

    return {
      credit: ''
    }
  },
  mounted() {
    const options = [
        'From the amazing ',
        'From ',
        'Made with extreme rush by ',
        'Made with JavaScript by ',
        'The first ever finished project by ',
        'The only un-un-finished project by ',
        'Made in a day by ',
        'Made with magic by ',
        'Cobbled together by ',
        'Made with Hanan by '
      ]
    // credit: options[Math.floor(Math.random() * options.length)] + 'Hanan'
    this.credit = options[Math.floor(Math.random() * options.length)] + 'Hanan'
  }
})
</script>

<style lang="postcss">
body {
  @apply bg-green-700;
}
</style>

<style lang="postcss" scoped>

@keyframes santa-in {
  0% {
    transform: translateY(100%);
    margin-top: -100%;
  }
  100% {
    @apply mt-0;
    transform: translateY(0);
  }
}

svg {
  @apply h-44;
  @apply filter;
  @apply drop-shadow-lg;
  transform: translateY(100%);
  margin-top: -100%;
  animation-name: santa-in;
  animation-iteration-count: 1;
  animation-delay: 500ms;
  animation-duration: 1s;
  animation-timing-function: ease-in;
  animation-fill-mode: forwards;
}

#svg-wrapper {
  max-height: 10.5rem;
  @apply overflow-hidden;
}

#wrapper {
  @apply h-screen w-screen;
  @apply flex flex-col justify-center items-center;
  @apply p-3;
}

.card-part {
  @apply rounded-lg;
  @apply block;
  @apply w-full;
  @apply p-5;
  @apply max-w-sm;
  @apply text-xl;
  font-family: "Caveat";
}

#title {
  @apply bg-red-500;
  @apply text-white text-3xl;
  @apply text-center;
  @apply shadow-xl;
  font-family: "Spirax";
  @apply z-20;
}

#message {
  @apply bg-white;
  @apply -mt-3;
  @apply z-10;
}

#from {
  @apply bg-red-400;
  @apply pb-2;
  @apply -mt-3;
}
</style>
