<template>
  <div class="container">
    <div class="page">
      <h1>{{title}}</h1>
      <p>{{body}}</p>
    </div>
  </div>
</template>

<style lang="scss">
.container {
  background-color: #333333;
  height: 100px;
}

.page {
  width: 62.5%;
  margin: 0 auto;
  text-align: center;
  color: white;
}
</style>

<script>
import axios from "axios";
export default {
  asyncData({ params }) {
    return axios
      .get("https://hrrakn.microcms.io/api/v1/blog/" + params.page, {
        headers: {
          "X-API-KEY": "cf25adb1-1c01-45c0-8afd-e89648949a56"
        }
      })
      .then(res => {
        console.log(res);

        return {
          title: res.data.title,
          body: res.data.body
        };
      });
  }
};
</script>