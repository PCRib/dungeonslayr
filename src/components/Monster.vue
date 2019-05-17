<template>
  <div class="monster">
    <div class="monsterName">Lvl {{monster.level}} {{monster.name}}</div>
    <div :style="{width: healthBar + '%'}" class="health"></div>
    <p>{{monster.currentHP}} / {{monster.maxHP}}</p>
    <p></p>
  </div>
</template>

<script>
export default {
  name: "Monster",
  props: ["monster"],
  data() {
    return {};
  },
  computed: {
    healthBar() {
      return (this.monster.currentHP / this.monster.maxHP) * 100;
    }
  }
};
</script>

<style lang="scss" scoped>
.monster {
  width: 80%;
  height: 5rem;
  padding: 1rem 1rem;
  background: #fffff6;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  box-shadow: 0px 3px 4px #00000024;
  .health {
    height: 1rem;
    width: 100%;
    background: greenyellow;
    transition: width 500ms;
  }
}
</style>
