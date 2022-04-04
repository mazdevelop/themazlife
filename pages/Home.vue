<template>
  <div class="home padding">
    <div class="container--imgs">
      <div
        :class="`wrapper--img img-${index}`"
        v-for="(item, index) in 3"
        :key="index"
      >
        <nuxt-link
          :to="{
            path: `${project_info[project_number].title}`,
            params: { userID: 123 },
          }"
        >
          <img
            :src="
              require(`~/assets/images/${project_info[project_number].poster}`)
            "
            alt=""
            srcset=""
          />
        </nuxt-link>
      </div>
      <div class="wrapper--slider--desktop">
        <p @click="changeImg('previous')">
          <i class="bx bx-left-arrow-alt"></i>
        </p>
        <p @click="changeImg('next')"><i class="bx bx-right-arrow-alt"></i></p>
      </div>
    </div>
    <div class="wrapper--info">
      <p>{{ project_info[project_number].technology }}</p>
      <h1>{{ project_info[project_number].title }}</h1>
    </div>
    <div class="wrapper--slider">
      <p @click="changeImg('previous')"><i class="bx bx-left-arrow-alt"></i></p>
      <p @click="changeImg('next')"><i class="bx bx-right-arrow-alt"></i></p>
    </div>
  </div>
</template>

<script>
import Project from "../projects.json";
export default {
  name: "Home",
  data() {
    return {
      project_info: Project,
      project_number: 0,
    };
  },
  methods: {
    changeImg(value) {
      if (value === "next") {
        this.project_number == this.project_info.length - 1
          ? (this.project_number = 0)
          : this.project_number++;
      } else {
        this.project_number == 0
          ? (this.project_number = this.project_info.length - 1)
          : this.project_number--;
      }
    },
  },
};
</script>

<style lang="scss">
.home {
  display: flex;
  height: calc(100vh - 80px);
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;

  @media screen and (min-width: $laptop) {
    flex-direction: column-reverse;
    justify-content: space-between;
  }

  .container--imgs {
    width: 100%;
    height: 300px;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    .wrapper--slider--desktop {
      display: flex;
      justify-content: space-between;
      width: 100%;
      max-width: 830px;
      display: none;
      @media screen and (min-width: $laptop) {
        display: flex;
      }
      p {
        font-size: 5rem;
        cursor: pointer;
      }
    }
    @media screen and (min-width: $tablet) {
      height: 500px;
    }
    .wrapper--img {
      width: 220px;
      height: 240px;
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      overflow: hidden;

      @media screen and (min-width: $tablet) {
        width: 440px;
        height: 480px;
      }
      @media screen and (min-width: $laptop) {
        width: 330px;
        height: 360px;
      }
      &.img-0 {
        opacity: 0.6;
        transform: translate(-90%, -50%) rotate(-12deg) scale(0.8);
        @media screen and (min-width: $laptop) {
          transform: translate(-95%, -50%) rotate(-12deg) scale(0.8);
        }
      }
      &.img-1 {
        opacity: 0.6;
        transform: translate(-10%, -50%) rotate(12deg) scale(0.8);
        @media screen and (min-width: $laptop) {
          transform: translate(-5%, -50%) rotate(12deg) scale(0.8);
        }
      }
      img {
        width: 600px;
        height: 400px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) scale(0.7);
        position: absolute;
        object-fit: cover;
        @media screen and (min-width: $tablet) {
          width: 720px;
          height: 440px;
        }
      }
    }
  }
  .wrapper--info {
    p {
      text-align: center;
      @media screen and (min-width: $laptop) {
        font-size: 15px;
      }
    }
    h1 {
      @media screen and (min-width: $laptop) {
        font-size: 65px;
        margin: 0 0 10px 0;
        letter-spacing: 8px;
      }
    }
  }
  .wrapper--slider {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin-top: -50px;
    @media screen and (min-width: $laptop) {
      display: none;
    }
    p {
      font-size: 3rem;
    }
  }
}
</style>