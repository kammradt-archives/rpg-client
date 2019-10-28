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
    character: Object,
    newItem: Object 
  },
  components: { ItemCard },
  watch: {
    newItem() {
      let url = `http://localhost:8080/character/update`;
      this.character[this.newItem.category] = this.newItem.id;
      axios.put(url, this.character).then(() => {
        this.$emit("refreshCharacters");
      });
    }
  },
  methods: {
    unequip(e) {
      let url = `http://localhost:8080/character/update`;
      this.character[e.category] = null;
      axios.put(url, this.character).then(() => {
        this.$emit("refreshCharacters");
      });
    }
  }
};
</script>
