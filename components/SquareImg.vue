<template>
  <div class="wrapper--square--img">
    <img :src="require(`~/assets/images/${img_path}`)" alt="" />
  </div>
</template>

<script>
export default {
  name: "SquareImg",
  props: {
    img_path: {
      default: "sample-1/sample-poster.jpg",
    },
  },
};
</script>

<style lang="scss">
.wrapper--square--img {
  width: 220px;
  height: 240px;
  overflow: hidden;

  @media screen and (min-width: $tablet) {
    width: 440px;
    height: 480px;
  }
  @media screen and (min-width: $laptop) {
    width: 330px;
    height: 360px;
  }
  img {
    height: 240px;
    width: auto;
    transform: translate(-50%, -50%);
    margin-left: 50%;
    margin-top: 50%;
    object-fit: cover;
    @media screen and (min-width: $tablet) {
      //   width: 720px;
      height: 440px;
    }
  }
}
</style>