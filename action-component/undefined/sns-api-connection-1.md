# SNS API Connection #1

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_06.png)

Instagram API를 연동하여, 포스트된 정보를 노출하는 구성입니다.&#x20;

서비스 API이용을 위해서는 Instagram 비즈니스 계정 및 Accesstoken을 얻기 위한 과정이 필요합니다. 관련된 내용은 아래의 Document를 참고해주세요.

API 관련 정보 URL : [https://developers.facebook.com/docs/instagram-basic-display-api](https://developers.facebook.com/docs/instagram-basic-display-api)

이 예제는 Advanced Type으로 마케터가 관련 키 관리나, 노출 포스트의 갯수 를 설정할 수 있도록 구현하였습니다.

## 샘플 URL&#x20;

[https://isd.i-on.net/new/ac/sample09/exam\_01.html](https://isd.i-on.net/new/ac/sample09/exam\_01.html)

## Component 구성&#x20;

### 기본설정

Advanced Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### Advanced&#x20;

#### &#x20;Popup form (HTML)

```html
<style>
#slidesjs-item-list { position: relative;}
#slidesjs-item-list > div.slidesjs-item {padding: 5px;border: solid 2px #eee;position: relative;border-color:#e6c37c;margin-bottom:3px;}
#slidesjs-item-list > span.button-add > a,
#slidesjs-item-list > div.slidesjs-item > span.button-del > a { font-size:12px; color:#fff;padding:4px 8px;opacity:0.6;border-radius: .2rem;cursor: pointer;z-index: 1;position: absolute;}
#slidesjs-item-list > span.button-add > a { left: 6px; top: 6px;background-color: #739e73; border-color:#659265;}
#slidesjs-item-list > div.slidesjs-item > span.button-del > a { right: 1px;bottom: 1px;background-color: #a90329; border-color:#900323;}
#slidesjs-item-list > span.button-add > a:hover, 
#slidesjs-item-list > div.slidesjs-item > span.button-del > a:hover {opacity:0.8;}
#slidesjs-item-list > div.slidesjs-item > div * { box-sizing: border-box;}
#slidesjs-item-list > div.slidesjs-item > div > input,
#slidesjs-item-list > div.slidesjs-item > div > textarea { padding: 6px 10px; height: 32px; background: #303131; border: none; border-radius: 2px; line-height: 20px; color: #fff; outline: none; min-width: 50px; font-size: 12px; }
#slidesjs-item-list > div.slidesjs-item > div > span.label { width: 160px; font-size: 12px; white-space: nowrap; line-height: 30px; }
#slidesjs-item-list > div.slidesjs-item > div > div > label > button.button-upload { line-height: 20px;cursor: pointer;width:100%;height:32px;background: #303131;border: none;border-radius: 2px;color:#fff; }
#slidesjs-item-list > div.slidesjs-item > div > div > label > button.button-upload:hover { background: #474848; }

</style>



<div id="slidesjs-item-add-template" style="display:block;">
<div id="slidesjs-item-list">
	<div class="slidesjs-item">           		
             <div style="display: flex; padding-top: 5px;">
 <span class="label">* Instagram Access Token</span>
			<input name="access_token" id="item_at" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
	      </div>
	
             <div style="display: flex; padding-top: 5px;">
 <span class="label">Count</span>
			<input name="loopcnt" type="text" id="item_lc" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
	      </div>
	</div>
</div>
</div> 
```

#### Javascript \[JSON -> form]

```javascript
$.each(_data.options, function(index, item) {
	addItem(item);
});
```

#### Javascript \[form -> JSON]

```javascript
var _slides = [];
var _options = [];

  $('#slidesjs-item-list > div.slidesjs-item').each(function (index, item) {
    _options.push({
      accesstoken : $('#item_at').val() ,
      loop_cnt : $('#item_lc').val()
      });
  });
  
  jsondata = JSON.stringify(_options[0].accesstoken);

  var token = _options[0].accesstoken;
  
  $.ajax({
    url: 'https://graph.instagram.com/me/media?fields=id,media_type,media_url,timestamp,permalink,comments_count,like_count&access_token=' + token,
    type: 'GET',
    async:false,
    success: function (response) {
    
      $.each(response.data, function(index,item){
        _slides.push({
          'id' : item.id,
          'mediatype' : item.media_type,
          'url' : item.media_url,
          'link' : item.permalink
        });
      });
      
    },
    error: function (data) {
      console.log('Please check Instagram Access token');
    }
  });

  return {
    slides: _slides,
    options : _options
  }
```



### vue.js

#### Sample Data

```json
{
    "advancedData": {
        "slides": [],
        "options": [
            {
                "accesstoken": "",
                "loop_cnt": "20"
            }
        ]
    },
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### Template

```typescript
<div class="row justify-content-center">
  <div class="col-md-12 text-center margin-six-bottom">
    <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Advanced Component</span>
    <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
  </div>
</div>
<div class="row justify-content-center">
  <div class="col-12">
    <ul class="portfolio-overlay portfolio-wrapper grid grid-4col xl-grid-4col lg-grid-4col md-grid-2col sm-grid-2col xs-grid-1col gutter-extra-large text-center">
      <li class="grid-sizer"></li>
      <!-- start lightbox gallery item -->
      <li class="grid-item wow animate__fadeIn" v-for="(node, index) of advancedData.slides" v-if="index < advancedData.options[0].loop_cnt" style="float:left;">
        <a :href="node.link" :title="node.id" data-group="lightbox-gallery" class="lightbox-group-gallery-item">
          <div class="portfolio-box">
            <div class="portfolio-image bg-gradient-sky-blue-pink">
              <video :src="node.url" alt="" v-if="node.mediatype === 'VIDEO'"></video>
              <img :src="node.url" alt="" v-else/>
              <div class="portfolio-hover justify-content-end d-flex flex-column padding-50px-tb lg-padding-30px-tb xs-padding-15px-tb">
                <i class="feather icon-feather-zoom-in portfolio-plus-icon font-weight-300 text-white absolute-middle-center icon-small move-top-bottom"></i>
              </div>
            </div>
          </div>
        </a>
      </li>
      <!-- end lightbox gallery item -->
    </ul>
  </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

(none)

#### Javscript

(none)
