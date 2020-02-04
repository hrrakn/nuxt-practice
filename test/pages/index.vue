<template>
  <div class="link">
    <ul>
      <li v-for="li in list">
        <nuxt-link :to="'/page/'+li.id">{{li.title}}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
.link {
  width: 62.5%;
  margin: 0 auto;
  ul {
    list-style: none;
    display: flex;
    justify-content: space-between;
    li {
      a {
        text-decoration: none;
        color: inherit;
      }
      a:hover {
        color: red;
      }
    }
  }
}
</style>
<script>
import axios from "axios";
export default {
  data() {
    return {
      list: []
    };
  },
  asyncData({ params }) {
    return axios
      .get("https://hrrakn.microcms.io/api/v1/blog", {
        headers: {
          "X-API-KEY": "cf25adb1-1c01-45c0-8afd-e89648949a56"
        }
      })
      .then(res => {
        return {
          list: res.data.contents
        };
      });
  }
};
</script>