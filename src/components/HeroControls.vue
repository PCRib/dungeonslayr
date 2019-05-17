<template>
  <div class="heroControls">
    <button class="btn btn-attack" @click="$emit('att-method')">Attack</button>
    <button class="btn btn-spattack" @click="$emit('spatt-method')">S.Attack</button>
    <button class="btn btn-defend" @click="$emit('def-method')">Defend</button>
    <button class="btn btn-potion" @click="$emit('pot-method')">Potion</button>
    <div class="potions">{{potions === 0 ? "0 Potions ": potions + " " + "/ 5"}}</div>
  </div>
</template>

<script>
export default {
  name: "HeroControls",
  data() {
    return {};
  },
  props: ["potions"]
};
</script>

<style lang="scss" scoped>
.heroControls {
  width: 80%;
  height: 5rem;
  padding: 0 1rem;
  background: #f3f3f3;
  border-radius: 5px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  box-shadow: 0px 3px 4px #00000024;
  .potions {
    color: #ff5858;
    font-weight: 700;
  }
}
.btn {
  width: 4rem;
  height: 2rem;
  background: green;
  border-radius: 5px;
  box-shadow: 0px 3px 4px #00000024;
}
.btn-attack {
  background: #6dc16d;
  color: #fffff6;
  font-weight: 700;
}
.btn-spattack {
  background: #69c9ff;
  color: #fffff6;
  font-weight: 700;
}
.btn-defend {
  background: #c1ae6d;
  color: #fffff6;
  font-weight: 700;
}
.btn-potion {
  background: #ff5858;
  color: #fffff6;
  font-weight: 700;
}
</style>
