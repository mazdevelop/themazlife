<template>
  <div class="project padding">
    <h1>{{ project.title }}</h1>
    <div class="poster-img">
      <img
        class="poster"
        :src="require(`~/assets/images/${project.cover}`)"
        alt=""
      />
    </div>
    <div class="wrapper--content">
      <div class="main">
        <div class="sub">
          <div class="flex columns">
            <h3>رنگ های مورد استفاده</h3>
            <div class="flex">
              <div
                v-for="(color, i) in project.colors"
                :key="i"
                :style="`background-color:${color};`"
                class="theme-dot"
              ></div>
            </div>
            <div class="flex">
              <p v-for="(color, i) in project.colors" :key="i">{{ color }}</p>
            </div>
          </div>
        </div>
        <div class="sub">
          <div class="flex columns">
            <h3>فونت مورد استفاده</h3>
            <div class="tx-center">
              <h2>{{ project.font }}</h2>
            </div>
          </div>
        </div>
      </div>
      <div class="project-detail"></div>
    </div>
    <div class="wrapper-detail">
      <div class="project-desc">
        <h3>توضیحات</h3>
        <p v-for="(text, i) in project.desc" :key="i">{{ text }}</p>
        <div class="links">
          <a
            :href="`${project.link}`"
            target="_blank"
            rel="noopener noreferrer"
          >
            لینک دمو پروژه -
          </a>
          <a
            v-if="project.dribbble"
            :href="`${project.dribbble}`"
            target="_blank"
            rel="noopener noreferrer"
          >
            dribbble لینک -
          </a>
        </div>
      </div>
      <div class="project-thumbnail">
        <img
          class="thumbnail"
          :src="require(`~/assets/images/${project.thumbnail}`)"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
import Project from "../projects.json";
export default {
  name: "Project",
  data() {
    return {
      project_info: Project,
      project: {},
    };
  },
  created() {
    this.getProject();
  },
  methods: {
    getProject() {
      for (const project of this.project_info) {
        project.title === this.$route.params.Project
          ? (this.project = project)
          : "";
      }
    },
  },
};
</script>

<style lang="scss">
.project {
  h1 {
    text-align: center;
    font-size: 2rem;
    @media screen and (min-width: $tablet) {
      font-size: 4rem;
    }
  }
  .poster-img {
    display: flex;
    justify-content: center;
    .poster {
      width: 90%;
      object-fit: cover;
      border-radius: 20px;
      box-shadow: -1px 1px 3px -1px rgba(0, 0, 0, 0.61);
      @media screen and (min-width: $tablet) {
        width: 50%;
        font-size: 4rem;
      }
    }
  }

  .wrapper--content {
    .main {
      display: grid;
      grid-template-columns: 1fr;
      grid-template-areas: "sub";
      gap: 1rem;
      margin: 10px;
      @media screen and (min-width: $tablet) {
        grid-template-columns: 1fr 1fr;
        grid-template-areas: "sub" "sub";
      }
      .sub {
        grid-area: "sub";
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 0 4px;
        .flex {
          display: flex;
          p {
            font-size: 10px;
            margin: 0 2px;
            font-weight: bold;
          }
          h3 {
            text-align: center;
          }
          .tx-center {
            text-align: center;
          }
        }
        .columns {
          flex-direction: column;
        }
        .theme-dot {
          height: 59px;
          width: 59px;
          background-color: black;
          border-radius: 50%;
          margin-right: -20px;
          cursor: pointer;
          border: 2px solid;
        }
      }
    }
  }
  .wrapper-detail {
    display: grid;
    padding: 10px;
    justify-content: center;
    grid-template-columns: 1fr;
    grid-template-areas: "desc " "thumbnail";
    gap: 2em;
    @media screen and (min-width: $tablet) {
      grid-template-columns: 2fr 1fr;
      grid-template-areas: "desc" "thumbnail";
    }
    .project-desc {
      grid-area: "desc";
      display: flex;
      justify-content: center;
      align-items: flex-end;
      flex-direction: column;

      p {
        font-size: 12px;
        text-align: right;
        font-weight: bold;
      }
      a {
        text-decoration: none;
        color: rgb(77, 148, 255);
        font-size: 16px;
        font-weight: bold;
        margin-top: 5px;
        &:hover,
        &:focus {
          text-decoration: none;
          cursor: pointer;
        }
      }
      .links {
        display: flex;
        justify-content: space-around;
        width: 100%;
      }
    }
    .project-thumbnail {
      .thumbnail {
        grid-area: "thumbnail";
        width: 100%;
        height: 370px;
        @media screen and (min-width: $tablet) {
          width: 300px;
          height: 500px;
        }

        object-fit: cover;
        border-radius: 40px;
      }
    }
  }
}
</style>