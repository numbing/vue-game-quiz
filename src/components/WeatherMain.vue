<template>
  <div class="weatherMain">
    <h1>I am weather app</h1>
    <p v-if="newCat.length > 0">{{ kittifyName }}</p>
    <input type="text" v-model="newCat" />
    <button @click="addkitty">
      Add
    </button>
    <!-- <button :disabled="email.length < 2"> submit </button> -->
    <ul>
      <li :key="cat.name" v-for="cat in cats">{{ cat.name | capitalize }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "WeatherMain",
  data: () => ({
    newCat: "",
    cats: [
      { name: "asda" },
      { name: "dasdaww" },
      { name: "dasdasd" },
      { name: "sadsad" },
    ],
  }),
  methods: {
    addkitty: function() {
      this.cats.push({ name: this.newCat });
      this.newCat = "";
    },
  },
  filters: {
    capitalize: function(value) {
      return value.toUpperCase();
    },
  },
  computed: {
    kittifyName: function() {
      return this.newCat + "y";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
