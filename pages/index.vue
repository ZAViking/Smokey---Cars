<script>
    import CarLogin from '~/components/CarLogin.vue';
    export default {
        name: 'CarLogin', // Component name should be defined
    };
</script>
  

<style scoped>
    h1 {
    font-family: 'FarAwayGalaxy', sans-serif;
    }

    /* @import url("animate.css"); */
    /* @import url("main.css"); */
</style>

<style lang="scss">
    @use "~/assets/scss/main.scss";
</style>

<template>
    <div>
      <CarLogin />
    </div>
</template>