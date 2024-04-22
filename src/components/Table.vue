<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="items"
      :items-per-page="itemsPerPage"
      class="elevation-1"
      @click:row="onRowClick"
    ></v-data-table>

    <v-snackbar v-model="snackbar" :right="$vuetify.breakpoint.lgAndUp">
      {{ snackbarText }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  methods: {
    onRowClick(data) {
      this.snackbar = true;
      this.snackbarText = `${data.name} attacked with ${data.weapon}`;
    },
  },
  data() {
    return {
      headers: [
        { text: "Name", sortable: true, value: "name" },
        { text: "Weapon", sortable: true, value: "weapon" },
      ],
      items: [
        { name: "Cloud Strife", weapon: "Buster Sword" },
        { name: "Barret Wallace", weapon: "Assault Gun" },
        { name: "Tifa Lockhart", weapon: "Leather Glove" },
        { name: "Aerith Gainsborough", weapon: "Silver Staff" },
        { name: "Red XIII", weapon: "Mythril Clip" },
      ],
      itemsPerPage: 5,
      snackbar: false,
      snackbarText: "",
    };
  },
};
</script>

<style lang="scss" scoped></style>
