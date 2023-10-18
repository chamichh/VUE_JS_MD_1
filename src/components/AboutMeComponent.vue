<template>
  <div class="about-me">
    <h1 class="about-me-title">ABOUT ME</h1>
    <div class="about-me-info">
      <span>Name: {{ user.name }}</span>
      <span>Surname: {{ user.surname }}</span>
      <span>Code: {{ user.code }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "Aleksis",
        surname: "Kalis",
        code: "IT21044",
      },
    };
  },
};
</script>

<style scoped>
.about-me {
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 5px;
}

.about-me-title {
  color: #333;
  font-size: 24px;
  margin-bottom: 10px;
}

.about-me-info {
  color: #666;
  font-size: 16px;
  margin-bottom: 5px;
}
</style>
