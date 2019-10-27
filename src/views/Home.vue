<template>
  <v-container fluid>
    <v-row>
      
      <v-col cols="12" md="6">
        <Character :character="characters[0]" />
      </v-col>

      <v-col>
        <v-expansion-panels>
          <AvailableItems
            v-for="equipamentCategory in equipaments"
            :key="equipamentCategory"
            :itemCategory="equipamentCategory"
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
    }
  }
};
</script>
