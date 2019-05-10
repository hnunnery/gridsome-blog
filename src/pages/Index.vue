<template>
  <Layout>
    <v-container>
      <v-layout row wrap justify-center>
        <v-flex xs12 md10 lg8 mt-2>
          <v-img alt="Example image" :src="imgUrl" width="135" class="mx-auto"></v-img>
          <h1 class="display-2 primary--text my-5 text-xs-center">Gridsome Blog</h1>
          <v-list two-line>
            <v-list-tile v-for="(post, index) in posts" :key="index" @click="onClick(post)">
              <v-list-tile-content>
                <v-list-tile-title>{{ post.node.title }}</v-list-tile-title>
                <v-list-tile-sub-title>{{ post.node.date }}</v-list-tile-sub-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
        </v-flex>
      </v-layout>
    </v-container>
  </Layout>
</template>

<page-query>
query {
  allPost {
    totalCount
    edges {
      node {
        id
        title
        slug
        path
        date
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: "It Finally Works!"
  },
  data() {
    return {
      imgUrl: require("@/favicon.png")
    };
  },
  computed: {
    posts() {
      return this.$page.allPost.edges;
    },
    totalCount() {
      return this.$page.allPost.totalCount;
    }
  },
  methods: {
    onClick(post) {
      this.$router.push({ path: post.node.path });
    }
  }
};
</script>
