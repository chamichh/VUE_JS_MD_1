<template>
  <div class="app">
    <div class="column">
      <NavigationComponent @changeComponent="changeComponent" :activeComponent="activeComponent" />
    </div>
    <div class="column">
      <HeaderComponent @login="handleLogin" @logout="handleLogout" :loggedIn="loggedIn" />
      <div v-if="loggedIn">
        <HomeComponent v-if="activeComponent === 'home'" />
        <AboutMeComponent v-else />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
  },
  data() {
    return {
      loggedIn: false,
      activeComponent: 'home',
    };
  },
  methods: {
    handleLogin() {
      const confirmation = confirm('Do you want to log in?');
      if (confirmation) {
        this.loggedIn = true;
        this.$emit('userLoggedIn');
      }
    },
    handleLogout() {
      const confirmation = confirm('Do you want to log out?');
      if (confirmation) {
        this.loggedIn = false;
        this.$emit('userLoggedOut');
      }
    },
    changeComponent(component) {
      this.activeComponent = component;
    },
  },
};
</script>

<style scoped>
.app {
  display: flex;
}

.column {
  flex: 1;
}
</style>