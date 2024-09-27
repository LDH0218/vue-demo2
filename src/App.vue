<template>
  <header class="header" id="header">
    <nav class="nav container">
      <a href="#" class="nav__logo">
        <i class="ri-anchor-line"></i>
        <span>PISHIP</span>
      </a>
      <div class="nav__menu" :class="{ 'show-menu': isMenuOpen }" >
        <ul class="nav__list">
          <li >
            <a href="#" class="nav__link">HOME</a>
          </li>
          <li >
            <a href="#" class="nav__link">EXPLORE</a>
          </li>
          <li >
            <a href="#" class="nav__link">CARIBBEAN</a>
          </li>
          <li >
            <a href="#" class="nav__link">CONTACT</a>
          </li>
        </ul>
        <div class="nav__close" @click="closeMenu">
          <i class="ri-close-large-line"></i>
        </div>
      </div>
      <div class="nav__toggle" @click="toggleMenu">
        <i class="ri-menu-line"></i>
      </div>
    </nav>
  </header>

  <main class="main">
    <section class="home">
      <div class="home__container container">
        <img :src="cloud" alt="Cloud" class="home__cloud-1">
        <img :src="cloud" alt="Cloud" class="home__cloud-2">
        <div class="home__data">
          <h3 class="home__subtitle">NEW PIRATE</h3>
          <h1 class="home__title">
            <span>LEGEND OF</span> <br>
            <span>THE SEAS</span>
          </h1>
          <a href="#" class="home__button">EXPLORE NOW</a>
        </div>
        <div class="home__images">
          <div class="home__waves-3" :style="{ backgroundImage: `url(${waves3})` }"></div>
          <div class="home__waves-2" :style="{ backgroundImage: `url(${waves2})` }"></div>
          <img :src="pirateShip" alt="Pirate Ship" class="home__ship">
          <div class="home__waves-1" :style="{ backgroundImage: `url(${waves1})` }"></div>
        </div>
      </div>
    </section>
  </main>

</template>

<script setup>
/*=============== SHOW MENU ===============*/
import { ref } from 'vue';
import cloud from './assets/img/cloud.svg';
import pirateShip from './assets/img/pirate-ship.svg';
import waves1 from './assets/img/waves-1.png';
import waves2 from './assets/img/waves-2.png';
import waves3 from './assets/img/waves-3.png';
const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};



/*=============== REMOVE MENU MOBILE ===============*/
const closeMenu = () => {
  isMenuOpen.value = false;
};

/*=============== ADD SHADOW HEADER ===============*/
const shadowHeader = () => {
  const header = document.getElementById('header');
  if (header) {
    // Add a class if the scroll position is greater than 50
    if (window.scrollY >= 50) {
      header.classList.add('shadow-header');
    } else {
      header.classList.remove('shadow-header');
    }
  }
};

// Add the scroll event listener
window.addEventListener('scroll', shadowHeader);

</script>

<style scoped>
/*=============== HEADER & NAV ===============*/
.header {
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  right: 0;
  background-color: transparent;
  z-index: var(--z-fixed);
  transition: background-color 0.4s, box-shadow 0.4s;
  display: flex; /* 确保使用 flex 布局 */
  justify-content: center; /* 整体居中 */
}
.nav{
  position: relative;
  height: var(--header-height);
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
}
.nav__logo{
  display: inline-flex;
  align-items: center;
  column-gap: 0.5rem;
  font-family: var(--second-font);
  color: var(--black-color);
}
.nav__logo i{
  font-size: 1.5rem;
}
.nav__logo span{
  font-weight: var(--font-bold);
}
.nav__toggle,
.nav__close{
  display: flex;
  font-size: 1.5rem;
  cursor: pointer;
}

/* Navigation for mobile devices */
@media screen and (max-width: 1150px) {
  .nav__menu{
    position: fixed;
    top: -120%;
    left: 0;
    background-color: var(--body-color);
    box-shadow: 0 4px 24px hsla(40,24%,4%,0.1);
    width: 100%;
    padding-block: 5rem 4rem;
    transition: top 0.4s;
  }
}
.nav__list{
  text-align: center;
  display: flex;
  flex-direction: column;
  row-gap: 2.5rem;
}
.nav__link{
  color: var(--black-color);
}
.nav__close{
  position: absolute;
  top: 1rem;
  right: 1.5rem;
}


/* Show menu */
.show-menu{
  top: 0;
}


/* Add shadow header */
.shadow-header {
  background-color: var(--body-color);
  box-shadow:0 2px 16px hsla(40,24%,4%,.1);
}


/*=============== HOME ===============*/
.home {
  position: relative;
}
.home__container {
  padding-top: 9.5rem;
  height: 100vh;
}
.home__data {
  position: relative;
  z-index: var(--z-tooltip);
}
.home__subtitle {
  font-size: var(--big-font-size);
  font-weight: var(--second-font);
  color: var(--black-color);
  margin-bottom: .5rem;
}
.home__title {
  font-size: var(--biggest-font-size);
  font-family: var(--second-font);
  line-height: 100%;
  margin-bottom: 1rem;
}
.home__title span {
  font-size: var(--bigger-font-size);
}
.home__button {
  position: relative;
  display: inline-flex;
  padding: 0.75rem 2rem;
  border-radius: 4rem;
  color: black;
  border: 3px solid var(--black-color);
  background-color: var(--body-color);
}
.home__button::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  border: 3px solid var(--black-color);
  background-color: var(--body-color);
  border-radius: 4rem;
  left: 0;
  right: 0;
  bottom: -8px;
  justify-self: center;
  z-index: -1;
  transition: transform 0.4s;
}
.home__button:hover::after {
  transform: translate(2px, 2px);
}
.home__cloud-1,
.home__cloud-2 {
  position: absolute;
  width: 150px;
}
.home__cloud-1 {
  top: 6rem;
  right: 1rem;
  animation: cloud-1 8s linear infinite;
}
.home__cloud-2 {
  top: 16rem;
  left: 0.5rem;
  animation: cloud-2 10s linear infinite;
}
.home__images {
  overflow: hidden;
}
.home__images div{
  max-width: initial;
  width: 650px;
  height: 270px;
  background-size:1000px 100%;
  position: absolute;
  left:0
}
.home__waves-1
{
  bottom: -1.5rem;
  animation: wave-1 4s linear infinite;
}
.home__waves-2
{
  bottom: -1rem;
  animation: wave-2 4s linear infinite;
}
.home__waves-3
{
  bottom: 3rem;
  animation: wave-1 4s linear infinite;
}
.home__ship {
  width: 300px;
  position: absolute;
  bottom: 2rem;
  left: 0;
  right: 0;
  margin-inline: auto;
  transform-origin: center center;
  animation: ship 2s linear infinite;
}
/* Animated Clouds */
@keyframes cloud-1 {
  0% {
    margin-right: -1000px;
  }
  100% {
    margin-right: 100%;
  }
}
@keyframes cloud-2 {
  0% {
    margin-left: 100%;
  }
  100% {
    margin-left: -1000px;
  }
}
/* Animated waves */
@keyframes wave-1 {
  0% {
    background-position-x: 1000px;
  }
  100% {
    background-position-x: 0;
  }
}
@keyframes wave-2 {
  0% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(0, -5px);
  }
  100% {
    transform: translate(0, 0);
  }
}
@keyframes wave-3 {
  0% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(0, -2px);
  }
  100% {
    transform: translate(0, 0);
  }
}

/* Animated ship */
@keyframes ship {
  0% {
    transform: translateY(0) rotate(0);
  }
  25% {
    transform: translateY(0) rotate(-8deg);
  }
  50% {
    transform: translateY(4px) rotate(-8deg);
  }
  75% {
    transform: translateY(1px) rotate(8deg);
  }
  100% {
    transform: translateY(0) rotate(0);
  }
}

/*=============== BREAKPOINTS ===============*/
/* For small devices */
@media screen and (max-width: 300px) {
  .container {
    margin-inline: 1rem;
  }
  .home__title  {
    font-size: 3rem;
  }
  .home__title span {
    font-size: 2.5rem;
  }
}
@media screen and (min-width: 350px) and (max-height : 680px) {
  .home__container {
    height: 750px;
  }
  .home__images div{
    width: 100%;
  }
}
/* For medium devices */
@media screen and (min-width: 576px) {
  .home__images div{
    width: 100%;
  }
  .home__ship {
    width: 400px;
  }
}

/* For large devices */
@media screen and (min-width: 1150px) {
  .home__container {
    margin-inline: auto;
  }
  .nav{
    height: calc(var(--header-height) + 2rem);
  }
  .nav__toggle,
  .nav__close{
    display: none;
  }
  .nav__list{
    flex-direction: row;
    column-gap: 4.5rem;
  }
  .home__container {
    height: 860px;
    padding-top: 11.5rem;
  }
  .home__title{
    margin-bottom: 3rem;
  }
  .home__button,
  .home__button::after {
    border-width: 4px;
  }
  .home__button::after {
    bottom: -12px;
  }
  .home__cloud-1,
  .home__cloud-2 {
    width: 250px;
  }
  .home__cloud-1 {
    top: 8rem;
    right: 2rem;
  }
  .home__cloud-2 {
    top: 18rem;
    left: 1rem;
  }
  .home__images div{
    height: 375px;
    background-size: 100vw 100%;
  }
  @keyframes wave-1 {
    0% {
      background-position-x: 100vw;
    }
    100% {
      background-position-x: 0;
    }
  }
  @keyframes wave-2 {
    0%{
      background-position-x: 0;
    }
    100%{
      background-position-x: 100vw;
    }
  }

  .home__waves-1
  {
    bottom: -2.5rem;
  }
  .home__waves-2
  {
    bottom: -2rem;
  }
  .home__waves-3
  {
    bottom: 5rem;
  }
  .home__ship {
    width: 630px;
    left: 30rem;
  }
}
@media screen and (min-width: 1150px) and (min-height:1000px) {
  .home__container {
    display: grid;
    height: 100vh;
  }
  .home__data {
    align-self: center;
  }
}
</style>
