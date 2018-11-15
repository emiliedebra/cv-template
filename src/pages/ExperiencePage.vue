<!-- Experience Page -->

<template>
  <v-container flat class="experience-page width-limit-800" text-xs-left>
    <h3 class="head">Work Experience</h3>
    <experience-text v-for="item in experiences" :key="item.company" :content="item"></experience-text>
    <v-container class="divider-container" pa-0 pt-3 pb-3>
      <v-divider></v-divider>
    </v-container>
    <h3 class="head">Projects</h3>
    <project-text v-for="item in projects" :key="item.company" :content="item"></project-text>
  </v-container>
</template>

<script>
import ExperienceText from '../components/text/ExperienceText.vue';
import ProjectText from '../components/text/ProjectText.vue';
import { projects } from '../data/projects';
import { experiences } from '../data/experiences';

export default {
  name: 'experience',
  data() {
    return {
      projects,
      experiences
    };
  },
  components: {
    ExperienceText,
    ProjectText,
  },
};
</script>
<style>
.experience-page {
  padding-top: 0;
  padding-bottom: 0;
}
</style>
