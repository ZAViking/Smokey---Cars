<template>
    <div>
      <AppHeader />
      <nav />
      <slot />
      <AppFooter />
    </div>
  </template>
  
<script>
  definePageMeta({
    layout: 'custom-layout'
  });


  import Nav from '~/components/Nav.vue';  // Adjust path if necessary
  import AppHeader from '~/components/AppHeader.vue';  // Import the component
  import AppFooter from '~/components/AppFooter.vue';

  export default {
    components: {
      AppHeader,  // Register the component
      AppFooter,
    },
  };
</script>
