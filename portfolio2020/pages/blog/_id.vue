<template lang="pug">
  .page
    section.page-contents
      h2.page-ttl BLOG
      p.page-ttl {{datas.title.rendered}}
      br
      p(v-html="datas.content.rendered")
</template>

<script>
export default {
  async asyncData({ $axios, route }) {
    const url = "http://localhost/ts_blog/wp//wp-json/wp/v2/posts";
    const datas = await $axios.$get(url + "/" + route.params.id);
    return {
      datas
    };
  },
  created() {
    // console.log(this.datas);
  }
};
</script>

<style lang="scss" scoped>
li {
  font-size: rem(18);
}
</style>
