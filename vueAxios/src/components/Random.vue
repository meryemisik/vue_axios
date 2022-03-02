<template>
  <div>
    <div class="mt-3 randomJoke">
      <b-card-group deck>
        <b-card
          border-variant="info"
          :header="'Joke ID : ' + random.id"
          align="center"
        >
          <img :src="random.icon_url" alt="" />
          <b-card-text>{{ random.value }}</b-card-text>
        </b-card>
      </b-card-group>
    </div>
  </div>
</template>

<script>
import customAxios from "../customAxios";
export default {
  data() {
    return {
      isloading: true,
      random: [],
    };
  },
  created() {
    customAxios.get("random").then((response) => {
      this.random = response.data;
    });
  },
};
</script>

<style>
.randomJoke {
  margin: auto;
  width: 50%;
}
</style>

