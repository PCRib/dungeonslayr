<template>
  <div @click="$emit('toggle-btn')">
    <p>{{loot.name}}</p>
  </div>
</template>

<script>
export default {
  name: "LootTable",
  props: ["loot"],
  created() {
    console.log(this.$props);
  }
};
</script>

<style lang="scss" scoped>
p {
  color: black;
  cursor: pointer;
}
</style>
