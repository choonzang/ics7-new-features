# SNS API Component #2

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_06\_.png)

Instagram API를 연동하여, 포스트된 정보를 노출하는 구성입니다.&#x20;

서비스 API이용을 위해서는 Instagram 비즈니스 계정 및 Accesstoken을 얻기 위한 과정이 필요합니다. 관련된 내용은 아래의 Document를 참고해주세요.

API 관련 정보 URL : [https://developers.facebook.com/docs/instagram-basic-display-api](https://developers.facebook.com/docs/instagram-basic-display-api)

이 예제는 Basic Type으로 Post의 수, Slide Options, Template을 수정할 수 있도록 한 구성입니다.  코드를 직접수정할 수 있도록 입력필드로 되어있기 때문에 코드 내용에 대한 이해가 필요할 수 있습니다.



## 샘플 URL

[https://isd.i-on.net/new/ac/sample09/exam\_02.html](https://isd.i-on.net/new/ac/sample09/exam\_02.html)

## Component 구성&#x20;

### 기본설정

Basic Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### Advanced

필드는 3가지로 구성하였습니다.

1.  Post Number(텍스트)

    노출될 포스트의 전체 수를 정합니다.


2.  Slide Option (텍스트)

    타이틀 정보를 입력합니다.

    &#x20;
3.  Site Template (텍스트타입)

    사용자가 볼수 있는 템플릿 소스를 입력합니다.

### vue.js

#### Sample Data

```json
{
    "posted_num": "20",
    "slider_options": "{\"loop\": true, \"slidesPerView\": 6, \"spaceBetween\": 15, \"autoplay\": { \"delay\": 3500, \"disableOnInteraction\": false },  \"keyboard\": { \"enabled\": true, \"onlyInViewport\": true }, \"pagination\": { \"el\": \".swiper-pagination\", \"clickable\": true, \"dynamicBullets\": true }, \"navigation\": { \"nextEl\": \".swiper-button-next\", \"prevEl\": \".swiper-button-prev\" }, \"breakpoints\": { \"1200\": { \"slidesPerView\": 6 }, \"992\": { \"slidesPerView\": 3 }, \"768\": { \"slidesPerView\": 3 } } }",
    "slide_template": "<figure><a href=\"#\" data-href=\"{{link}}\" target=\"_blank\"><img src=\"#\" data-src=\"{{image}}\" class=\"insta-image\" alt=\"\" /><span class=\"insta-counts\"><i class=\"fab fa-instagram\"></i>{{likes}}</span></a></figure>",
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### 템플릿

```html
<div class="row justify-content-center">
    <div class="col-md-12 text-center margin-seven-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
        <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
    </div>
</div>
<div class="row align-items-center justify-content-center">
    <div class="col-12 text-center">
        <div class="instagram-follow-api swiper-container">
            <div class="swiper-wrapper instafeed-grid instafeed-wrapper" :data-total="posted_num" :data-slider-options="slider_options">
                <div class="swiper-slide" v-html="slide_template"></div>
            </div>
            <div class="instagram-title alt-font absolute-middle-center bg-white text-extra-dark-gray border-radius-2px letter-spacing-1px font-weight-500 text-medium text-uppercase">#Instagram decor</div>
        </div>
    </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

```javascript
var isotopeObjs     = [];
var instadata = [];
var instagramWrapperItems = document.querySelectorAll('.instafeed-wrapper');
    instagramWrapperItems.forEach( function(instagramWrapperItem, index) {
        var token = '(Access Token Value)', //Token을 업데이트함
            _this = $( instagramWrapperItem ),
            token = _this.attr( 'data-token' ) || token,
            total = _this.attr( 'data-total' ) || '9', // default photo item number
            slider= _this.attr( 'data-slider-options' ),
            _html = _this.html(),
            outputHTML = '';
        if ( typeof ( slider ) !== 'undefined' && slider !== null ) {
            _this.html( '' );
        }
        $.ajax({
            url: 'https://graph.instagram.com/me/media?fields=id,media_type,media_url,timestamp,permalink,comments_count,like_count&access_token=' + token,
            type: 'GET',
            async:false,
            success: function ( response ) {
                outputHTML += _this.find( '.grid-item' ).length > 0 ? '<li class="grid-sizer"></li>' : '';
                for ( var x in response.data ) {
                    if ( x < parseInt( total ) ) {
                        if ( response.data[x]['media_type'] == 'IMAGE' || response.data[x]['media_type'] == 'CAROUSEL_ALBUM') {
                            var link    = response.data[x]['permalink'] || '',
                                image   = response.data[x]['media_url'] || '',
                                likes   = response.data[x]['like_count'] || '',
                                comments= response.data[x]['comments_count'] || '',
                                mediatype =    response.data[x]['media_type'] || '',
                                output  = _html;

                            output  = output.replace( ' href="#"', '' );
                            output  = output.replace( ' src="#"', '' );
                            output  = output.replace( 'data-href', 'href' );
                            output  = output.replace( 'data-src', 'src' );
                            output  = output.replace( '{{type}}', mediatype );
                            output  = output.replace( '{{link}}', link );
                            output  = output.replace( '{{image}}', image );
                            output  = output.replace( '{{likes}}', likes );
                            output  = output.replace( '{{comments}}', comments );
                            outputHTML += output;
                        }
                    }
                }
                instadata.push(response.data);

                _this.html( outputHTML );
                if ( typeof ( slider ) !== 'undefined' && slider !== null ) {
                    // Apply swiper
                    var sliderOptions   = $.parseJSON( slider );
                    var swiperObj       = instagramWrapperItem.parentElement;
                    new Swiper( swiperObj, sliderOptions );
                } else {
                    // Apply isotope
                    if( ! _this.find( '.wow' ).length > 0 ) {
                        _this.find( '.grid-item' ).css( 'visibility', 'hidden' );
                    }
                    _this.imagesLoaded(function () {
                        if( ! _this.find( '.wow' ).length > 0 ) {
                            _this.find( '.grid-item' ).css( 'visibility', '' );
                        } else if( ! isMobile ) {
                            _this.find( '.grid-item' ).css( 'visibility', 'hidden' );
                        }
                        _this.removeClass( 'grid-loading' );
                        _this.isotope({
                            layoutMode: 'masonry',
                            itemSelector: '.grid-item',
                            percentPosition: true,
                            stagger: 0,
                            masonry: {
                                columnWidth: '.grid-sizer',
                            }
                        });
                        isotopeObjs.push( _this );
                    });
                }
            },
            error: function (data) {
                var output = '<div class="col-12"><span class=text-center>No Images Found</span></div>';
                _this.append( output );
            }
        });
    });

```
