<template>
  <div class="card_div">
    <div
      v-for="(category, index) in postList"
      :key="index"
      class="card"
      style="width: 20rem"
    >
      <i style="font-size: 30px; margin-top: 15px" :class="category.icon"></i>
      <div class="card-body">
        <h5 class="card-title">{{ category }}</h5>
        <p class="card-text">
          Prepare yourself to laugh a joke about {{ category }}
        </p>
        <button @click="goToJoke()" class="btn btn-primary">
          To {{ category }} joke
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import customAxios from "../customAxios";

export default {
  data() {
    return {
      postList: [],
    };
  },
  created() {
    customAxios
      .get("/categories")
      .then((response) => {
        this.postList = response.data;
      })
      .catch((e) => console.log(e));
  },
  methods: {
    goToJoke() {
      this.$router.push("/categories/:categoryId");
    },
  },
};
</script>
<style scoped>
.card {
  width: 10rem;
  margin-left: 1rem;
  margin-top: 1rem;
}
.card_div {
  display: flex;
  flex-wrap: wrap;
  margin-left: 2rem;
}
</style>