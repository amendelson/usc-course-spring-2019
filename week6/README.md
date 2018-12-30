<a href="https://amendelson.github.io/usc-course-spring-2019/"><div class="header">
<h1 class="ml7">
  <span class="text-wrapper">
    <span class="letters"><p id ="usc p">Data&nbsp;&nbsp;Journalism&nbsp;&nbsp;&nbsp;USC&nbsp;&nbsp;2019</p></span>
  </span>
</h1>
</div>
</a>
<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/2.0.2/anime.min.js"></script>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

<style>
.header{
      background-image: linear-gradient(to right, #e66465, #9198e5);
}

.ml7 {
  position: relative;
  font-weight: 1200;


}
.ml7 .text-wrapper {
  position: relative;
  display: inline-block;
  padding-top: 0.2em;
  padding-right: 0.05em;
  padding-bottom: 0.1em;
  overflow: hidden;
  padding-left: 14px;
  
}
.ml7 .letter {
  transform-origin: 0 100%;
  display: inline-block;
  line-height: 1.3em;
  font-size: 3.6em;
  color: #FFFFFF
}


</style>


<script>
// Wrap every letter in a span
$('.ml7 .letters').each(function(){
  $(this).html($(this).text().replace(/([^\x00-\x80]|\w)/g, "<span class='letter'>$&</span>"));
});

anime.timeline({loop: true})
  .add({
    targets: '.ml7 .letter',
    translateY: ["1.1em", 0],
    translateX: ["0.55em", 0],
    translateZ: 0,
    rotateZ: [180, 0],
    duration: 1050,
    easing: "easeOutExpo",
    delay: function(el, i) {
      return 50 * i;
    }
  }).add({
    targets: '.ml7',
    opacity: 0,
    duration: 1000,
    easing: "easeOutExpo",
    delay: 1000
  });
</script>


# Week 6
This week, we'll use those new mapping skills (and some old-fashioned problem solving) to tackle a breaking news challenge.

---

### Lecture

There is no lecture! No time! There's breaking news!

---

### Hands-on

We've got some piping-hot data: the latest unemployment figures for California.

You're the only data journalist around in the newsroom, and the editors want a map ASAP.

What do you do?

[Start here](https://qz.com/877432/the-us-unemployment-rate-measure-is-deceptive-and-doesnt-need-to-be/).

We'll go over how to wrangle that. And then you'll fire up QGIS to make a map of the rate by California county.

...

If we have time, we'll also make a comparison to February 2009.

([Here is something we might need later](https://data.ca.gov/dataset/ca-geographic-boundaries/resource/091ff50d-bb24-4537-a974-2ce89c6e8663)) 

---

### Links

* An example of [cool stuff](http://graphics.latimes.com/calmap-california-county-unemployment/) you can do with unemployment data.
* Quartz on [how the unemployment rate can mislead](https://qz.com/877432/the-us-unemployment-rate-measure-is-deceptive-and-doesnt-need-to-be/)

---

### Homework

* You are working on your Final Project
