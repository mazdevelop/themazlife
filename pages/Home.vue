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
        <p @click="animeImg('previous')">
          <i class="bx bx-left-arrow-alt"></i>
        </p>
        <p @click="animeImg('next')"><i class="bx bx-right-arrow-alt"></i></p>
      </div>
    </div>
    <div class="wrapper--info">
      <p class="technology">{{ project_info[project_number].technology }}</p>
      <Title :title="project_info[project_number].title" />
    </div>
    <div class="wrapper--slider">
      <p @click="animeImg('previous')"><i class="bx bx-left-arrow-alt"></i></p>
      <p @click="animeImg('next')"><i class="bx bx-right-arrow-alt"></i></p>
    </div>
  </div>
</template>

<script>
import Project from "../projects.json";
import gsap from "gsap";
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
    animeImg(value) {
      const img_left = document.querySelector(".wrapper--img.img-0");
      const img_right = document.querySelector(".wrapper--img.img-1");
      const img_center = document.querySelector(".wrapper--img.img-2");
      const duration = 1.4;
      gsap
        .timeline()
        .to([img_left, img_right], {
          duration: duration,
          x: "-50%",
          rotate: "0deg",
          scale: 1,
          ease: "expo.inOut",
        })
        .to(
          [
            img_center.querySelector("a img"),
            img_right.querySelector("a img"),
            img_left.querySelector("a img"),
          ],
          {
            duration: duration,
            stagger: 0.05,
            top: "200%",
            ease: "expo.inOut",
          },
          "start"
        )
        .to(
          ".technology",
          {
            opacity: 0,
            duration: 0.5,
          },
          "start"
        )
        .add(() => this.animeTitleToTop(), "start")
        .add(() => this.changeImg(value))
        .set(
          [
            img_center.querySelector("a img"),
            img_right.querySelector("a img"),
            img_left.querySelector("a img"),
          ],
          {
            top: "-100%",
          }
        )
        .to(
          [
            img_left.querySelector("a img"),
            img_right.querySelector("a img"),
            img_center.querySelector("a img"),
          ],
          {
            duration: duration,
            stagger: 0.05,
            top: "50%",
            ease: "expo.inOut",
          }
        )

        .add(() => this.animeTitleToButton())
        .to(".technology", {
          opacity: 1,
          duration: duration,
          delay: 0.5,
        })
        .to(
          [img_left, img_right],
          {
            scale: 0.8,
          },
          "finish"
        )
        .to(
          img_right,
          {
            rotate: "12deg",
            x: "-20%",
          },
          "finish"
        )
        .to(
          img_left,
          {
            rotate: "-12deg",
            x: "-80%",
          },
          "finish"
        );
    },
    animeTitleToTop() {
      const duration = 1;
      gsap.timeline().to(".title--components span", {
        duration: duration,
        stagger: 0.02,
        skewX: "-40deg",
        skewY: "-40deg",
        y: "150%",
        ease: "expo.inOut",
      });
    },
    animeTitleToButton() {
      const duration = 1;
      gsap
        .timeline()
        .set(".title--components span", {
          skewX: "60deg",
          skewY: "60deg",
        })
        .to(".title--components span", {
          duration: duration,
          stagger: 0.02,
          y: "0%",
          skewX: "0deg",
          skewY: "0deg",
          ease: "expo.inOut",
        });
    },
    test() {
      const duration = 1;
      gsap.timeline().to(".title--components .new_letter", {
        duration: duration,
        stagger: 0.02,
        y: "0%",
        ease: "expo.inOut",
      });
    },
  },
};
</script>

<style lang="scss">
.home {
  display: flex;
  height: 100vh;
  padding-bottom: 0 !important;
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