<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" md="6">
        <Character :id="currentCharacter" :newItem="newItem" />
      </v-col>

      <v-col cols="12" md="6">
        <v-expansion-panels>
          <AvailableItems
            v-for="equipamentCategory in equipaments"
            :key="equipamentCategory"
            :itemCategory="equipamentCategory"
            @equip="equip"
          />
        </v-expansion-panels>
      </v-col>
      <v-speed-dial v-model="fab" top left direction="right" open-on-hover>
        <template v-slot:activator>
          <v-btn v-model="fab" color="blue darken-2" dark fab>
            <v-icon v-if="fab">mdi-close</v-icon>
            <v-icon v-else>mdi-account-circle</v-icon>
          </v-btn>
        </template>
        <v-btn
          fab
          dark
          color="green"
          v-for="character in characters"
          :key="character.id"
          @click="setCurrentCharacter(character.id)"
        >
          <v-icon>{{character.id}}</v-icon>
        </v-btn>
      </v-speed-dial>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
import Character from "@/components/Character";
import AvailableItems from "@/components/AvailableItems";

export default {
  name: "Home",
  components: { Character, AvailableItems },
  data: () => ({
    characters: [],
    currentCharacter: 1,
    newItem: {},
    equipaments: ["helmet", "armor", "pants", "gloves", "shoes", 'weapon'],
    fab: false
  }),
  mounted() {
    this.getCharacters();
  },
  methods: {
    getCharacters() {
      axios.get("http://localhost:8080/character/index").then(response => {
        this.characters = response.data;
      });
    },
    setCurrentCharacter(id) {
      this.currentCharacter = id;
    },
    equip(e) {
      this.newItem = e;
    }
  }
};
</script>
