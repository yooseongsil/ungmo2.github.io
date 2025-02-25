---
layout: fs-post
title: <strong>Carousel slider</strong>
categories: fastcampus-ui-component
section: fastcampus-ui-component
seq: 11
permalink: /:categories/:title
description:
---

캐러셀(Carousel)은 슬라이드 형태의 컨텐츠를 순환하며 표시하는 UI를 말한다. [캐러셀은 비생산적인 디자인 패턴](https://brunch.co.kr/@ebprux/41)이라는 주장이 있기도 하지만 사용자가 스크롤을 내리지 않은 상태에서도 많은 정보를 노출할 수 있는 장점이 있어 많은 웹사이트에서 사용하고 있다.

![porsche](/img/porsche.gif)
{: .w-650}

[Porsche 메인페이지의 캐러셀](https://www.porsche.com/usa/)
{: .desc-img}

시중에는 jQuery 기반의 캐러설 플러그인이 다수 존재하고 이들로 멋진 캐러셀을 만들 수 있다. jQuery에 의존성 없이 사용할 수 있는 캐러셀을 만들어보자.

우리가 작성할 캐러셀의 최종 모습은 아래와 같다.

![carousel-slider](/assets/fs-images/exercise/carousel.gif)
{: .w-350}

캐러셀 슬라이더
{: .desc-img}

요구 사항은 아래와 같다.

1. 무한 루핑 기능을 지원한다.
2. 슬라이딩 애니메이션을 지원한다.
3. 각 슬라이드의 width/height는 가변적이다. 단, 모든 슬라이드의 width/height는 동일하다.
4. 슬라이드 이동 버튼을 연타해도 이상없이 동작해야 한다.
5. 캐러셀 슬라이더를 표시할 HTML 요소와 슬라이드 이미지의 url로 구성된 배열을 전달하면 동적으로 캐러셀 슬라이더를 생성한다.

뷰의 기본 템플릿은 다음과 같다.

이미지 파일 링크

- <a href="http://poiemaweb.com/assets/fs-images/exercise/movies/movie-1.jpg">movie-1.jpg</a>
- <a href="http://poiemaweb.com/assets/fs-images/exercise/movies/movie-2.jpg">movie-2.jpg</a>
- <a href="http://poiemaweb.com/assets/fs-images/exercise/movies/movie-3.jpg">movie-3.jpg</a>
- <a href="http://poiemaweb.com/assets/fs-images/exercise/movies/movie-4.jpg">movie-4.jpg</a>

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <link href="https://fonts.googleapis.com/css?family=Open+Sans:300,400" rel="stylesheet" />
    <title>Carousel Slider</title>
    <style>
      *,
      *::after,
      *::before {
        box-sizing: border-box;
      }
      body {
        font-family: 'Open Sans';
        font-weight: 300;
        color: #58666e;
        background-color: #f0f3f4;
      }
      .title {
        color: #db5b33;
        font-weight: 300;
        text-align: center;
      }
      /* 캐러셀의 window 역할을 한다. */
      .carousel {
        position: relative;
        margin: 0 auto;
        overflow: hidden;
        /* carousel 요소의 width 셋팅이 완료될 때까지 감춘다. */
        opacity: 0;
      }
      .carousel-slides {
        --currentSlide: 0;
        --duration: 0;
        /* 수평 정렬 */
        display: flex;
        transition: transform calc(var(--duration) * 1ms) ease-out;
        transform: translate3D(calc(var(--currentSlide) * -100%), 0, 0);
      }
      .carousel-slides img {
        padding: 5px;
      }
      /* carousel의 prev, next 버튼 */
      .carousel-control {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        font-size: 2em;
        color: #fff;
        background-color: transparent;
        border-color: transparent;
        cursor: pointer;
        z-index: 99;
      }
      .carousel-control:focus {
        outline: none;
      }
      /* carousel의 prev 버튼 */
      .carousel-control.prev {
        left: 0;
      }
      /* carousel의 next 버튼 */
      .carousel-control.next {
        right: 0;
      }
    </style>
  </head>
  <body>
    <h1 class="title">Carousel Slider</h1>
    <div class="carousel">
      <!-- <div class="carousel-slides">
        <img src="movies/movie-4.jpg">
        <img src="movies/movie-1.jpg">
        <img src="movies/movie-2.jpg">
        <img src="movies/movie-3.jpg">
        <img src="movies/movie-4.jpg">
        <img src="movies/movie-1.jpg">
      </div>
      <button class="carousel-control prev">&laquo;</button>
      <button class="carousel-control next">&raquo;</button> -->
    </div>
    <script>
      const carousel = ($container, images) => {};

      carousel(document.querySelector('.carousel'), [
        'movies/movie-1.jpg',
        'movies/movie-2.jpg',
        'movies/movie-3.jpg',
        'movies/movie-4.jpg'
      ]);
    </script>
  </body>
</html>
```
