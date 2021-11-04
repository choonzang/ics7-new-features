# Text Slider

## 개요&#x20;

![](<../../.gitbook/assets/스크린샷 2021-11-03 오전 11.45.38.png>)

Text Slider 입니다. 슬라이더 방식으로 마우스를 이용하여 좌우 이동이 가능하고, 배경이미지, 속성, 타이틀, 내용을 출력해주는 구성입니다.

이 슬라이더의 관련된 옵션 및 사양은 아래의 링크를 참고 해주세요&#x20;

슬라이더 관련 참고URL : [https://lithohtml.themezaa.com/documentation/#slider](https://lithohtml.themezaa.com/documentation/#slider)



## 참고 URL

[https://isd.i-on.net/new/ac/sample01/exam\_01.html](https://isd.i-on.net/new/ac/sample01/exam\_01.html)



## Component 구성

### 기본정보&#x20;

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
#slidesjs-item-list > div.slidesjs-item > div > span.label { width: 80px; font-size: 12px; white-space: nowrap; line-height: 30px; }
#slidesjs-item-list > div.slidesjs-item > div > div > label > button.button-upload { line-height: 20px;cursor: pointer;width:100%;height:32px;background: #303131;border: none;border-radius: 2px;color:#fff; }
#slidesjs-item-list > div.slidesjs-item > div > div > label > button.button-upload:hover { background: #474848; }
</style>
<div id="slidesjs-item-list">
	<span class="button-add"><a onclick="javascript:addItem();" title="Add New Slide"><i class="fas fa-plus"></i></a></span>
</div>
<div id="slidesjs-item-add-template" style="display:none;">
	<div class="slidesjs-item">
		<div style="display: flex; padding-top: 5px;">
			<span class="label">배경이미지</span> 
			<div style="display: flex; flex: 1; ">
				<label class="el-select">
					<select name="imageUrlType">
						<option value="url">URL</option>
						<option value="file">FILE</option>
					</select>			
				</label>
				<label class="el-input label-imageUrl" style="flex: 1;margin-left: 5px;">
					<input type="text" name="imageUrl" placeholder="https://example.com/"/>
				</label>
				<label class="el-input label-imageUpload" style="flex: 1;margin-left: 5px;position:relative;display: none;">
					<input type="file" name="uploadFile" style="display: none;"/>
					<button class="button-upload" type="button" onclick="$(this).parent().find('input[name=uploadFile]').click();"><i class="fas fa-arrow-circle-up"></i><span>업로드</span></button>
				</label>
				<label class="el-input label-imageData" style="flex: 1;margin-left: 5px;position:relative;display: none;">
					<div class="el-input-result-box">
						<input name="imageData" type="hidden"/>
						<span name="imagefileName"></span>
						<i name="delImageData" class="fas fa-times"></i>
					</div>
				</label>
			</div>
		</div>
		<div style="display: flex; padding-top: 5px;">
			<span class="label">바로가기</span>
			<input name="link" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="http://">
			<span class="label" style="text-align: center;">정렬</span>
			<label class="el-select">
			<select name="text_align" style="width: 100px;"><option value="left" selected="selected">좌측</option><option value="rigth">우측</option></select>	
			</label>
		</div> 
		<div style="display: flex; padding-top: 5px;">
			<span class="label">제목</span>
			<input name="title" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
		</div>
		<div style="display:flex;padding-top: 5px;">
			<textarea name="content" style="flex: 1 1 0%; height: 50px;padding: 0 3px 0 3px;" placeholder="내용" ></textarea>
		</div>
		<span class="button-del" onmouseover="$(this).parent().css('border-color','#e6817c');" onmouseout="$(this).parent().css('border-color','#e6c37c');"><a onclick="delItem(this);"><i class="fas fa-trash-alt"></i></a></span>
	</div>
</div> 
<script>
	function delItem(_el){
		if(confirm("del?")) {
			$(_el).closest('.slidesjs-item').remove();
		}
	}

	function addItem(_item){
		var tplEl = $($('#slidesjs-item-add-template').html());

		if(_item) {
			tplEl.find('input[name=imageUrl]').val(_item.imageUrl);
			tplEl.find('input[name=imageData]').val(_item.imageData);
			tplEl.find('span[name=imagefileName]').text(_item.imagefileName);
			tplEl.find('input[name=link]').val(_item.link);
			if(_item.text_align) tplEl.find('select[name=text_align]').val(_item.text_align);
			tplEl.find('input[name=title]').val(_item.title);
			tplEl.find('textarea[name=content]').val(_item.content);
		}
		
		initImageUrlType(tplEl);
		//event
		tplEl.find('input[name=uploadFile]').change(changeImageFileFn);
		tplEl.find('select[name=imageUrlType]').change(changeImageUrlTypeFn);
		tplEl.find('i[name=delImageData]').click(delImageDataFn);
		
		$('#slidesjs-item-list').append(tplEl);
	}

	function changeImageUrlTypeFn(){
		var _topEl = $(this).parent().parent();
		initImageUrlType(_topEl);
	}

	function initImageUrlType(_topEl){
		if(_topEl.find('input[name=imageData]').val() == '') {
			_topEl.find('select[name=imageUrlType]').prop('disabled',false);
			if(_topEl.find('select[name=imageUrlType]').val() == 'url') {
				_topEl.find('.label-imageUrl').show();
				_topEl.find('.label-imageUpload').hide();
			} else {
				_topEl.find('.label-imageUrl').hide();
				_topEl.find('.label-imageUpload').show();
			}
			_topEl.find('.label-imageData').hide();
		} else {
			_topEl.find('select[name=imageUrlType] option[value=file]').prop('selected',true);
			_topEl.find('select[name=imageUrlType]').prop('disabled',true);
			
			_topEl.find('.label-imageUrl').hide();
			_topEl.find('.label-imageUpload').hide();
			_topEl.find('.label-imageData').show();
		}
	}

	function delImageDataFn(){
		var _topEl = $(this).parent().parent().parent().parent();
		_topEl.find('input[name=imageData]').val('');
		_topEl.find('select[name=imageUrlType] option[value=url]').prop('selected',true);
		initImageUrlType(_topEl);
	}

	function changeImageFileFn(){
		var _value = $(this).val(); 
		var ext =_value.split(".")[_value.split(".").length-1].toLowerCase() ;
		if (',jpg,gif,png,'.indexOf(',' + ext + ',') >= 0) {
			var _input = this;
			if (_input.files && _input.files[0]) { 
				var reader = new FileReader(); 
				reader.onload = function (e) {
					// console.info(e);
					var _topEl = $(_input).parent().parent();
					_topEl.find('input[name=imageUrl]').val('');
					_topEl.find('span[name=imagefileName]').text(_input.files[0].name);
					_topEl.find('input[name=imageData]').val(e.target.result);
					initImageUrlType(_topEl);
				}
				reader.readAsDataURL(_input.files[0]);  
			}
		} else {
			alert("Error..");
		}		
	}
</script>
```

#### Javascript \[JSON -> form]

```javascript
$.each(_data.slides, function(index, item) {
	addItem(item);
});
```

#### Javascript \[form -> JSON]

```javascript
var _slides = [];
$('#slidesjs-item-list > div.slidesjs-item').each(function (index, item) {
	_slides.push({
		imageUrl : $(this).find('input[name=imageUrl]').val(),
		imageData : $(this).find('input[name=imageData]').val(),
		imagefileName : $(this).find('span[name=imagefileName]').text(),
		link : $(this).find('input[name=link]').val(),
		text_align : $(this).find('select[name=text_align]').val(),
		title : $(this).find('input[name=title]').val(),
		content : $(this).find('textarea[name=content]').val()
	});
});
return {
	slides : _slides
}
```



### vue.js

#### Sample Data

```json
{
    "advancedData": {
        "slides": [
            {
                "imageUrl": "https://www.i-on.net/main/topbnnr/__icsFiles/afieldfile/2021/03/31/ionhompage_silde4.jpg",
                "imageData": "",
                "imagefileName": "",
                "link": "sdfsdf",
                "text_align": "left",
                "title": "전시관리가 편리한 커머스 솔루션",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
            },
            {
                "imageUrl": "",
                "imageData": "",
                "imagefileName": "",
                "link": "",
                "text_align": "left",
                "title": "",
                "content": ""
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
<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-md-12 text-center margin-five-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Advanced Component</span>
      <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
    </div>
  </div>

  <div class="row">
    <div class="swiper swiper-container slider-zoom-slide black-move p-0 h-550px lg-h-500px sm-h-600px" data-slider-options=''>
      <div class="swiper-wrapper">

        <div class="swiper-slide" v-for="(node, index) of advancedData.slides">
          <div class="col-12 p-0 cover-background align-items-end d-flex justify-content-end h-100" :style="'background-image: url(' + node.imageData + ');'">
            <div class="w-45 bg-white padding-5-rem-tb padding-5-half-rem-lr slider-zoom-content xl-w-55 xl-padding-3-rem-all lg-w-70 md-w-50 md-padding-5-rem-all sm-w-60 xs-w-95">
              <div class="col-12 p-0 margin-20px-bottom d-md-inline-block align-items-center justify-content-center">
                <span class="alt-font text-neon-orange d-inline-block font-weight-500 align-middle">{{index+1}}</span>
                <span class="w-30px h-1px d-inline-block align-middle bg-medium-gray margin-10px-left margin-10px-right"></span>
                <span class="d-inline-block alt-font text-neon-orange text-uppercase font-weight-500 align-middle">{{node.text_align}}</span>
              </div>
              <h6 class="alt-font align-self-center text-extra-dark-gray font-weight-500">{{node.title}}</h6>
              <p class="margin-35px-bottom">{{node.content}}</p>
              <a :href="node.link" class="btn btn-fancy btn-small btn-dark-gray">Link</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

[https://unpkg.com/swiper@7/swiper-bundle.min.css](https://unpkg.com/swiper@7/swiper-bundle.min.css)

[https://unpkg.com/swiper@7/swiper-bundle.min.js](https://unpkg.com/swiper@7/swiper-bundle.min.js)



#### Javscript

```javascript
const swiper = new Swiper('.swiper', {
"centeredSlides": true, "spaceBetween": 60, "loop": true, "navigation": { "nextEl": ".swiper-button-next-nav-2", "prevEl": ".swiper-button-previous-nav-2" }, "autoplay": { "delay": "4500", "disableOnInteraction": false }, "keyboard": { "enabled": true, "onlyInViewport": true }, "breakpoints": { "991": { "slidesPerView": 2 }, "767": { "slidesPerView": 1 } }, "effect": "slide"
});
```



