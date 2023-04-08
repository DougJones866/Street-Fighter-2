<template>
  <div class="characterBox">
    <h3>{{ selectedCharacter }}</h3>
    <div class="container">
      <div
        v-for="character in characters"
        :key="character.id"
        class="characters"
        :style="characterStyle(character)"
        @mouseover="
          setActive(character);
          selection(character);
        "
        @mouseleave="active = false"
      >
        <img
          :src="`./portraits/${character.img}`"
          @click="selection(character)"
          class="portrait"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      characters: [
        {
          id: 1,
          name: "Ryu",
          img: "ryu.gif",
          active: false,
        },
        {
          id: 2,
          name: "Ken",
          img: "ken.gif",
          active: false,
        },
        {
          id: 3,
          name: "Chun-li",
          img: "chun-li.gif",
          active: false,
        },
        {
          id: 4,
          name: "Cammy",
          img: "cammy.gif",
          active: false,
        },
        {
          id: 5,
          name: "Balrog",
          img: "balrog.gif",
          active: false,
        },
        {
          id: 6,
          name: "Blanka",
          img: "blanka.gif",
          active: false,
        },
        {
          id: 7,
          name: "Deejay",
          img: "deejay.gif",
          active: false,
        },
        {
          id: 8,
          name: "Dhalsim",
          img: "dhalsim.gif",
          active: false,
        },
        {
          id: 9,
          name: "E. Honda",
          img: "ehonda.gif",
          active: false,
        },
        {
          id: 10,
          name: "Feilong",
          img: "feilong.gif",
          active: false,
        },
        {
          id: 11,
          name: "Guile",
          img: "guile.gif",
          active: false,
        },
        {
          id: 12,
          name: "M Bison",
          img: "mbison.gif",
          active: false,
        },
        {
          id: 13,
          name: "Sagat",
          img: "sagat.gif",
          active: false,
        },
        {
          id: 14,
          name: "T Hawk",
          img: "thawk.gif",
          active: false,
        },
        {
          id: 15,
          name: "Vega",
          img: "vega.gif",
          active: false,
        },
        {
          id: 16,
          name: "Zangief",
          img: "zangief.gif",
          active: false,
        },
      ],
      active: false,
      selectedCharacter: null,
    };
  },
  methods: {
    selection(character) {
      this.selectedCharacter = `${character.name}`;
      this.active = true;
      console.log(`${character.name}`);
      console.log(this.active);
    },
    setActive(character) {
      this.characters.forEach((c) => {
        c.active = c === character;
      });
    },
  },
  computed: {
    characterStyle() {
      return (character) => {
        return {
          backgroundColor: !character.active ? "#5683d4" : "red",
        };
      };
    },
  },
};
</script>

<style scoped>
h3 {
  color: orangered;
}
.container {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 0%;
  line-height: 0%;
  width: 0%;
  margin:auto;
  justify-content: center;
  /* position: fixed; */
  left: 0;
  bottom: 5%;
  right: 0;
  box-sizing: border-box;
  padding: 0 10px;
}


.characters {
  background-color: turquoise;
  border: solid lightgray;
  border-style: inset;
}

@media only screen and (min-width: 1000px) {
  .container {
    position: fixed;
  }
}

@media only screen and (max-width: 926px) {
  .container {
    grid-template-columns: repeat(4, 1fr);
  }
  img {
  }
}

@media only screen and (max-width: 500px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
  img {
  }
}
</style>
