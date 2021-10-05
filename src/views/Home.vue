<template>
  <div class="home">
    <section class="one">
      <h1>Model X</h1>
      <div class="buttonsContainer">
        <button class="order">Order now</button>
        <button class="viewDetails">View details</button>
      </div>
    </section>
    <section class="two"></section>
    <div class="bounce-arrow">
      <div class="bouncing">
        <span class="mdi mdi-chevron-down"></span>
      </div>
    </div>
  </div>
</template>

<style scoped src="@/assets/styles/home.css"></style>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {},
  data() {
    return {
      mouseWheel: true,
      lastScroll: 0,
      currentDiv: 1,
    };
  },
  mounted() {
    this.startScrollEvent();
  },
  methods: {
    startScrollEvent(){
      window.addEventListener('wheel', this.scrollToNextDiv, false);
    },
    removeScrollEvent(){
      window.removeEventListener('wheel', this.scrollToNextDiv, false);
    },
    scrollToNextDiv(e) {
      if(!this.mouseWheel) return false;
      this.mouseWheel = false;

      setTimeout(() => {
        this.mouseWheel = true;
      }, 200);

      e = window.event || e;

      let height = window.innerHeight;
      let section = document.getElementsByTagName('section');
      console.log(this.currentDiv);

      if(this.currentDiv < section.length && this.currentDiv > 0){
        if(e.deltaY > 0) {
          window.scrollTo({
            top: height * this.currentDiv,
            behavior: 'smooth'
          });
          this.currentDiv++;
        }else {
          window.scrollTo({
            top: height * this.currentDiv,
            behavior: 'smooth'
          });
          this.currentDiv--;
        }
      }else {
        this.currentDiv = 1;
        window.scrollTo({
          top: 0,
          behavior: 'smooth'
        })
      }
    },
  },
};
</script>
