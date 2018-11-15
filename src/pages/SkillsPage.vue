<!-- Skills Page -->

<template>
  <v-container flat text-xs-center class="skills-page">
    <v-container class="width-limit-1000">
      <v-layout row>
        <v-flex>
          <v-chip outline disabled :selected="item.pressed" :key="index" v-for="(item, index) in skills" @click.native="selectSkills(index)">{{ item.title }}</v-chip>
        </v-flex>
      </v-layout>
    </v-container>
      <v-container class="width-limit-1000">
        <v-layout row>
          <v-flex>
            <transition-group name="fade-chip">
              <v-chip close disabled :key="item.title" v-for="item in skillsSelected" @input="selectSkills(skills.indexOf(item))">{{ item.title }}</v-chip>
            </transition-group>
          </v-flex>
        </v-layout>
      </v-container>
    <transition-group name="reorder">
      <skills-text v-for="item in skillsExplained" :key="item.title" :title="item.title" :content="item.content"></skills-text>
    </transition-group>
  </v-container>
</template>

<script>
import SkillsText from '../components/text/SkillsText.vue';

export default {
  name: 'skills',
  data() {
    return {
      skillsInitial: [
        {
          title: 'Skill Title',
          content: [
            'Explanation One',
            'Explanation Two',
            'Explanation Three',
            'Explanation Four',
          ],
          tags: [
            'Tag One',
            'Tag Two',
          ],
        },
        {
          title: 'Skill Two Title',
          content: [
            'Explanation One',
          ],
          tags: [
            'Tag Three'
          ],
        },
      ],
      skills: [
        {
          title: 'Tag One',
          pressed: false,
        },
        {
          title: 'Tag Two',
          pressed: false,
        },
        {
          title: 'Tag Three',
          pressed: false,
        },
      ],
      skillsExplained: [],
      skillsSelected: [],
    };
  },
  components: {
    SkillsText,
  },
  mounted() {
    this.skillsExplained = [...this.skillsInitial];
  },
  methods: {
    selectSkills(pressed) {
      if (this.skills[pressed].pressed) {
        this.skills[pressed].pressed = false;
        // remove selected
        this.skillsSelected.splice(this.skillsSelected.indexOf(this.skills[pressed]), 1);
        this.reorderSkills();
        // this.skills.splice(this.skills.length, 0, this.skills[pressed]);
        // this.skills.splice(pressed, 1);
      } else {
        this.skills[pressed].pressed = true;
        // add selected
        this.skillsSelected.splice(0, 0, this.skills[pressed]);
        this.reorderSkills();
        // this.skills.splice(0, 0, this.skills[pressed]);
        // this.skills.splice(pressed + 1, 1);
      }
    },
    reorderSkills() {
      this.skillsExplained = [...this.skillsInitial];
      // most recently selected is at index 0
      for (let itemIndex = this.skillsSelected.length - 1; itemIndex > -1; itemIndex--) {
        const item = this.skillsSelected[itemIndex];
        for (const skill of this.skillsExplained) {
          if (skill.tags.indexOf(item.title) !== -1) {
            // add to beginning
            // remove from original
            this.skillsExplained.splice(this.skillsExplained.indexOf(skill), 1);
            this.skillsExplained.splice(0, 0, skill);
            // break;
          }
        }
      }
    },
  },
};
</script>
<style>
  .skills-page {
    padding-top: 0;
    padding-bottom: 0;
  }

  /* Transitions and Animations */
  .reorder-move {
    transition: transform 1s;
  }

  .fade-chip-item {
    transition: all 1s;
    display: inline-block;
    margin-right: 10px;
  }
  .fade-chip-enter, .fade-chip-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
  .fade-chip-leave-active {
    position: absolute;
  }
</style>
