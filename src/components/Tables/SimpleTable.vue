<template>
  <div>
    <md-table v-model="users" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Name of vase">{{ item.name }}</md-table-cell>
        <md-table-cell md-label="Type">{{ item.type }}</md-table-cell>
        <md-table-cell md-label="Weather Conditions">{{ item.weather }}</md-table-cell>
        <md-table-cell md-label="Life">{{ item.life }}</md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "simple-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      selected: [],
      users: [
        {
          name: "Golden cactus",
          type: "Cactus",
          life: "∞",
          weather: "Drought resistant",
        },
        {
          name: "Aloe Vera",
          type: "Cactus",
          life: "∞",
          weather: "Drought resistant",
        },
        {
          name: "Flowers of stock",
          type: "Plant",
          life: "∞",
          weather: "Low water",
        },
        {
          name: "Primrose",
          type: "Plant",
          life: "∞",
          weather: "Resistant to summer",
        },
        {
          name: "Golden cactus",
          type: "Cactus",
          life: "∞",
          weather: "Drought resistant",
        },
        {
          name: "Flowers of stock",
          type: "Plant",
          life: "∞",
          weather: "Low water",
        },
      ],
    };
  },
};
</script>
