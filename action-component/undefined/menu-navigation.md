# Menu Navigation (준비중)

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_08.png)

## 샘플 URL

[https://isd.i-on.net/new/ac/sample05/exam\_02.html](https://isd.i-on.net/new/ac/sample05/exam\_02.html)

## Component 구성

### 기본정보&#x20;

Advanced Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### Advanced&#x20;

#### &#x20;Popup form (HTML)

```html
//
```

#### Javascript \[JSON -> form]

```javascript
//
```

#### Javascript \[form -> JSON]

```javascript
//
```



### vue.js

#### Sample Data

```json
{}
```

#### Template

```typescript
//
```



### JS

#### Add External javascript (CDN Links)

[https://unpkg.com/swiper@7/swiper-bundle.min.css](https://unpkg.com/swiper@7/swiper-bundle.min.css)



#### Javscript

```javascript
const swiper = new Swiper('.swiper', {
"centeredSlides": true, "spaceBetween": 60, "loop": true, "navigation": { "nextEl": ".swiper-button-next-nav-2", "prevEl": ".swiper-button-previous-nav-2" }, "autoplay": { "delay": "4500", "disableOnInteraction": false }, "keyboard": { "enabled": true, "onlyInViewport": true }, "breakpoints": { "991": { "slidesPerView": 2 }, "767": { "slidesPerView": 1 } }, "effect": "slide"
});
```

