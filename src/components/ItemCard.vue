<template>
  <v-card :disabled="dontHaveItem">

    <v-row>
      <v-col :cols="equipable ? 12 : 8">
        <p v-text="itemName" class="font-weight-medium text-center headline mb-0" />
      </v-col>
      <v-col v-if="!equipable" cols="4">
        <v-btn  text block @click="unequipItem">
          <v-icon v-if="!dontHaveItem" color="red" v-text="'mdi-alpha-x-circle-outline'" />
        </v-btn>
      </v-col>
    </v-row>


    <v-row>
      <v-col cols="12" sm="6" class="pt-3 text-center">
        <v-icon large left color="red" v-text="'mdi-sword'" />
        <span v-text="itemDamage" class="font-weight-light headline" />
      </v-col>

      <v-col cols="12" sm="6" class="pt-3 text-center">
        <v-icon large left color="blue" v-text="'mdi-shield-half-full'" />
        <span v-text="itemDefence" class="font-weight-light headline" />
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12">
        <v-btn v-if="equipable" text block large @click="equipItem">
          <v-icon large color="green" v-text="'mdi-plus'" />
        </v-btn>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    item: Object,
    category: String,
    equipable: {
      type: Boolean,
      default: true
    }
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
  },
  methods: {
    equipItem() {
      this.$emit('equip', {
        category: this.category,
        id: this.item.id
      })
    },
    unequipItem() {
      this.$emit('unequip', {
        category: this.category
      })
    }
  }
};
</script>