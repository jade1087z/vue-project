<script setup>
import { siteText } from '../constants'
</script>

<template>
  <section id="site">
    <div class="site__inner">
      <div class="site__title">site Coding <em>나의 작업물</em></div>
      <div class="site__wrap">
        <div v-for="(site, key) in siteText" :key="key" :class="'site__item s' + (key + 1)">
          <span class="num">{{ key + 1 }} </span>
          <div class="text">
            <div>{{ site.text[0] }}</div>
            <div>{{ site.text[1] }}</div>
            <div>{{ site.text[2] }}</div>
          </div>
          <h3 class="title">{{ site.title }}</h3>
          <div class="btn">
            <a href="#">{{ site.code }}</a>
            <a href="#">{{ site.view }}</a>
          </div>
          <div class="info">
            <span>{{ site.info[0] }}</span>
            <span>{{ site.info[1] }}</span>
            <span>{{ site.info[2] }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
  <!--  site -->
</template>
<style lang="scss">
.site__inner {
  padding: 16px;
  background-color: var(--black);
  color: var(--white100);
}

.site__title {
  position: sticky;
  top: 30px;
  left: 0;
  width: 100%;
  height: 5vw;
  border-bottom: 2px solid var(--white200);
  font-size: 3vw;
  font-family: var(--mainEng-font);
  font-weight: 600;
  padding-bottom: 7vw;
}

.site__item {
  height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: sticky;
  left: 0;
  margin-top: 2vw;
  margin-bottom: 1vw;
  margin: 2vw 0;
  padding-left: 1.5vw;
  border-bottom: 1px solid var(--white200);
}
.site__item.s1 {
  background-color: var(--black100);
  top: 180px;
}
.site__item.s2 {
  background-color: var(--black100);
  top: 200px;
}
.site__item.s3 {
  background-color: var(--black100);
  top: 220px;
}
.site__item.s4 {
  background-color: var(--black100);
  top: 240px;
}
.site__item .num {
  font-family: var(--mainNum-font);
  font-size: 2.3vw;
  font-weight: 600;
  display: inline-block;
  padding-bottom: 0.3vw;
  /* text-decoration: underline;
    text-underline-position: under;
    text-decoration-color: var(--white400); */
  transition: all 0.2s;
  position: relative;
  color: var(--white400);
}
.site__item .num:hover {
  color: var(--white100);
}
.site__item .num::before {
  content: '';
  position: absolute;
  left: -56%;
  bottom: 10%;
  width: 200%;
  height: 2px;
  background-color: var(--white400);
  transition: all 0.5s;
  transform: scaleX(0);
}
.site__item .num:hover::before {
  background-color: var(--white100);
  transform: scaleX(1);
}
.site__item .text {
  text-align: center;
}
.site__item .text:first-child {
  font-size: 1.5rem;
}
.info {
  position: absolute;
  left: 0;
  bottom: 3%;
  width: 98%;
  margin-left: 1%;
  display: flex;
  justify-content: space-between;
}
.site__wrap .btn a {
  color: var(--white200);
  display: inline-block;
  margin-bottom: 2vw;
}
.info span {
  font-family: var(--mainKor-font);
  font-size: 12px;
  padding: 3px 0;
  text-transform: uppercase;
}
</style>
