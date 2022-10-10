<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Menu from './components/Menu.vue'
import Social from './components/Social.vue'
</script>

<template>
  <Menu/>
  <div class="wrapper">
  <div class="wrapper-inner">
    <p>Hi, I'm <a href="https://www.gla.ac.uk/stafflist/search/person/4edee9e18597/">Graeme</a> a librarian, historian and educator advancing the <a href="https://en.wikipedia.org/wiki/Digital_transformation">digital transformation</a> in cultural instititutions. I am currently working at the <a href="https://www.gla.ac.uk/myglasgow/archivespecialcollections/">University of Glasgow</a>. I have a particular interest in digital humanities, book history and data visualisation. The best way to get a hold of me is by <a href="https://www.gla.ac.uk/stafflist/search/person/4edee9e18597/">email</a> or on <a href="https://twitter.com/gj_kemp">twitter</a>.</p>
  </div>
</div>


<div id="circle" class="circle"></div>  
</template>

<style scoped>
html, body {
  perspective: 800px;
  margin: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  font-family: -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica Neue,Arial,sans-serif;
}

.menu {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}

.wrapper {
  width: 100%;
  height: 100%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  cursor: default;
}

h1 {
  font-size: 50px;
  margin: 0 auto 10px;
}

p {
  line-height: 1.6;
  font-size: 18px; 
  color: #232323;
}

@media only screen and (min-width: 600px) {
  p {
    font-size: 50px;
  }
}

@media only screen and (min-width: 600px) {
  .circle {
    width: 40px;
    height: 40px;
    background: linear-gradient(to top left, #A964FF, #A964FF);
    border-radius: 50%;
    position: absolute;
    top: 50%;
    left: 50%;
    margin: -20px 0 0 -20px;
    pointer-events: none;
    mix-blend-mode: multiply;
    z-index: 10;
  }
}
</style>

<script>
  import Kinet from 'kinet';

  export default {
    
    name: 'home',
    mounted() {
      this.pointer()
    },
    methods: {
      pointer: function () {
         // create instance of kinet with custom settings
        let kinet = new Kinet({
          acceleration: 0.06,
          friction: 0.20,
          names: ["x", "y"],
        });
        // select circle element
        var circle = document.getElementById('circle');
        // set handler on kinet tick event
        kinet.on('tick', function(instances) {
          circle.style.transform = `translate3d(${ (instances.x.current) }px, ${ (instances.y.current) }px, 0) rotateX(${ (instances.x.velocity/2) }deg) rotateY(${ (instances.y.velocity/2) }deg)`;
        });
        // call kinet animate method on mousemove
        document.addEventListener('mousemove', function (event) {
          kinet.animate('x', event.clientX - window.innerWidth/2);
          kinet.animate('y', event.clientY - window.innerHeight/2);
        });
        // log
        kinet.on('start', function() {
          console.log('start');
        });
        kinet.on('end', function() {
          console.log('end');
        });
      }
    }
  }
</script>