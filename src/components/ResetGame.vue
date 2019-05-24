<template>
  <div class="background">
    <div class="nextDungeon">
      <button class="btn btn-next" @click="$emit('reset-game')">Play Again?</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResetGame",
  props: ["monster", "hero"]
};
</script>

<style lang="scss" scoped>
.background {
  position: absolute;
  width: 100%;
  top: 0;
  height: 5rem;
  background: #8c8c8cab;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.nextDungeon {
  width: 70%;
  height: 10rem;
  padding: 1rem 1rem;
  background: #fffff6;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  box-shadow: 0px 3px 4px #00000024;
}
.btn {
  height: 2rem;
  width: 5rem;
  background: green;
  border-radius: 5px;
  box-shadow: 0px 3px 4px #00000024;
}
.btn-next {
  background: #6dc16d;
  color: #fffff6;
  font-weight: 700;
}
</style>
