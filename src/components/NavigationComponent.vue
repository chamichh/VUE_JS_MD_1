<template>
  <nav class="navigation">
    <button @click="changeComponent('home')" :class="{ active: activeComponent === 'home' }">
      HOME
    </button>
    <button @click="changeComponent('about')" :class="{ active: activeComponent === 'about' }">
      ABOUT ME
    </button>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      activeComponent: "home",
    };
  },
  methods: {
    changeComponent(component) {
      this.activeComponent = component;
      this.$emit("changeComponent", component);
    },
  },
};
</script>

<style scoped>
.navigation {
  display: flex;
  justify-content: space-between;
  align-items: center;
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
</style>
