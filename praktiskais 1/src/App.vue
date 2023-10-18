<template>
  <div class="app-container">
    <HeaderComponent @login="handleLogin" @logout="handleLogout" :loggedIn="loggedIn" />
    <div class="main-content" v-if="loggedIn">
      <NavigationComponent @navigate="navigateTo" />
      <div class="content">
        <HomeComponent v-if="activeComponent === 'home'" />
        <AboutMeComponent v-else-if="activeComponent === 'about'" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import NavigationComponent from '@/components/NavigationComponent.vue'
import HomeComponent from '@/components/HomeComponent.vue'
import AboutMeComponent from '@/components/AboutMeComponent.vue'

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
  },
  data() {
    return {
      activeComponent: 'home', 
      loggedIn: false, 
    }
  },
  methods: {
    handleLogin() {
      if (confirm('Do you want to log in?')) {
        this.loggedIn = true;
        this.$emit('login'); 
      }
    },
    handleLogout() {
      if (confirm('Do you want to log out?')) {
        this.loggedIn = false;
        this.$emit('logout');
      }
    },
    navigateTo(component) {
      this.activeComponent = component;
    },
  },
}
</script>

<style scoped>
.app-container {
  display: flex;
}
.content {
  flex: 1;
  padding: 20px;
}
.h1{
  color:white;
}
</style>
