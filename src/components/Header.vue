<template>
  <nav>
    <img src="../assets/dungeonslayr.png">
  </nav>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss" scoped>
img {
  height: 5rem;
}
nav {
  position: fixed;
  top: 0;
  padding: 1rem 1rem;
  width: 100%;
  display: flex;
  justify-content: center;
  background: rgb(123, 16, 28);
}
</style>
