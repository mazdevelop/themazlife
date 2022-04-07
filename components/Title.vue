<template>
  <h1 class="title--components">
    <span
      :class="new_letter ? 'new_letter' : ''"
      v-for="(letter, i) in letters"
      :key="i"
      >{{ letter }}
    </span>
  </h1>
</template>

<script>
export default {
  name: "Title",
  data() {
    return {
      letters: [],
      new_letter: false,
    };
  },
  mounted() {
    this.cutTitle();
  },
  methods: {
    cutTitle() {
      const exit_letters = document.querySelectorAll(".title--components span");
      for (const letter of exit_letters) {
        letter.remove();
      }
      const Title = this.$props.title;
      for (const letter of Title) {
        this.letters.push(letter);
      }
    },
  },
  props: {
    title: {
      default: "Default",
    },
  },
  watch: {
    title(new_value, old_value) {
      this.cutTitle();
      this.new_letter = true;
    },
  },
};
</script>

<style lang="scss">
.title--components {
  overflow: hidden;
  span {
    display: inline-block;
    &.new_letter {
      transform: translateY(-150%);
    }
  }
}
</style>