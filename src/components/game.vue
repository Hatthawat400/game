<template>
  <div>
    <p>
      HP player {{randomNo(1,3)}}
      {{player[randomNo(1,3)-1].name }}
    </p>+รูป
    <hr />
    name = {{aPlayer.name}}
    hp = {{aPlayer.hp}}
    image = {{aPlayer.image}}
    <hr />
    <p>HP Monster 150</p>+รูป
    <button @click="start()">start</button>
    <button @click="Attack()">Attack</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      aPlayer: { name: "", hp: 0, image: "" },

      // ชื่อ player[1].name
      player: [
        { name: "Iron man", hp: 30, image: "a" },
        { name: "Thor", hp: 150, image: "b" },
        { name: "The Hulh", hp: 200, image: "c" },
      ],
      monster: [
        { name: "Thanos", hp: 50 },
        { name: "Loki", hp: 120 },
        { name: "Ultron", hp: 250 },
      ],
    };
  },
  methods: {
    randomNo: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      //1. random player 1-3 -->ชื่อ hp รูป
      this.aplayer = this.player[this.randomNo(1, 3) - 1]; //{....}
      //2. random monster 1-3
    },
  },
  attack: function () {
    //1. player-->monster
    //2  player<--monster
    //3  HP เท่าไหร่แล้ว player.HP <=0 ---> ?
    //4  monster.HP <=0 ---> ?
    //5  END GAME
  },
};
</script>

<style>
</style>
