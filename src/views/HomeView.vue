<template>
  <div ref="vantaRef" class="hero">
    <div class="pfp">
      <img :src="profileSrc" alt="Profile Image">
      <h1>Hi, I'm</h1>
      <p class="typewrite" data-period="2000" data-type='[
          " Normand Cardinal.",
          " A Web Developer.",
          " A Bot Developer."
        ]'>
        <span class="wrap"></span>
      </p>
    </div>
  </div>

  <div class="content">
    <p>
      Welcome to my portfolio! I am a passionate web and bot developer, dedicated to creating innovative solutions and
      bringing ideas to life. Explore my projects and get in touch to collaborate!
    </p>
  </div>

  <div class="grid-content">
    <div class="card">
      <h2 class="card-title">About Me</h2>
      <div class="card-description">
        <p class="card-description">
          I am a self-taught developer with a strong interest in web technologies and bot development. I enjoy learning
          new
          skills and applying them to real-world projects.

        </p>
        <button class="card-button" onclick="window.location.href='/about'">Learn More</button>
      </div>
    </div>
    <div class="card">
      <p class="card-title">My Skills</p>
      <p class="card-description">
        JavaScript, Vue.js, Node.js, HTML, CSS, Python, Discord.js, REST APIs, Git, and more.
      </p>
    </div>
    <div class="card">
      <p class="card-title">Contact</p>
      <p class="card-description">
        Feel free to reach out to me via email or social media!
      </p>
    </div>
  </div>

</template>

<style scoped>
a {
  text-decoration: none;
  color: inherit;
}

.grid-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 24px;
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
  align-items: start;
}

.card {
  text-align: center;
  padding: 20px;
  border: 1px #793B2E solid;
  border-radius: 12px;
  background: #6d482e;
  transition: all 0.3s ease;
  display: grid;
  grid-template-rows: auto 0fr;
  transition: grid-template-rows 0.4s ease, border-color 0.3s ease, box-shadow 0.3s ease;
}


.card:hover {
  grid-template-rows: auto 1fr;
  border-color: #9c4f3f;
}

.card-title {
  margin: 0;
  transition: padding 0.3s ease;
}


.card-description {
  min-height: 0;
  overflow: hidden;
  opacity: 0;
  color: #cbd5e1;
  margin: 0;
  transition: opacity 0.3s ease, margin 0.3s ease;
}


.card:hover .card-description {
  opacity: 1;
  margin-top: 10px;

  transition: opacity 0.3s ease 0.1s, margin 0.3s ease;
}

.card-button {
  margin-top: 10px;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background-color: #9c4f3f;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}



.hero {
  width: auto;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  max-width: 800px;
  margin: 2rem auto;
  padding: 1rem;
  text-align: center;
  font-family: 'Poppins', sans-serif;
  font-size: 1.2rem;
  color: #cbd5e1;
}

.pfp {
  display: grid;
  grid-template-columns: max-content max-content 350px;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  align-items: center;
  margin-top: 2rem;
  text-shadow: 1rem;
}

.pfp img {
  position: relative;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-right: 1rem;
  mix-blend-mode: screen;
}

.typewrite {
  color: #9B6A46;
  font-size: 2rem;
  margin-left: 10px;
}
</style>


<script setup>
import { ref, onMounted } from 'vue';
import profileSrc from '../assets/Me.png';

import * as THREE from 'three';
import p5 from 'p5';
import BIRDS from 'vanta/dist/vanta.topology.min';

const vantaRef = ref(null);
let vantaEffect = null;


onMounted(() => {
  vantaEffect = BIRDS({
    el: vantaRef.value,
    p5,
    mouseControls: false,
    touchControls: false,
    gyroControls: false,
    minHeight: 200.00,
    minWidth: 200.00,
    scale: 1.00,
    scaleMobile: 1.00,
    color: 0x793B2E,
    backgroundColor: 0x0,
    speed: 0
  });
});


var TxtType = function (el, toRotate, period) {
  this.toRotate = toRotate;
  this.el = el;
  this.loopNum = 0;
  this.period = parseInt(period, 10) || 2000;
  this.txt = '';
  this.tick();
  this.isDeleting = false;
};

TxtType.prototype.tick = function () {
  var i = this.loopNum % this.toRotate.length;
  var fullTxt = this.toRotate[i];

  if (this.isDeleting) {
    this.txt = fullTxt.substring(0, this.txt.length - 1);
  } else {
    this.txt = fullTxt.substring(0, this.txt.length + 1);
  }

  this.el.innerHTML = '<span class="wrap">' + this.txt + '</span>';

  var that = this;
  var delta = 200 - Math.random() * 100;

  if (this.isDeleting) { delta /= 2; }

  if (!this.isDeleting && this.txt === fullTxt) {
    delta = this.period;
    this.isDeleting = true;
  } else if (this.isDeleting && this.txt === '') {
    this.isDeleting = false;
    this.loopNum++;
    delta = 500;
  }

  setTimeout(function () {
    that.tick();
  }, delta);
};

onMounted(() => {
  var elements = document.getElementsByClassName('typewrite');
  for (var i = 0; i < elements.length; i++) {
    var toRotate = elements[i].getAttribute('data-type');
    var period = elements[i].getAttribute('data-period');
    if (toRotate) {
      new TxtType(elements[i], JSON.parse(toRotate), period);
    }
  }

  var css = document.createElement("style");
  css.type = "text/css";
  css.innerHTML = ".typewrite > .wrap { border-right: 0.08em solid #fff; font-weight: bold;}";
  document.body.appendChild(css);
});
</script>
