<template>
    <header :style="{ backgroundColor: backgroundColor }">
      <div class="header-container">
        <div class="logo">
          <img src="../assets/logo (white).svg" alt="Your logo" />
        </div>
        <h1>{{ pageTitle }}</h1>
        <div class="user-info">
          <div class="avatar">
            <span :style="{ backgroundColor: randomColor }"></span>
          </div>
          <span class="full-name" v-if="loggedIn">{{ full_name }}</span>
        </div>
        <button @click="handleLoginLogout">{{ loginLogoutButtonText }}</button>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: "HeaderComponent",
    props: {
      loggedIn: {
        type: Boolean,
        default: false,
      },
    },
    data() {
      return {
        user: {
          name: "Laurenss",
          surname: "Lablaiks",
          code: "IT21046",
        },
        pageTitle: "SQUIDPAGE",
        randomColor: "",
        backgroundColor: "#301934",
        loginLogoutButtonText: "LOGIN",
      };
    },
    computed: {
      full_name() {
        return `${this.user.name} ${this.user.surname}`;
      },
    },
    methods: {
      handleLoginLogout() {
        if (this.loggedIn) {
          if (confirm("Do you want to log out?")) {
            this.loginLogoutButtonText = "LOGIN";
            this.backgroundColor = "#301934";
            this.$emit("logout");
          }
        } else {
          if (confirm("Do you want to log in?")) {
            this.loginLogoutButtonText = "LOGOUT";
            this.backgroundColor = "#800080";
            this.randomColor = randomColor();
            this.$emit("login");
          }
        }
      },
    },
  };
  
  function randomColor() {
    const colors = ["red", "green", "blue", "yellow", "orange", "purple"];
    return colors[Math.floor(Math.random() * colors.length)];
  }
  </script>
  
  <style scoped>
  header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 50px;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header-container {
    display: flex;
    align-items: center;
  }

  .logo {
    transform: scale(0.3);
  }

  .user-info {
    display: flex;
    align-items: center;
  }

  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin-right: 10px;
  }

  .full-name {
    font-size: 16px;
  }

  button {
    background-color: #000;
    color: #fff;
    padding: 10px;
    border-radius: 5px;
  }

  button {
    position: absolute;
    right: 10px;
  }

  h1 {
    margin-left: 10px;
  }
  .full-name {
  position: fixed;
  top: 10px;
  left: 1620px;
  }
</style>


  