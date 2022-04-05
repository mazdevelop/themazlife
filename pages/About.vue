<template>
  <div class="about padding">
    <div class="wrapper--presentation">
      <h3 class="txt-center">به سایت من خوش آمدید</h3>
      <h1>محسن</h1>
      <h1>علی زاده</h1>
      <div class="wrapper--img">
        <img :src="require(`~/assets/images/about.jpg`)" alt="" />
      </div>
      <div class="flex">
        <p class="presentation--pitch">
          من محسن علیزاده هستم یک فریلنسر در حوزه طراحی وب
          <br />
          گاهی طراحی لوگو و دیجیتال مارکتینگ رو انجام میدم<br />
          بیشتر اوقات صرف ایده پردازی و خواندن مقالات و کتاب هایی میکنم که بتونه
          کار و سبک زندگی ام رو رو شد بده
          <br />
          همیشه چیز هایی جدیدی برای یادگیری وجود داره چیزی که بتونه شما را بهتر
          کنه
          <br />
          من عاشق این چالشم
        </p>
      </div>
    </div>
    <div class="wrapper--info">
      <CardInfo v-for="(info, i) in infos" :key="i" :infos="info" />
    </div>
    <div class="wrapper--contact">
      <h1>نمونه کد های بیشتر در</h1>
      <div class="flex">
        <a href="https://github.com/mazdevelop"
          ><i class="bx bxl-github bx-md"></i
        ></a>
        <a href="https://codepen.io/mazdevelop100"
          ><i class="bx bxl-codepen bx-md"></i
        ></a>
        <a href="https://codesandbox.io/u/mazdevelop"
          ><i class="bx bx-square-rounded bx-md"></i
        ></a>
        <a href="https://stackblitz.com/@mazdevelop"
          ><i
            class="bx bxs-zap bx-flip-horizontal bx-md"
            style="color: #76bae4"
          ></i
        ></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "About",

  data() {
    return {
      infos: [
        {
          name: "مهارت ها",
          contents: [
            {
              title: "Javascript",
              content: "Vue.js , Nuxt.js , Gsap",
            },
            {
              title: " Preprocessors",
              content: "Sass ",
            },
            {
              title: " PHP",
              content: "Laravel ",
            },
            {
              title: " Workflow",
              content: "GIT , NPM ",
            },
            {
              title: " Others",
              content: "PS , AI , Figma  ",
            },
          ],
        },
        {
          name: " راه های ارتباطی",
          contents: [
            {
              title: "Linkedin",
              content: "https://www.linkedin.com/in/mohsen-alizadeh-dev/",
            },
            {
              title: "EMAIL",
              content: "maz.coders@gmail.com",
            },
            {
              title: " INSTAGRAM",
              content: "https://instagram.com/mohsen_alizde_en",
            },
          ],
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.about {
  @media screen and (min-width: $laptop) {
    width: 1250px;
    margin-left: auto;
    margin-right: auto;
    box-sizing: border-box;
  }
  .txt-center {
    text-align: center;
    h1 {
      &:nth-child(0) {
        letter-spacing: 3;
      }
    }
  }
  .wrapper--presentation {
    h1 {
      text-align: center;
      line-height: 30px;
      font-size: 32px;
      @media screen and (min-width: $laptop) {
        font-size: 64px;
      }
    }
    p {
      text-align: right;
    }
    .wrapper--img {
      max-width: 80vw;
      margin: 15px auto;
      display: flex;
      justify-content: center;
      align-items: center;
      img {
        width: 100%;
        @media screen and (min-width: $laptop) {
          width: 50%;
        }
        height: 380px;
        border-radius: 20px;
        object-fit: cover;
      }
    }
    .presentation--pitch {
      font-size: 15px;
      font-weight: bold;
    }
    .flex {
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
  .wrapper--info {
    @media screen and (min-width: $laptop) {
      display: flex;
      justify-content: space-between;
    }
  }
  .wrapper--contact {
    .flex {
      display: flex;
      justify-content: center;
      align-items: center;

      a {
        margin-right: 5px;
        &:hover {
          cursor: pointer;
          transition: transform 0.3s cubic-bezier(0.39, 0.575, 0.565, 1);
          transform: scale(1.2);
        }
      }
    }
    h1,
    a {
      text-align: center;
    }
  }
}
</style>