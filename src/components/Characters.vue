<template>
  <div class="characterBox">
    <!-- Side Portrait -->
    <div class="selectedCharacter">
      <img :src="`./portraits/${characterImg}`" class="bigPortrait" v-if="selectedCharacter" />
      <img :src="`./portraits/ryu.gif`" class="bigPortrait" v-if="!selectedCharacter" />
      <div class="characterName">
        <span class="cName" v-if="selectedCharacter">{{ selectedCharacter }}</span>
        <span class="cName" v-if="!selectedCharacter">Ryu</span>
      </div>
      
    </div>
    <!-- Character Grid -->
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
          name: "Vega",
          img: "vega.gif",
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
          name: "M. Bison",
          img: "bison.gif",
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
      characterImg: null,
    };
  },
  methods: {
    selection(character) {
      if (this.selectedCharacter){
        this.selectedCharacter = "ryu.gif"
      }
      this.selectedCharacter = `${character.name}`;
      this.characterImg = `${character.img}`;
      this.active = true;
      console.log(`${character.name}`);
    },
    setActive(character) {
      this.characters.forEach((c) => {
        c.active = c === character;
      });
    },
  },
  computed: {
    defaultCharacter() {
      if (this.selectedCharacter){
        this.selectedCharacter = "ryu.gif"
      }
    },
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
.cName {
  position: relative;
  bottom: -0.02em;
  
}

.characterBox {
}

.selectedCharacter {
  position: absolute;
  left: 5%;
  bottom: 35%;
  box-sizing: border-box;
  justify-content: left;
  display: flex;
  flex-direction: column;
}
.characterName {
  width: 100%;
  left: 5%;
  background-color: red;
  display: inline-block;
  text-align: center;
  font-size: 6vw;
  background: linear-gradient(
    0deg,
    rgba(240, 149, 2, 1) 13%,
    rgba(242, 244, 34, 1) 65%
  );
  background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-text-stroke: 1px white;
}
.container {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 0%;
  line-height: 0%;
  width: 0%;
  margin: auto;
  justify-content: center;
  /* position: fixed; */
  left: 0;
  bottom: 5%;
  right: 0;
  box-sizing: border-box;
  padding: 0 10px;
}

.bigPortrait {
  height: 350px;
  width: auto;
  background-color: rgba(0, 0, 0, 0.4); 
color: rgba(0, 0, 0, 0.2);
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
  
  .characterBox{
    display:flex;
  }
  .container {
    grid-template-columns: repeat(8, 1fr);
    width: 10%;
  }
  .portrait{
    width: 10vw;
  }
  .bigPortrait {
    width: 15vw;
    height: auto;
  }
  .selectedCharacter {
    bottom: 5%;
  }
  
}

@media only screen and (max-width: 500px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
  .characterBox {
    display:flex;
    flex-direction: row;
  }
  .portrait{
    width: 15vw;
  }
  .characterBox{
    display:flex;
  }
  .bigPortrait {
    width: 25vw;
    height: auto;
  }
  .selectedCharacter {
    top: 5%;
  }
}
</style>
