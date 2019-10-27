<template>
  <v-expansion-panel>
    <v-expansion-panel-header v-text="formattedName" class="font-weight-medium headline" />
    <v-expansion-panel-content>
      <v-row>
        <v-col v-for="item in items" :key="item.id" cols="6" sm="4">
          <ItemCard :item="item" />
        </v-col>
      </v-row>
    </v-expansion-panel-content>
  </v-expansion-panel>
</template>

<script>
import axios from "axios";
import ItemCard from "@/components/ItemCard";

export default {
  name: "AvailableItems",
  props: {
    itemCategory: String
  },
  components: {
    ItemCard
  },
  data: () => ({
    items: []
  }),
  mounted() {
    this.getItems();
  },
  computed: {
    formattedName() {
      return (
        this.itemCategory.charAt(0).toUpperCase() + this.itemCategory.slice(1)
      );
    }
  },
  methods: {
    getItems() {
      let url = `http://localhost:8080/${this.itemCategory}/index`;
      axios.get(url).then(response => {
        this.items = response.data;
      });
    }
  }
};
</script>
