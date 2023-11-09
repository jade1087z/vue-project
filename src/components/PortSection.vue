<script setup>
import { portText } from '../constants'
</script>

<template>
  <section id="port">
    <div class="port__inner">
      <div class="port__title">portfolio <em>포폴 작업물</em></div>
      <div class="port__wrap">
        <div v-for="(port, key) in portText" :class="'port__item p' + (key + 1)">
          <span class="num">{{ key + 1 }}</span>
          <a href="#">
            <img :src="port.img" alt="" />
          </a>
          <h3 class="title">{{ port.title }}</h3>
          <p class="desc">
            {{ port.desc }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

export default {
  mounted: function () {
    this.scrollAnimation()
  },
  methods: {
    scrollAnimation() {
      const horSection = gsap.utils.toArray('.port__item')

      gsap.to(horSection, {
        xPercent: -120 * (horSection.length - 1),
        ease: 'none',
        scrollTrigger: {
          trigger: '#port',
          start: 'top 56px',
          end: '+=3000',
          pin: true,
          scrub: 1,
          markers: true,
          invalidateOnRefresh: true,
          anticipatePin: 1
        }
      })
    }
  }
}
</script>

<style lang="scss">
#port {
  background-color: var(--black);
  width: 100%;
  overflow: hidden;
}
.port__inner {
  padding: 16px;
}
.port__wrap {
  display: flex;
  /* wrap -100p */
  flex-wrap: wrap;
  width: 7000px;
}
.port__title {
  width: 100%;
  /* 고친거 */
  height: 5vh;
  color: #ccc;
  /*  */
  font-size: 1.2rem;
  font-weight: 600;
  padding-bottom: 1rem;
  padding-top: 1.3rem;
}
.port__item {
  width: 500px;
  height: 70vh;
  background-color: #ccc;
  margin-right: 20px;
  border: 3px solid var(--white200);
  padding: 2rem;
}
.port__item.p1 {
  background-color: var(--black600);
}
.port__item.p2 {
  background-color: var(--black700);
}
.port__item.p3 {
  background-color: var(--black800);
}
.port__item.p4 {
  background-color: var(--black900);
}
.port__item.p5 {
  background-color: var(--black1000);
}
.port__item.p6 {
  background-color: var(--black900);
}
.port__item.p7 {
  background-color: var(--black1200);
}
.port__item.p8 {
  background-color: var(--black900);
}
.port__item.p9 {
  background-color: var(--black1000);
}
.port__item.p10 {
  background-color: var(--black900);
}

.port__item .num {
  font-weight: bold;
  font-family: var(--mainNum-font);
  font-size: 1.4rem;
  color: var(--font-color1);
}
.port__item a img {
  width: 100%;
  border: 4px solid var(--neon-color-puple8);
}
.port__item .title {
  margin: 1rem 0;
  font-size: 0.9rem;
  font-weight: bold;
  text-align: center;
  color: var(--font-color1);
  letter-spacing: 0.4vh;
}

.port__item .desc {
  border-top: 2px solid var(--neon-color-puple7);
  font-size: 0.8rem;
  padding: 0.5rem 0;
  color: var(--black200);
  font-weight: 600;
  text-align: left;
  color: var(--font-color1);
  letter-spacing: 0.3vh;
}
</style>
