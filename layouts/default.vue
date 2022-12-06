<template>
    <div>
        <div class="content">
            <AppMenu />
            <Nuxt />
        </div>
    </div>
</template>
<script>
import AppMenu from '@/components/AppMenu.vue';

export default {
    components: {
        AppMenu
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