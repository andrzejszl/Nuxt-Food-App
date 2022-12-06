<template>
    <div>
        <div class="content">
            <AppMenu />
            <Nuxt />
          </div>
          <AppFooter />
    </div>
</template>
<script>
import AppMenu from '@/components/AppMenu.vue';
import AppFooter from '@/components/AppFooter.vue';

export default {
    components: {
        AppMenu,
        AppFooter
    },
};
</script>

<style>
html {
  font-family: "Mulish", sans-serif;
  font-weight: 300;
  font-size: 16px;
  word-spacing: 1px;
  box-sizing: border-box;
}
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
}
h1, h2, h3, h4 {
  font-family: "Poppins", sans-serif;
  font-weight: 600;
}
</style>