<template>
  <v-container fluid>
    <v-row>
      
      <v-col cols="12" md="6">
        <Character
          @refreshCharacters="getCharacters"
          :character="characters[0]"
          :newItem="newItem"
        />
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

    </v-row>
  </v-container>
</template>

<script>
import axios from "axios"
import Character from "@/components/Character"
import AvailableItems from "@/components/AvailableItems"

export default {
  name: "Home",
  components: { Character, AvailableItems},
  data: () => ({
    characters: [],
    newItem: {},
    equipaments: ['helmet', 'armor', 'pants', 'gloves', 'shoes']
  }),
  mounted() {
    this.getCharacters()
  },
  methods: {
    getCharacters() {
      axios.get("http://localhost:8080/character/index").then(response => {
        this.characters = response.data;
      });
    },
    equip(e) {
      this.newItem = e
    }
  }
};
</script>
