<template>
  <div id="app" class="app">
    <sidebar-nav />
    <div class="wrapper">
      <router-view/>
    </div>
  </div>
</template>

<script>
import SidebarNav from './components/SidebarNav.vue';

export default {
  components: { SidebarNav },
  data() {
    return {
      loading: false,
    };
  },
};
</script>

<style lang="scss">
@import 'sass/main.scss';
</style>
