<template lang="pug">
  header#header
    h1.logo LOGO
    nav.gnav
      ul.gnav-list
        li.gnav-item
          nuxt-link.gnav-link(to="/") HOME
        li.gnav-item
          nuxt-link.gnav-link(to="/work") WORK
        li.gnav-item
          nuxt-link.gnav-link(to="/blog") BLOG
        li.gnav-item
          nuxt-link.gnav-link(to="/contact") CONTACT
</template>

<style lang="scss" scoped>
#header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  .gnav {
    .gnav-list {
      display: flex;
      .gnav-item {
        .gnav-link {
          display: block;
          margin-right: rem(8);
        }
      }
    }
  }
}
</style>
