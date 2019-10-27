<template>
  <v-card elevation="12">
    <p class="display-1 font-weight-light text-center pa-2" v-text="character.name" />
    <hr color="grey" />
    <v-card-text>
      <v-row>
        <v-col class="mx-auto" cols="4">
          <ItemCard :item="character.helmet" />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4">
          <ItemCard :item="character.primaryWeapon" />
        </v-col>
        <v-col cols="4">
          <ItemCard :item="character.armor" />
        </v-col>
        <v-col cols="4">
          <ItemCard :item="character.secondaryWeapon" />
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4" offset="4">
          <ItemCard :item="character.pants" />
        </v-col>
        <v-col cols="4">
          <ItemCard :item="character.gloves" />
        </v-col>
      </v-row>
      <v-row>
        <v-col class="mx-auto" cols="4">
          <ItemCard :item="character.shoes" />
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import ItemCard from "./ItemCard";

export default {
  name: "Character",
  props: {
    character: Object
  },
  components: { ItemCard },
};
</script>
