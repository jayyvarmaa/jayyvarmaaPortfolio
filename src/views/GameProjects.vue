<template>
  <div>
    <h1>Game Development Portfolio</h1>

    <div style="margin-bottom: 30px;">
      Here are some of the games and interactive experiences I've created using Unity, Unreal Engine, and various game development technologies.
      Each project showcases different aspects of game development from procedural generation to AI systems.
    </div>

    <ProjectsList v-bind:projects="projects" />

    <div style="margin-top: 20px;">
      More games and projects available under the <strong>VarmaBrothers</strong> label. 
      Check out my <router-link to="/other-projects">brands and other projects</router-link> for additional work.
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import ProjectsList from "@/components/ProjectsList.vue";
import gameProjectsData from "@/data/GameProjectsData";

export default Vue.extend({
  name: "GameProjects",
  components: {
    ProjectsList,
  },
  data: function () {
    return {
      projects: gameProjectsData,
    };
  },
});
</script>
