<template lang="pug">
  .page
    section.page-contents
      h2.page-ttl BLOG
      p.page-ttl ブログのページ
      ul
        li(v-for="data in datas")
          nuxt-link(:to="'/blog/' + data.id") {{data.title.rendered}}
      button(@click="reCallApi()") API全読み込み
      p(v-if="loading") ローディングしますよ
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const url = "http://localhost/ts_blog/wp//wp-json/wp/v2/posts?per_page=3";
    const datas = await $axios.$get(url);
    return {
      datas
    };
  },
  data() {
    return {
      loading: true
    };
  },
  created() {
    // console.log(this.datas);
  },
  methods: {
    reCallApi() {
      const datas2 = this.$axios
        .$get("http://localhost/ts_blog/wp//wp-json/wp/v2/posts?per_page=20")
        .then(res => {
          this.datas = res;
        })
        .catch(error => {
          console.log("response error", error);
        })
        .finally(() => (this.loading = false));
    }
  }
};
</script>

<style lang="scss" scoped>
li {
  font-size: rem(18);
}
</style>
