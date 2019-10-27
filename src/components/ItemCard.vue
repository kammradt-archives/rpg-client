<template>
  <v-card :disabled="dontHaveItem">
    <p v-text="itemName" class="font-weight-medium text-center headline mb-0" />
    <v-row>
      <v-col cols="12" sm="6" class="pt-3 text-center">
        <v-icon large left color="red" v-text="'mdi-sword'" />
        <span v-text="itemDamage" class="font-weight-light headline" />
      </v-col>

      <v-col cols="12" sm="6" class="pt-3 text-center">
        <v-icon large left color="blue" v-text="'mdi-shield-outline'" />
        <span v-text="itemDefence" class="font-weight-light headline" />
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    item: Object
  },
  computed: {
    dontHaveItem() {
      return this.item == null
    },
    itemName() {
      return this.item ? this.item.name : '​'
    },
    itemDamage() {
      return this.item ? this.item.damage ? this.item.damage : 0 : 0
    },
    itemDefence() {
      return this.item ? this.item.defence : 0
    }
  }
};
</script>