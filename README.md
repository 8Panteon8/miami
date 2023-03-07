# Miami slider

>The Swiperjs parameter `freeMode` does not behave correctly in Safari 

## Settings swiper

- **Swiper one for photos**:

```javascript
const sliderMain = new Swiper(".slider_main", {
  freeMode: true,
  centeredSlides: true,
  mousewheel: true,
  parallax: true,
  breakpoints: {
    0: {
      slidesPerView: 2.5,
      spaceBetween: 20,
    },
    600: {
      slidesPerView: 3.5,
      spaceBetween: 60,
    },
  },
});
const sliderBg = new Swiper(".slider_bg", {
  centeredSlides: true,
  parallax: true,
  spaceBetween: 60,
  slidesPerView: 3.5,
});
```
>Slides have different percentages to organize the window effect 

```html
data-swiper-parallax="20%"
data-swiper-parallax="30%"
```
 - **Second swiper for background**:

```javascript
document.querySelectorAll(".slider__item").forEach((item) => {
  item.addEventListener("click", (evant) => {
    item.classList.toggle("opened");
  });
});

let desc = document.querySelector(".description");

sliderMain.on("slideChange", (e) => {
  sliderMain.activeIndex > 0
    ? desc.classList.add("hidden")
    : desc.classList.remove("hidden");
});
```
>Don't forget to connect the sliders

```javascript
sliderMain.controller.control = sliderBg;
```

>Slider_bg styling

```css
.slider_bg {
  z-index: 0;
  transform: rotate(-20deg) !important;
  top: -90vh;
  left: -10vh;
  opacity: 0.15;
  filter: blur(120px) saturate(10);
}

```



## Screenshot
![ezgif com-video-to-gif](https://user-images.githubusercontent.com/113831614/223418018-d5387593-acb7-4107-9820-3d04b621b5d8.gif)
