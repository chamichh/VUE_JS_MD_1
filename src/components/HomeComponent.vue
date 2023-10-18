<template>
  <div class="home">
    <template v-if="!loggedIn">
      <img alt="Logo" class="logo" src="/components/logo_white.svg" />
      <button class="login-btn" @click="handleLoginButtonClick">
        LOGIN
      </button>
    </template>

    <template v-else>
      <nav class="navigation">
        <button @click="changeComponent('home')" :class="{ active: activeComponent === 'home' }">
          HOME
        </button>
        <button @click="changeComponent('about')" :class="{ active: activeComponent === 'about' }">
          ABOUT ME
        </button>
      </nav>

      <div v-if="(activeComponent === 'home')"></div>

      <div v-else class="about-me">
        <h3 class="about-me-info">{{ user.name }}</h3>
        <h3 class="about-me-info">{{ user.surname }}</h3>
        <h3 class="about-me-info">{{ user.code }}</h3>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loggedIn: false,
      activeComponent: "home",
      user: {
        name: "Aleksis",
        surname: "Kalis",
        code: "IT21044",
      },
    };
  },
  methods: {
    handleLoginButtonClick() {
      const confirmation = confirm("Do you want to log in?");
      if (confirmation) {
        this.$emit("login");
      }
    },
    changeComponent(component) {
      this.activeComponent = component;
    },
  },
};

</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.logo {
  width: 100px;
  height: 100px;
  margin-top: 10px;
  margin-left: 10px;
}

.login-btn {
  margin-top: 10px;
  margin-right: 10px;
  background-color: #f2f2f2;
  padding: 10px;
  border-radius: 5px;
  color: #333;
  cursor: pointer;
}

.navigation {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-top: 10px;
  margin-left: 10px;
}

button {
  background-color: #f2f2f2;
  padding: 10px;
  border-radius: 5px;
  color: #333;
  cursor: pointer;
}

button.active {
  font-weight: bold;
}

.about-me {
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 5px;
  margin-top: 10px;
  margin-left: 10px;
}

.about-me-info {
  color: #666;
  font-size: 16px;
  margin-bottom: 5px;
}
</style>
