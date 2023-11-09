<script setup>
import { headerNav } from '../constants'
</script>
<template>
  <header id="header" role="banner">
    <div class="header__inner">
      <div class="header__logo">
        <a href="#">portfolio <em>developer</em></a>
      </div>
      <div
        class="header__nav"
        role="navigation"
        aria-label="메인 메뉴"
        :class="{ show: isNavVisible }"
      >
        <ul>
          <li v-for="(nav, key) in headerNav" :key="key">
            <a :href="nav.url" @click="scrollLink($event)">{{ nav.title }}</a>
          </li>
        </ul>
      </div>
      <div
        class="header__nav__mobile"
        id="headerToggle"
        aria-controls="primary-menu"
        aria-expanded="isNavVisible.toString()"
        role="button"
        @click="toggleMenu"
      >
        <span></span>
      </div>
    </div>
  </header>
  <!-- header -->
</template>
<script>
export default {
  data() {
    return {
      isNavVisible: false
    }
  },
  methods: {
    toggleMenu() {
      this.isNavVisible = !this.isNavVisible
    },
    scrollLink(event) {
      event.preventDefault()

      const targetId = event.target.getAttribute('href')
      const targetElement = document.querySelector(targetId)

      if (targetElement) {
        targetElement.scrollIntoView({ behavior: 'smooth' })
      }
    }
  }
}
</script>
<style>
#header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  z-index: 10000;
  text-transform: uppercase;
}

.header__inner {
  height: 10vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(100px);
  padding: 1rem;
}

.header__logo {
  width: 20%;
}
.header__logo a {
  font-size: 2vh;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 0.4vh;
  white-space: nowrap;
  color: var(--white200);
}
.header__logo a:hover {
  color: var(--white200);
}
.header__nav {
  width: 80%;
  display: flex;
  justify-content: flex-end;
}
.header__nav li {
  display: inline;
  width: 20%;
  padding: 0 1rem 0 1rem;
}
.header__nav li a {
  font-size: 0.9rem;
  font-weight: 600;
  position: relative;
  padding: 0.3rem;
  color: var(--white200);
}
.header__nav li a::before {
  content: '';
  position: absolute;
  width: calc(100% - 18px);
  height: 1px;
  background-color: var(--white200);
  left: 11px;
  bottom: -3px;
  transform: scaleX(0);
  transition: all 0.3s;
}
.header__nav li a:hover::before {
  transform: scaleX(1);
}
.header__nav li a:hover {
  color: var(--white200);
}

.header__nav__mobile {
  width: 40px;
  height: 40px;
  cursor: pointer;
  display: none;
}

.header__nav__mobile span {
  display: block;
  width: 40px;
  height: 2px;
  background-color: var(--black600);
  margin-top: 19px;
  position: relative;
  transition: width 0.3s;
}
.header__nav__mobile span::before {
  content: '';
  position: absolute;
  width: 40px;
  height: 2px;
  background-color: var(--black600);
  right: 0;
  top: 6px;
  transition: width 0.3s;
}
.header__nav__mobile span::after {
  position: absolute;
  content: '';
  width: 40px;
  height: 2px;
  background-color: var(--black600);
  right: 0;
  bottom: 6px;
  transition: width 0.3s;
}

@media (max-width: 800px) {
  .header__nav {
    display: none;
  }
  /* block 상태는 애니메이션을 못줌  */
  .header__nav.show {
    display: block;
  }

  .header__nav.show ul {
    display: block;
    position: absolute;
    right: 0;
    top: 70px;
    background-color: var(--white400);
    z-index: 1000;
    min-width: 159px;
    padding: 20px 0;
  }

  .header__nav.show li {
    display: block;
    text-align: right;
  }

  .header__nav.show li a {
    display: inline-block;
    padding: 10px;
  }
  .header__nav.show + .header__nav__mobile span::before {
    width: 20px;
  }
  .header__nav.show + .header__nav__mobile span::after {
    width: 20px;
  }
  .header__nav__mobile {
    display: block;
  }
}
</style>
