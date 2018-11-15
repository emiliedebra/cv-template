<!-- Basic Info Bar -->

<template>
  <v-container class="about-page">
    <v-layout column>
      <!-- Avatar -->
      <v-flex>
        <v-avatar size="200px">
          <!-- TODO: Add avatar -->
          <img src="/static/img/default-avatar.png">
        </v-avatar>
      </v-flex>
      <!-- Text Info -->
      <v-container>
        <v-layout column>
          <!-- Basic Info -->
          <v-flex>
            <info-text v-for="item in basic" :key="item.title" :title="item.title" :content="item.content"></info-text>
          </v-flex>
          <!-- Additional Info -->
          <v-flex>
            <info-text v-for="item in additional" :key="item.title" :title="item.title" :content="item.content"></info-text>
          </v-flex>
        </v-layout>
      </v-container>
    </v-layout>
  </v-container>
</template>

<script>
import InfoText from '../text/InfoText.vue';

export default {
  name: 'basic-info-bar-col',
  data() {
    return {
      basic: profile.basic,
      additional: profile.additional,
    };
  },
  components: {
    InfoText,
  },
};
</script>
