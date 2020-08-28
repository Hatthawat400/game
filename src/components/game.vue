]<template>
  <div>
    <button v-on:click="start" class="button-a btn btn-outline-warning"  id="start">START</button>
    <button v-on:click="attack" class="button-a btn btn-outline-warning" id="atk">ATTACK</button>
    <button v-on:click="Special" class="button-a btn btn-outline-warning" id="atk">SPECIAL ATTACK</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      player: [
        { name: "Iron man", hp: 400, image: require("../assets/1.png") },
        { name: "Thor", hp: 200, image: require("../assets/2.png") },
        { name: "The Hulk", hp: 300, image: require("../assets/3.png") },
        { name: "Captain America", hp: 260, image: require("../assets/4.png") },
        { name: "Captain Marvel", hp: 250, image: require("../assets/5.png") },
      ],
      monster: [
        { name: "Thanos", hp: 400, image: require("../assets/6.png") },
        { name: "Hela", hp: 240, image: require("../assets/7.png") },
        { name: "Ultron", hp: 194, image: require("../assets/8.png") },
        { name: "Doctor Doom", hp: 160, image: require("../assets/9.png") },
        { name: "Red Skull", hp: 190, image: require("../assets/10.png") },
      ],
    };
  },
  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      //1.random player 1-3
      //2.random monster 1-3
      this.aplayer = this.randomNO(1, 5) - 1;
      this.amonster = this.randomNO(1, 5) - 1;
      //สุ่มค่า player 1-5 --->ชื่อ ค่า hp รูป
      this.name_Player = this.player[this.aplayer].name;
      this.$emit("H_name", this.name_Player);
      console.log("emit", this.name_Player);

      this.hp_Player = this.player[this.aplayer].hp;
      this.$emit("H_hp", this.hp_Player);
      console.log("hp", this.hp_Player);

      this.image_Player= this.player[this.aplayer].image;
      this.$emit("H_image", this.image_Player);
      console.log("im", this.image_Player);

      //สุ่มค่า Monster 1-5 --->ชื่อ ค่า hp รูป
      this.name_monster = this.monster[this.amonster].name;
      console.log("emit", this.name_monster);
      this.$emit("M_name", this.name_monster);
      this.hp_monster = this.monster[this.amonster].hp;
      this.$emit("M_hp", this.hp_monster);
      this.image_monster = this.monster[this.amonster].image;
      this.$emit("M_image", this.image_monster);
    },
    attack: function () {
      //1.player --> monster
      this.atk = this.randomNO(3, 10);
      this.$emit("P_atk", this.atk);
      console.log("Attack :", this.atk);
      //2.player <-- monster
      this.atk = this.randomNO(3, 10);
      this.$emit("M_atk", this.atk);
      console.log("Atk back", this.atk);
      //3.player.HP <=0 ===>!
      //4.monster.HP <=0 ===>!
      //5.END GAME
    },
    Special: function () {
      this.s_atk = this.randomNO(10, 20);
      this.$emit("P_SATK", this.s_atk);
      console.log("Special Attack :", this.s_atk);
      //2.player <-- monster
      this.s_atk = this.randomNO(10, 20);
      this.$emit("M_SPATK", this.s_atk);
      console.log("SPATK back :", this.s_atk);
    },
  },
};
</script>

<style>
.b {
  font-size: 50px;
}

.b{
  background-color: white;
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 10px 3px;
}
.a{
  margin: auto;
  width: 90%;
  height: 650px;
}
</style>