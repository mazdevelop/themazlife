<template>
  <div class="home">
    <div class="wrapper--imgs" @click="changeImg">
      <div class="wrapper--info">
        <h1>{{ project_info[project_number].title }}</h1>
        <p>{{ project_info[project_number].technology }}</p>
      </div>
      <div
        :class="`wrapper--img img-${index}`"
        v-for="(item, index) in 3"
        :key="index"
      >
        <img
          :src="require(`~/assets/images/${project_info[project_number].path}`)"
          alt=""
          srcset=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      project_info: [
        {
          path: "smaple-1.jpg",
          title: "Portfolio",
          technology: "Vue 3 && GSAP",
        },
        {
          path: "smaple-2.jpg",
          title: "Dashboard",
          technology: "Sass",
        },
        {
          path: "smaple-3.jpg",
          title: "Clone Twitter",
          technology: "Vue 2 && Tailwind 3",
        },
      ],
      project_number: 0,
    };
  },
  methods: {
    changeImg() {
      this.project_number == this.project_info.length - 1
        ? (this.project_number = 0)
        : this.project_number++;
    },
  },
};
</script>

<style lang="scss">
.home {
  height: calc(100vh - 80px);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;
  .wrapper--imgs {
    width: 100%;
    height: 100%;
    position: relative;
    .wrapper--info {
      display: grid;
      justify-content: center;

      h1 {
        font-family: "Title";
        margin: 0;
        font-size: 5rem;
      }
      p {
        font-family: "Text";
        font-size: 0.75rem;
        margin: 0;
        text-align: center;
      }
    }
    .wrapper--img {
      width: 30%;
      position: absolute;
      left: 50%;
      top: 55%;
      transform: translate(-50%, -50%);
      &.img-0 {
        opacity: 0.6;
        transform: translate(-90%, -50%) rotate(-12deg) scale(0.8);
      }
      &.img-1 {
        opacity: 0.6;
        transform: translate(-10%, -50%) rotate(12deg) scale(0.8);
      }
      img {
        width: 100%;
      }
    }
  }
}
</style>