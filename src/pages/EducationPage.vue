<!-- Education Page -->

<template>
  <v-container flat text-xs-left class="education-page width-limit-500">
    <h3 class="head">Tertiary Education</h3>
    <education-text v-for="item in tertiary" :key="item.title" :content="item"></education-text>
    <v-container class="divider-container" pa-0 pt-3 pb-3>
      <v-divider></v-divider>
    </v-container>
    <h3 class="head">Secondary Education</h3>
    <education-text v-for="item in secondary" :key="item.title" :content="item"></education-text>
  </v-container>
</template>

<script>
import EducationText from '../components/text/EducationText.vue';

export default {
  name: 'education',
  data() {
    return {
      tertiary: [
        {
          institution: 'Institution Title',
          year: 'Month Year - Month Year',
          description: 'Insert a Description Here',
          additional: 'Insert some additional text here',
          logo: '<logo>',
        },
      ],
      secondary: [
        {
          institution: 'Institution Title',
          year: 'Year - Year',
          description: 'Insert a Description Here',
          additional: 'Insert additional text here',
        },
      ],
    };
  },
  components: {
    EducationText,
  },
};
</script>
<style>
.education-page {
  padding-top: 0;
  padding-bottom: 0;
}
</style>
