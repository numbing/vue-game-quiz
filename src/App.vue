<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <Header />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
            v-if="loading"
            :currentQuestion="questions[index]"
            :next="next"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header";
import QuestionBox from "./components/QuestionBox";
import axios from "axios";
export default {
  name: "App",
  components: {
    Header,
    QuestionBox,
  },
  data() {
    return {
      questions: [],
      index: 0,
      loading: false,
    };
  },

  methods: {
    next() {
      this.index++;
    },
  },
  mounted: function() {
    axios
      .get(
        "https://opentdb.com/api.php?amount=10&category=27&difficulty=medium&type=multiple"
      )
      .then((response) => {
        this.loading = true;
        this.questions = response.data.results;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
