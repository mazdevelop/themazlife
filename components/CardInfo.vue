<template>
  <div class="card-info">
    <!-- <p class="title">{{ $props.infos.name }}</p> -->
    <div
      class="wrapper--list-info"
      v-for="(content, i) in infos.contents"
      :key="i"
    >
      <p class="subtitle">{{ content.title }}</p>
      <p class="content">{{ content.content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardInfo",
  props: {
    infos: Object,
  },
};
</script>

<style lang="scss">
.card-info {
  border: 2px dashed #000;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px 0;
  margin: 20px 0;
  @media screen and (min-width: $laptop) {
    padding: 50px 100px;
    width: 100%;
    max-width: 30%;
    display: flex;
    font-display: column;
    justify-content: center;
  }
  .title {
    font-weight: bold;
  }
  .wrapper--list-info {
    .subtitle {
      text-decoration: underline;
      text-align: center;
    }
    .content {
      line-height: 25px;
      text-align: center;
      white-space: inherit;
      @media screen and (min-width: $laptop) {
        white-space: nowrap;
      }
    }
  }
}
</style>