<template>
  <div id="app" class="game">
    <div>

      <div class="row a">
        <div class="col-md-6">
          <h1>{{he_name}} | HP ; {{he_hp}}</h1>
          <div class="heroTile tile">
            <img :src="h_img" alt class="img-fluid image" :width="he_hp + 'px'" />
          </div>
        </div>
        <div class="col-md-6">
          <h1>{{mon_name}} | HP ; {{mon_hp}}</h1>
          <div class="enemyTile tile">
            <img :src="m_img" alt class="img-fluid image" :width="mon_hp + 'px'" />
          </div>
        </div>
      </div>

      <game
        @H_name="h_name"
        @H_hp="h_hp"
        @H_image="h_image"
        @M_name="m_name"
        @M_hp="m_hp"
        @M_image="m_image"
        @P_atk="p_atk"
        @M_atk="m_atk"
        @P_SATK="p_satk"
        @M_SPATK="m_satk"
      ></game>
    </div>
    <modal
      v-if="he_hp <= 0 && mon_hp > 0 && he_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU LOUSE</h1>
    </modal>
    <modal
      v-if="mon_hp <= 0 && he_hp > 0 && he_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU WIN</h1>
    </modal>
    <modal
      v-if="(he_hp<=0 && mon_hp <= 0 ) && he_name != ''"
      v-bind="reset"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">DRAW</h1>
    </modal>
  </div>
</template>

<script>
import game from "./components/game";
import modal from "./components/over";
export default {
  name: "App",
  components: {
    game,
    modal,
  },
  data: function () {
    return {
      he_name: "",
      mon_name: "",
      he_hp: 0,
      mon_hp: 0,
      attack: 0,
      h_img: "",
      m_img: "",
    };
  },
  methods: {
    //hero
    h_name(value) {
      this.he_name = value;
      console.log("emit", this.he_name);
    },
    h_hp(value) {
      this.he_hp = value;
      console.log("emit", this.he_hp);
    },
    h_image(value) {
      this.h_img = value;
      console.log("emit", this.h_img);
    },
    //Mon
    m_name(value) {
      this.mon_name = value;
    },
    m_hp(value) {
      this.mon_hp = value;
    },
    m_image(value) {
      this.m_img = value;
    },
    //Attack hero
    p_atk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
      console.log("emit", this.mon_hp);
    },
    p_satk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
    },
    //Attack Mon
    m_atk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
    },
    m_satk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
    },
    $reset(value) {
      this.he_name = value;
      this.mon_name = value;
      this.h_img = value;
      this.m_img = value;
    },
    reset(value) {
      this.he_hp = value;
      this.mon_hp = value;
    },
  },
};
</script>

<style>
#app {
  font-family: "Orbitron", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}
.game{
  background-image: url("assets/222.jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}

</style>
