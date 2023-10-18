<template>
  <div class="navigation">
    <router-link :to="{ name: 'home' }">
      <button :class="{ active: currentRoute === 'home' }">HOME</button>
    </router-link>
    <router-link :to="{ name: 'about' }">
      <button :class="{ active: currentRoute === 'about' }">ABOUT ME</button>
    </router-link>
  </div>
</template>

<script>
export default {
  props: {
    currentRoute: String,
    loggedIn: Boolean,
  },
  methods: {
    navigateTo(tab) {
      this.$emit('changeTab', tab);
    },
    toggleLogin() {
      if (this.loggedIn) {
        this.$emit('logout');
      } else {
        if (window.confirm('Do you want to log in?')) {
          this.$emit('login');
        }
      }
    }
  }
};
</script>

<style scoped>
.navigation {
  position: fixed;
  top: 60px;
  left: 0;
  display: flex;
  flex-direction: column;
  padding: 15px;
}

button {
  background: none;
  border: none;
  color: white;
  font-size: 16px;
  cursor: pointer;
  margin: 5px 0;
}

button.active {
  font-weight: bold;
  color: #8645E8;
  background: #8645E8 !important;
}
</style>
