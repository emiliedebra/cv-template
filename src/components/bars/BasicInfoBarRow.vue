<!-- Basic Info Bar -->

<template>
  <v-container class="about-page">
    <v-layout row>
      <!-- Avatar -->
      <v-flex>
        <v-avatar size="180px">
          <img src="/static/img/default-avatar.png">
        </v-avatar>
      </v-flex>
      <v-container>
        <v-layout row>
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
import { profile } from '../../data/basic-info.js';
export default {
  name: 'basic-info-bar-row',
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
