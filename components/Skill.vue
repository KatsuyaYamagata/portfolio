<template>
  <v-container class="skill-wrapper">
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h2">Skill</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p class="text-left text-h4">Sound Skill</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <ul class="skill-list">
          <li class="skill">
            <h3>DAW Operation (Logic pro X)</h3>
            <progress class="skill-1" max="100" value="90" />
          </li>
          <li class="skill">
            <h3>Composing</h3>
            <progress class="skill-1" max="100" value="90" />
          </li>
          <li class="skill">
            <h3>Mixing/Mastering</h3>
            <progress class="skill-1" max="100" value="80" />
          </li>
          <li class="skill">
            <h3>Studio Recording</h3>
            <progress class="skill-1" max="100" value="80" />
          </li>
          <li class="skill">
            <h3>Sound Effects</h3>
            <progress class="skill-1" max="100" value="60" />
          </li>
          <li class="skill">
            <h3>Field Recording</h3>
            <progress class="skill-1" max="100" value="50" />
          </li>
          <li class="skill">
            <h3>Foley Sounds</h3>
            <progress class="skill-1" max="100" value="50" />
          </li>
        </ul>
      </v-col>
    </v-row>
       <v-row>
      <v-col cols="12">
        <p class="text-left text-h4">Web Tech Skill</p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <ul class="skill-list">
          <li class="skill">
            <h3>HTML5</h3>
            <progress class="skill-2" max="100" value="80" />
          </li>
          <li class="skill">
            <h3>CSS3</h3>
            <progress class="skill-2" max="100" value="80" />
          </li>
          <li class="skill">
            <h3>Javascript (ES6)</h3>
            <progress class="skill-2" max="100" value="80" />
          </li>
          <li class="skill">
            <h3>Vue.js/Nuxt.js</h3>
            <progress class="skill-2" max="100" value="70" />
          </li>
          <li class="skill">
            <h3>Vuetify</h3>
            <progress class="skill-2" max="100" value="70" />
          </li>
          <li class="skill">
            <h3>Firebase</h3>
            <progress class="skill-2" max="100" value="50" />
          </li>
          <li class="skill">
            <h3>AWS</h3>
            <progress class="skill-2" max="100" value="40" />
          </li>
        </ul>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
    name: "Skill"
};
</script>

<style lang="scss">
.skill-wrapper {
  text-align: center;
}

body {
  font-family: "Helvetica Neue", arial, sans-serif;
  padding: 2em;
}

h3 {
  font-size: 1.25em;
}

progress,
progress[role] {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border: none;
  background-size: auto;
  height: 50px;
  width: 100%;
}

.skill-list {
  list-style: none;
  margin: 0;
  padding: 1em;
}

.skill {
  margin-bottom: 1em;
  position: relative;
  h3 {
    color: #fff;
    left: 1em;
    position: absolute;
    line-height: 50px;
  }
  ::-webkit-progress-value {
    animation: bar-fill 2s;
    width: 0px;
  }
}

// Style the bar colors
.skill-1::-webkit-progress-value {
  background: #F75940;
}

.skill-1::-moz-progress-bar {
  background: #F75940;
}

.skill-2::-webkit-progress-value {
  background: #3DC7BE;
}

.skill-2::-moz-progress-bar {
  background: #3DC7BE;
}
// Animation Keyframes
@-webkit-keyframes bar-fill {
  0% {
    width: 0;
  }
}

@keyframes bar-fill {
  0% {
    width: 0;
  }
}
</style>
