<h1 class="ml7">
  <span class="text-wrapper">
    <span class="letters"><p id ="usc p">Data Journalism USC 2019</p></span>
  </span>
</h1>

<script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/2.0.2/anime.min.js"></script>

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>

<style>
.ml7 {
  position: relative;
  font-weight: 1200;
  font-size: 5.9em;
    background-image: linear-gradient(to top, #990000 , #FFCC00);   

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
  color: #FFFFFF
}

.usc-p{
   font-size: 5.9em;
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

Welcome to the website for JOUR 561: Fundamentals of Data                   Journalism Reporting. You'll find links to course materials here. You can get to this page by typing in `http://tiny.cc/usc-data` in your browser's address bar.

Here is [the class syllabus](docs/syllabus.pdf).

The class meets 6:30 to 8:30 on Wednesday nights, and the final is on May 1 from 7-9 p.m.

## Class links

* **[Week One](week1/)**: Course overview. Introductions.
* Week Two: Class Project discussion.
* Week Three: Mapping Part 1 – Buffers on steroids, spatial queries and spatial joins.
* Week Four: Class Project discussion.
* Week Five: Mapping Part 2 - Projections and the finer points of mapping.
* Week Six: Mapping Part 3 – Using Open Street Map and Plug-Ins.
* Week Seven: Mapping Part 4 – Interactive Maps. Class project discussion.
* Week Eight: Bulk geocoding data with an API.
* Week Nine: Overview of Jupyter Notebook and R Kernel. Using Markdown and Github.
* Spring Break
* Week Ten: Visualizing Data with ggplot2, Part 1 – faceting. Class project discussion.
* Week Eleven: Visualizing Data with ggplot2, Part 2 – layers and interactivity.
* Week Twelve: Writing functions and loops in R.
* Week Thirteen: Tidyuniverse in R – cleaning and transforming data.
* Week Fourteen: Tidyuniverse in R – modeling data. Class project discussion.
* Week Fifteen: TidyCensus in R – the best way to reign in Census data.
* Final



```

 .----------------.  .----------------. 
| .--------------. || .--------------. |
| |  ________    | || |      __      | |
| | |_   ___ `.  | || |     /  \     | |
| |   | |   `. \ | || |    / /\ \    | |
| |   | |    | | | || |   / ____ \   | |
| |  _| |___.' / | || | _/ /    \ \_ | |
| | |________.'  | || ||____|  |____|| |
| |              | || |              | |
| '--------------' || '--------------' |
 '----------------'  '----------------' 
 .----------------.  .----------------. 
| .--------------. || .--------------. |
| |  _________   | || |      __      | |
| | |  _   _  |  | || |     /  \     | |
| | |_/ | | \_|  | || |    / /\ \    | |
| |     | |      | || |   / ____ \   | |
| |    _| |_     | || | _/ /    \ \_ | |
| |   |_____|    | || ||____|  |____|| |
| |              | || |              | |
| '--------------' || '--------------' |
 '----------------'  '----------------' 


```

---

Us in this class when learning about new datasets we can FOIA:

![](https://media.giphy.com/media/5GoVLqeAOo6PK/giphy.gif)