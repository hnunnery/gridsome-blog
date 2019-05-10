<template>
  <BlogLayout>
    <v-container class="markdown-body">
      <v-layout row wrap justify-center>
        <v-flex xs12 md10 lg8 mt-2>
          <g-image :src="$page.post.image" width="600" class="mx-auto" alt="blog"/>
          <h1 class="display-2 red--text text--darken-3 mb-4">{{ this.$page.post.title }}</h1>
          <div v-html="$page.post.content"></div>
        </v-flex>
      </v-layout>
    </v-container>
  </BlogLayout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    content
  }
}
</page-query>


<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title
    };
  }
};
</script>