<template>
  <gift :not="true">
    <p class="text-3xl">You just had to break something.</p>
    <p>You managed to create a {{ error.statusCode }}, wow, just wow.</p>
  </gift>
</template>

<script>
  export default {
    props: ['error'],
    layout: 'error' // you can set a custom layout for the error page
  }
</script>
