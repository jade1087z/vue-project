<script setup>
import { skillText } from '../constants'
</script>
<template>
  <section id="skill">
    <div class="skill__inner">
      <h2 class="skill__title">
        <em>나의 도전</em>
      </h2>
      <div class="skill__desc">
        <div v-for="(skill, key) in skillText" :key="key">
          <span>{{ key + 1 }}</span>
          <h3>{{ skill.title }}</h3>
          <p>{{ skill.desc }}</p>
        </div>
      </div>
    </div>
  </section>
  <!-- skill -->
</template>
<style>
.skill {
}
.skill__inner {
  display: flex;
  justify-content: space-between;
  background-color: var(--black100);
}
.skill__title {
  position: sticky;
  top: 60px;
  left: 0;
  width: 48%;
  height: 500px;
  background-color: var(--black100);
  font-size: 4vw;
  font-weight: 900;
  line-height: 1.6;
  text-transform: uppercase;
  padding: 0vw 1vw 0 1vw;
  color: var(--white200);
}
.skill__title em {
  font-size: 1.25rem;
  font-family: var(--mainKor-font);
}
.skill__desc {
  width: 50%;
  padding: 1vw;
  margin-bottom: 70vw;
  height: 500px;
  background-color: var(--black200);
  color: var(--white300);
  cursor: pointer;
}
.skill__desc div:first-child {
  padding-top: 0.5vw;
}
.skill__desc div {
  padding: 0vw 1vw 0.5vw 1vw;
  margin-bottom: 10vw;
}
.skill__desc h3 {
  text-decoration: underline;
  text-underline-position: under;
}
.skill__desc div > p {
  padding-top: 1vw;
  transition: all 0.1s;
}

@media (max-width: 800px) {
  .skill__inner {
    flex-direction: column;
    padding-left: 1vw;
    background-color: var(--black100);
  }
  .skill__title {
    width: 100%;
    margin-bottom: 10vw;
    height: auto;
  }
  .skill__desc {
    background-color: var(--black100);
  }
}
</style>
