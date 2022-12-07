<template>
  <main class="container">
    <AppHeader />
    <AppRestaurantInfo :dataSource="fooddata" />
  </main>
</template>

<script>
import { mapState } from 'vuex';

import AppHeader from '@/components/AppHeader.vue';
import AppRestaurantInfo from '@/components/AppRestaurantInfo.vue';

export default {
  computed: {
    ...mapState([
      'fooddata',
    ])
  },
  components: {
    AppHeader, AppRestaurantInfo
  },
}
</script>

<style>

</style>
