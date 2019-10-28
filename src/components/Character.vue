<template>
  <v-card elevation="12">
    <p class="display-1 font-weight-light text-center pa-2" v-text="character.name" />
    <hr color="grey" />
    <v-card-text>
      <v-row>
        <v-col class="mx-auto" cols="4">
          <ItemCard
            :item="character.helmet"
            category="helmet"
            :equipable="false"
            @unequip="unequip"
          />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4">
          <ItemCard
            :item="character.primaryWeapon"
            category="primaryWeapon"
            :equipable="false"
            @unequip="unequip"
          />
        </v-col>
        <v-col cols="4">
          <ItemCard :item="character.armor" category="armor" :equipable="false" @unequip="unequip" />
        </v-col>
        <v-col cols="4">
          <ItemCard
            :item="character.secondaryWeapon"
            category="secondaryWeapon"
            :equipable="false"
            @unequip="unequip"
          />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4" offset="4">
          <ItemCard :item="character.pants" category="pants" :equipable="false" @unequip="unequip" />
        </v-col>
        <v-col cols="4">
          <ItemCard
            :item="character.gloves"
            category="gloves"
            :equipable="false"
            @unequip="unequip"
          />
        </v-col>
      </v-row>
      <v-row>
        <v-col class="mx-auto" cols="4">
          <ItemCard :item="character.shoes" category="shoes" :equipable="false" @unequip="unequip" />
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import axios from "axios";
import ItemCard from "./ItemCard";

export default {
  name: "Character",
  props: {
    id: Number,
    newItem: Object 
  },
  components: { ItemCard },
  data() {
    return {
      character: {}
    }
  },
  mounted() {
    this.getCharacter()
  },
  watch: {
    newItem() {
      let url = `http://localhost:8080/character/update`;
      this.character[this.newItem.category] = this.newItem.id;
      axios.put(url, this.character).then(() => {
        this.getCharacter()
      });
    },
    id() {
      this.getCharacter()
    }
  },
  methods: {
    unequip(e) {
      let url = `http://localhost:8080/character/update`;
      this.character[e.category] = null;
      axios.put(url, this.character).then(() => {
        this.$emit("refreshCharacters");
      });
    },
    getCharacter() {
      let url = `http://localhost:8080/character/show/${this.id}`;
      axios.get(url).then(response => {
        this.character = response.data
      })   
    }
  }
};
</script>
