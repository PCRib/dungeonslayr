<template>
  <div class="hero">
    <div class="heroName">Lvl {{hero.level}} Ser {{hero.name}}</div>
    <div :style="{width: healthBar + '%'}" class="health"></div>
    <p>{{hero.currentHP}} / {{hero.maxHP}}</p>
    <div class="controls">
      <HeroControls
        v-on:att-method="$emit('att-method')"
        v-on:spatt-method="$emit('spatt-method')"
        v-on:def-method="$emit('def-method')"
        v-on:pot-method="$emit('pot-method')"
        :potions="hero.potions"
      />
    </div>
  </div>
</template>

<script>
import HeroControls from "./HeroControls";
export default {
  name: "Hero",
  components: {
    HeroControls
  },
  props: ["hero"],
  data() {
    return {};
  },
  computed: {
    healthBar() {
      return (this.hero.currentHP / this.hero.maxHP) * 100;
    }
  }
};
</script>

<style lang="scss" scoped>
.hero {
  width: 80%;
  /* height: 5rem; */
  padding: 1rem 1rem;
  background: #fffff6;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  /* align-items: center; */
  box-shadow: 0px 3px 4px #00000024;
  .health {
    height: 1rem;
    width: 100%;
    background: greenyellow;
    transition: width 500ms;
  }
}
.controls {
  display: flex;
  justify-content: center;
}
</style>
