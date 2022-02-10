<template>
  <v-row justify="center">
    <v-col cols="10">
      <v-row>
        <v-col cols="4">
          <v-card v-for="content in contentsList" :key="content.id">
            <h3>{{content.title}}</h3>
            <v-divider />
            <div v-html="content.article" />
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
export default Vue.extend({
  name: "Home",
  data(): {
    contentsList:any[]
  }{
    return{
      contentsList:[]
    }
  },
  async created() {
    const { data } = await axios.get(
      process.env.VUE_APP_CMS_ENDPOINT + `blog`,
      {
        headers: {
          "X-MICROCMS-API-KEY": process.env.VUE_APP_CMS_KEY,
        },
      }
    );
    console.log(data);
    this.contentsList = data.contents;
  },
  methods: {
    async getArticles() {
      const { data } = await axios.get(
        process.env.VUE_APP_CMS_ENDPOINT + `blog/4xdvnmvae`,
        {
          headers: {
            "X-MICROCMS-API-KEY": process.env.VUE_APP_CMS_KEY,
          },
        }
      );
      console.log(data);
    },
  },
});
</script>
