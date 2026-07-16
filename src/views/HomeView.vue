<template>
  <div class="pfp">
    <img :src="profileSrc" alt="Profile Image">
    <h1>Hi, I'm </h1>
    <p href="" class="typewrite" data-period="2000" data-type='[ " Normand Cardinal.", " A Web Developer.", " A Designer.", " A Creator." ]'>
      <span class="wrap" style="font-weight: bold;"></span>
    </p>
  </div>


</template>

<style scoped>
.pfp {
  display: flex;
  justify-content: center;
  font-weight: bold;
  align-items: center;
  margin-top: 2rem;
  text-shadow: 1rem;
}

.pfp img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-right: 1rem;
  mix-blend-mode: screen;
}

.typewrite {
  color: #08bdd5;
  font-size: 2rem;
  margin-left: 10px;
}


</style>


<script setup>
import profileSrc from '../assets/Me.png';

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

window.onload = function () {
  var elements = document.getElementsByClassName('typewrite');
  for (var i = 0; i < elements.length; i++) {
    var toRotate = elements[i].getAttribute('data-type');
    var period = elements[i].getAttribute('data-period');
    if (toRotate) {
      new TxtType(elements[i], JSON.parse(toRotate), period);
    }
  }
  // INJECT CSS
  var css = document.createElement("style");
  css.type = "text/css";
  css.innerHTML = ".typewrite > .wrap { border-right: 0.08em solid #fff}";
  document.body.appendChild(css);
};
</script>
