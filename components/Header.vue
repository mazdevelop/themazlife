<template>
  <div class="header">
    <div class="wrapper--logo">
      <router-link to="/">
        <h1>MAZ</h1>
      </router-link>
    </div>
    <div class="wrapper--link">
      <router-link v-for="(link, i) in links" :key="i" :to="link.path">{{
        link.name
      }}</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      links: [
        {
          name: "پروژه ها",
          path: "/",
        },
        {
          name: "درباره ی من",
          path: "/About",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 15px;
  box-sizing: border-box;
  height: 80px;
  width: 100%;
  position: absolute;
  z-index: 90;
  @media screen and (min-width: $laptop) {
    padding: $padding;
  }
  .wrapper--link {
    display: flex;

    a {
      margin-left: 10px;
    }
  }
}
</style>