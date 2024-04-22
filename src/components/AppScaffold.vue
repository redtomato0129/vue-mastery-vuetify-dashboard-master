<template>
  <v-app>
    <v-app-bar color="primary" dark app>
      <v-toolbar-title>{{ title }}</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="link in links"
        :key="link.label"
        text
        rounded
        :to="link.url"
        >{{ link.label }}</v-btn
      >
      <v-btn @click="toggleTheme" text rounded>Toggle Theme</v-btn>
    </v-app-bar>
    <v-content><router-view></router-view></v-content>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="link in links"
          :key="link.label"
          :to="link.url"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link.label }}
        </v-btn>
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: "Vuetify Dashboard",
      links: [
        { label: "Home", url: "/" },
        { label: "Login", url: "/login" },
        { label: "Signup", url: "/signup" },
        { label: "Dashboard", url: "/dashboard" },
      ],
    };
  },
  methods: {
    toggleTheme() {
      this.$vuetify.theme.themes.dark.anchor = "#41B883";
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    },
  },
};
</script>

<style scoped></style>
