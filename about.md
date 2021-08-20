---
layout: page
title: About
permalink: /about/
images:
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210319_134639.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210328_151116.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210328_193036.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210423_185827.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210428_152921.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210522_104153.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210522_132429.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210522_135913.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/_[1].jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190307_163255.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190403_135126.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190419_165036.jpg"
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190507_192933.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190508_120417.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190525_133946.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190527_120258.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190527_120537.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190527_151832.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190527_161420.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20190529_191643.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20191124_092025.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20191207_090348.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20201112_160534.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20201113_111204.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210129_093400.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210129_100557.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/padri/main/assets/IMG_20210129_105749.jpg
  - image: https://raw.githubusercontent.com/steenblikrs/PADRI/main/assets/_%5B1%5D.jpg

---

PADRI was organized to support the research initiatives of Wenzhou-Kean University (WKU), Michael Graves College (MGC) faculty and students. It operates under the directive of making place ideal for humanity through research and technology. The Research Institute is currently working on local applied research projects in Zhejiang, China, as well as international research projects and competitions. The Michael Graves Collage wide Designing Public Spaces (DPS) research initiative is a main foci of our research agenda. For example the Wenruitang River Project (Sustainable development of vernacular historical districts in Wenzhou Area) is an ambitious and substantial part of DPS.

The Wenruitang River Project is a great example of the opportunities for young design students to engaging the community, and practice design methodology, in controlled yet real world scenarios, providing rapid feedback. This gives students the opportunity to learn in a very exciting, yet productive way. This is made possible through a focus on reinvigorating historic infrastructure, partnering with municipalities and key decision makers to propose innovative methods and interventions based on research and evaluation of existing conditions.

*There are numerous other funded research projects.


{% assign letterstring = "a,b,c,d,e,f,g,h,i,j,k,l,m,n" %}
{% assign letters = letterstring | split: ',' %}

<div class="carousel__holder">
    <div class="carousel">
        {% for item in site.data.carousel.images %}
          <input class="carousel__activator" type="radio" name="carousel" id="{{ letters[forloop.index0] }}" {% if forloop.first %}checked="checked"{% endif %} />
        {% endfor %}
        {% for item in site.data.carousel.images %}
          {% if forloop.index == forloop.length %}
            {% assign nextindex = 0 %}
          {% else %}
            {% assign nextindex = forloop.index0 | plus: 1 %}
          {% endif %}
          {% assign nextletter = letters[nextindex] %}
          {% if forloop.index0 == 0 %}
            {% assign previndex = forloop.length | minus: 1 %}
          {% else %}
            {% assign previndex = forloop.index0 | minus: 1 %}
          {% endif %}
          {% assign prevletter = letters[previndex] %}
          <div class="carousel__controls">
              <label class="carousel__control carousel__control--backward" for="{{ prevletter }}"></label>
              <label class="carousel__control carousel__control--forward" for="{{ nextletter }}"></label>
          </div>
        {% endfor %}
        <div class="carousel__track">
          <ul>
            {% for item in site.data.carousel.images %}
            <li class="carousel__slide" style="background-image: url('{{ item.image }}');"></li>
            {% endfor %}
          </ul>
        </div>
        <div class="carousel__indicators">
            {% for item in site.data.carousel.images %}
              <label class="carousel__indicator" for="{{ letters[forloop.index0] }}"></label>
            {% endfor %}
        </div>
    </div>
</div>

<style>
.carousel__holder {width: 100%; position: relative; padding-bottom: {{ include.height }}{{ include.unit }}; margin: 1rem 0 1rem;}
.carousel {
  height: 100%;
  width: 100%;
  overflow: hidden;
  text-align: center;
  position: absolute;
  padding: 0;
}
.carousel__controls,
.carousel__activator {
  display: none;
}
{% for item in site.data.carousel.images %}
.carousel__activator:nth-of-type({{ forloop.index }}):checked ~ .carousel__track {
  -webkit-transform: translateX(-{{ forloop.index0 }}00%);
          transform: translateX(-{{ forloop.index0 }}00%);
}
.carousel__activator:nth-of-type({{ forloop.index }}):checked ~ .carousel__slide:nth-of-type({{ forloop.index }}) {
  transition: opacity 0.5s, -webkit-transform 0.5s;
  transition: opacity 0.5s, transform 0.5s;
  transition: opacity 0.5s, transform 0.5s, -webkit-transform 0.5s;
  top: 0;
  left: 0;
  right: 0;
  opacity: 1;
  -webkit-transform: scale(1);
          transform: scale(1);
}
.carousel__activator:nth-of-type({{ forloop.index }}):checked ~ .carousel__controls:nth-of-type({{ forloop.index }}) {
  display: block;
  opacity: 1;
}
.carousel__activator:nth-of-type({{ forloop.index }}):checked ~ .carousel__indicators .carousel__indicator:nth-of-type({{ forloop.index }}) {
  opacity: 1;
}
{% endfor %}

.carousel__control {
  height: 30px;
  width: 30px;
  margin-top: -15px;
  top: 50%;
  position: absolute;
  display: block;
  cursor: pointer;
  border-width: 5px 5px 0 0;
  border-style: solid;
  border-color: #fafafa;
  opacity: 0.35;
  opacity: 1;
  outline: 0;
  z-index: 3;
}
.carousel__control:hover {
  opacity: 1;
}
.carousel__control--backward {
  left: 20px;
  -webkit-transform: rotate(-135deg);
          transform: rotate(-135deg);
}
.carousel__control--forward {
  right: 20px;
  -webkit-transform: rotate(45deg);
          transform: rotate(45deg);
}
.carousel__indicators {
  position: absolute;
  bottom: 20px;
  width: 100%;
  text-align: center;
}
.carousel__indicator {
  height: 15px;
  width: 15px;
  border-radius: 100%;
  display: inline-block;
  z-index: 2;
  cursor: pointer;
  opacity: 0.35;
  margin: 0 2.5px 0 2.5px;
}
.carousel__indicator:hover {
  opacity: 0.75;
}
.carousel__track {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  padding: 0;
  margin: 0;
  transition: -webkit-transform 0.5s ease 0s;
  transition: transform 0.5s ease 0s;
  transition: transform 0.5s ease 0s, -webkit-transform 0.5s ease 0s;
}
.carousel__track .carousel__slide {
  display: block;
  top: 0;
  left: 0;
  right: 0;
  opacity: 1;
}
{% for item in site.data.carousel.images %}
.carousel__track .carousel__slide:nth-of-type({{ forloop.index }}) {
  -webkit-transform: translateX({{ forloop.index0 }}00%);
          transform: translateX({{ forloop.index0 }}00%);
}
{% endfor %}

.carousel--scale .carousel__slide {
  -webkit-transform: scale(0);
          transform: scale(0);
}
.carousel__slide {
  height: 100%;
  position: absolute;
  opacity: 0;
  overflow: hidden;
}
.carousel__slide .overlay {height: 100%;}
.carousel--thumb .carousel__indicator {
  height: 30px;
  width: 30px;
}
.carousel__indicator {
  background-color: #fafafa;
}
{% for item in site.data.carousel.images %}
.carousel__slide:nth-of-type({{ forloop.index }}),
.carousel--thumb .carousel__indicators .carousel__indicator:nth-of-type({{ forloop.index }}) {
  background-size: cover;
  background-position: center;
}
{% endfor %}
</style>

<script>
  function isVisible(el) {
        while (el) {
            if (el === document) {
                return true;
            }

            var $style = window.getComputedStyle(el, null);

            if (!el) {
                return false;
            } else if (!$style) {
                return false;
            } else if ($style.display === 'none') {
                return false;
            } else if ($style.visibility === 'hidden') {
                return false;
            } else if (+$style.opacity === 0) {
                return false;
            } else if (($style.display === 'block' || $style.display === 'inline-block') &&
                $style.height === '0px' && $style.overflow === 'hidden') {
                return false;
            } else {
                return $style.position === 'fixed' || isVisible(el.parentNode);
            }
        }
  }
  {% if include.duration %}
  setInterval(function(){
    var j=0;
    var elements = document.querySelectorAll('.carousel__control--forward');
    for(i=(elements.length - 1);i>-1;i--) {
      if(isVisible(elements[i])) j=i;
    }
    elements[j].click();
  },{{ include.duration }}000);
  {% endif %}
</script>