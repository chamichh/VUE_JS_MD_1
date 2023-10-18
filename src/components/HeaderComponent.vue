<template>
  <header class="header">
    <img alt="Logo" class="logo" src="path/to/logo.svg" />
    <div class="avatar"></div>
    <div class="username">{{ full_name }}</div>
    <button @click="handleButtonClick">
      {{ loggedIn ? 'LOGOUT' : 'LOGIN' }}
    </button>
  </header>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "Aleksis",
        surname: "Kalis",
        code: "IT21044"
      }
    }
  },
  computed: {
    full_name() {
      return `${this.user.name} ${this.user.surname}`
    }
  },
  methods: {
    handleButtonClick() {
      if (this.loggedIn) {
        const confirmation = confirm("Do you want to log out?")
        if (confirmation) {
          this.$emit("logout")
        }
      } else {
        const confirmation = confirm("Do you want to log in?")
        if (confirmation) {
          this.$emit("login")
        }
      }
    }
  },
  props: {
    loggedIn: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #f2f2f2;
}

.logo {
  width: 100px;
  height: 100px;
}

.avatar {
  width: 50px;
  height: 50px;
  background-color: #ddd;
}

.username {
  font-size: 16px;
}

button {
  background-color: #f2f2f2;
  padding: 10px;
  border-radius: 5px;
  color: #333;
  cursor: pointer;
}
</style>