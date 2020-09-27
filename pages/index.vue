<template>
  <v-layout column justify-center>
    <v-flex xs12 sm8 md6>
      <section id="top" class="top-wrapper">
        <p class="text-left text-h2">Welcome to Katsuya Yamagata’s Portfolio Site</p>
      </section>
      <section id="about">
      <about />
      </section>
      <works />
      <skill />
    </v-flex>
  </v-layout>
</template>
<style>
.top-wrapper {
  text-align: center;
  padding: 38vh 0;
  height: 100vh;
}
</style>
<script>
import About from '@/components/about';
import Works from '@/components/works';
import Skill from '@/components/skill';
export default {
  components: {
    About,
    Works,
    Skill
  }
};
</script>
