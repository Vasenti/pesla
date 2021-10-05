<template>
  <div class="container">
    <header>
      <nav>
        <img src="@/assets/pesla.png" alt="" class="logo">
        <div class="menu-btn" @click="animateBurgerMenu()">
          <div class="menu-btn__burger"></div>
        </div>
        <ul class="nav-ul">
          <li><a href="#">Model X</a></li>
          <li><a href="#">Model Y</a></li>
          <li><a href="#">Model Z</a></li>
          <li><a href="#">Model C</a></li>
        </ul>
        <ul class="nav-ul">
          <li><a href="#">Store</a></li>
          <li><a href="#">Account</a></li>
        </ul>
      </nav>
    </header>
    <transition>
      <router-view/>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      openBurger: false,
    }
  },
  methods: {
    animateBurgerMenu(){
      let menuBtn = document.querySelector('.menu-btn');
      if(!this.openBurger) {
        menuBtn?.classList.add('open');
        this.openBurger = true;
      }else {
        menuBtn?.classList.remove('open');
        this.openBurger = false;
      }
    }
  }
}
</script>

<style scoped src="./assets/styles/app.css"></style>