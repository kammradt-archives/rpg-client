<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>RESTPG</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text href="https://github.com/kammradt/rpg-client" target="_blank">
        <span class="mr-2">Source Code</span>
        <v-icon large right>mdi-code-tags</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <router-view> </router-view>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data: () => ({
    //
  }),
};
</script>
