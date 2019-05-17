<template>
  <div id="app">
    <!-- <img src="./assets/dungeonslayr.png"> -->
    <Header/>
    <div class="content">
      <h1>{{ msg }} {{monster.level}}</h1>
      <div class="dash">
        <Monster :monster="monster"/>
        <Hero
          :hero="hero"
          v-on:att-method="attackMethod"
          v-on:spatt-method="spattackMethod"
          v-on:def-method="defendMethod"
          v-on:pot-method="potionMethod"
        />
        <NextDungeon v-if="showNext" v-on:next-dungeon="nextDungeon" :monster="monster"/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Monster from "./components/Monster";
import Hero from "./components/Hero";
import NextDungeon from "./components/NextDungeon";

export default {
  name: "app",
  data() {
    return {
      msg: "Dungeon Floor",
      combatLog: [],
      showNext: false,
      monster: { level: 1, name: "Logash", maxHP: 100, currentHP: 100 },
      hero: {
        level: 1,
        name: "Spicy P",
        maxHP: 100,
        currentHP: 100,
        potions: 5
      }
    };
  },
  components: {
    Header,
    Monster,
    Hero,
    NextDungeon
  },
  methods: {
    monsterAttack() {
      const monsterAtt = 7;
      this.hero.currentHP -= monsterAtt;
      return monsterAtt;
    },
    attackMethod() {
      this.monster.currentHP = this.monster.currentHP - 10;
      this.monsterAttack();
      this.combatLog.push("You attacked for 10 Hit Points");
      this.checkWin();
    },
    spattackMethod() {
      this.monster.currentHP = this.monster.currentHP - 20;
      this.monsterAttack();
      this.combatLog.push(
        "You attacked for 20 Hit Points. You can't use this move for 3 turns"
      );
      this.checkWin();
    },
    defendMethod() {
      const monsterAtt = this.monsterAttack();
      this.hero.currentHP += 5;
      this.combatLog.push(
        `You blocked the incoming attack, but this took ${monsterAtt} hitpoint of damage`
      );
    },
    potionMethod() {
      if (this.hero.potions >= 1) {
        if (this.hero.currentHP >= 100) {
          return;
        }
        if (this.hero.currentHP < 100) {
          this.hero.currentHP += 8;
          this.combatLog.push(
            `You healed for 8 Hit Points, ${this.hero.potions}`
          );
          this.hero.potions -= 1;
          this.monsterAttack();
        }
      } else {
        this.combatLog.push("You have no remaining potions");
        return;
      }
    },
    checkWin() {
      console.log("yo");
      if (this.monster.currentHP <= 0) {
        this.showNext = !this.showNext;
        this.newMonster = { ...this.monster };
        this.newMonster.level += 1;
        this.newMonster.maxHP += 20;
        this.newMonster.currentHP = this.newMonster.maxHP;
        this.monster = this.newMonster;
      }
    },
    nextDungeon() {
      this.showNext = !this.showNext;
      this.monster.name = "The Boss";
    }
  },
  computed: {
    nextLvl() {
      if (this.monster.currentHP === 0) {
        return alert("You did it!");
      }
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 100px;
}
body {
  margin: 0;
}
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

p {
  margin: 0;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0rem 5rem;
}
.dash {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  height: 500px;
  width: 100%;
  /* background: linear-gradient(#7b101ccc, #ff634766); */
  background: darkgrey;
  box-shadow: 0px 3px 4px #00000024;
  border-radius: 5px;
}
</style>
