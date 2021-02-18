This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app).

#### About
Learn how to create animated image slideshow using React and CSS3 transitions. Base on [React Image Slideshow Tutorial](https://www.youtube.com/watch?v=3ax9TW2c2bY). Big thanks you Ihatetomatoes youtube channel. 

#### Notes
- in App.css, in body { overflow-x: hidden; } so, we won't see horizontal scroll bar
- parent -> card-slider { position: relative }
- child -> card-slider-wrapper { position: absolute }
- Then, to move current active Card to the left, we can give card-slider-wrapper 
```{ left: - number % }``` that will offset the curr active card by number
- However, we actually will be using transition: transform indtead for a better performance. 
```{ transition: transform 300ms cubic-bezier(0.455, 0.03, 0.515, 0.955); } ```
this tranfrom property will gives us a nice smooth transition.
- in App.js, give in line style to div tag of card-slider-wrapper
```
 <div className="cards-slider-wrapper" 
  style={{
    'transform': `translateX(-${property.index*(100/properties.length)}%)`
  }}>
```
- Make sure translate is negative -> translateX(- number %) to be able to move card to the left.
- parent -> card-slider. We add class active-slide-${index number} to target active card that will be use in App.css
``` <div className={`cards-slider active-slide-${property.index}`}>```
- App.scss, Target Current active slide
from .active-slide-#{$i} Actvie card will have scale of (1) 
```
$i: 0;
@for $i from 0 through 29 {
    .cards-slider.active-slide-#{$i} #card-#{$i} {
      opacity: 1;
      transform: scale(1);
    }
}
```
- Unactive card will have scale of (0.8)
```
.card {
    opacity: 0.7;
    transform: scale(0.8);
}
```
- .details{} to control opacity of the detail info for active card and unactive card
- .col{} to give gredient effect to slides.