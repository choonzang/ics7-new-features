# Tab

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_03.png)

탭별로 관련된 콘텐츠를 보여주는 구성에 적용할 수 있는 Action Component입니다.  슬롯의 갯수만큼 탭을 생성할 수 있으며, 하나의 슬롯 안에는 이미지, 서브타이틀, 타이틀, 설명글, 링크 정보를 포함하고 있습니다.&#x20;

## 참고 URL

[https://isd.i-on.net/new/ac/sample06/exam\_01.html](https://isd.i-on.net/new/ac/sample06/exam\_01.html)&#x20;

## Component 구성&#x20;

### 기본설정

Advanced Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%

### Advanced

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
      <span class="label">탭 이름</span>
      <input name="tab_name" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
    </div>
    <div style="display: flex; padding-top: 5px;">
      <span class="label">이미지</span>
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
      <span class="label">서브 타이틀</span>
      <input name="subtitle" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
    </div>    
    <div style="display: flex; padding-top: 5px;">
      <span class="label">타이틀</span>
      <input name="title" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
    </div>
    <div style="display:flex;padding-top: 5px;">
      <textarea name="content" style="flex: 1 1 0%; height: 50px;padding: 0 3px 0 3px;" placeholder="내용" ></textarea>
    </div>
    <div style="display: flex; padding-top: 5px;">
      <span class="label">바로가기 링크</span>
      <input name="link" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="http://">
      <span class="label" style="text-align: center;">정렬</span>
      <label class="el-select">
        <select name="link_target" style="width: 100px;"><option value="_self" selected="selected">직접링크</option><option value="_blank">새창링크</option></select>
      </label>
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
      tplEl.find('input[name=tab_name]').val(_item.tab_name);
      tplEl.find('input[name=imageUrl]').val(_item.imageUrl);
      tplEl.find('input[name=imageData]').val(_item.imageData);
      tplEl.find('span[name=imagefileName]').text(_item.imagefileName);
      tplEl.find('input[name=link]').val(_item.link);
      if(_item.link_target) tplEl.find('select[name=link_target]').val(_item.link_target);
      tplEl.find('input[name=title]').val(_item.title);
      tplEl.find('input[name=subtitle]').val(_item.subtitle);
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
		link_target : $(this).find('select[name=link_target]').val(),
		tab_name : $(this).find('input[name=tab_name]').val(),	
		subtitle : $(this).find('input[name=subtitle]').val(),		
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
                "link_target": "_self",
                "tab_name": "",
                "subtitle": "",
                "title": "전시관리가 편리한 커머스 솔루션",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
            },
            {
                "imageUrl": "",
                "imageData": "",
                "imagefileName": "",
                "link": "",
                "link_target": "_self",
                "tab_name": "",
                "subtitle": "",
                "title": "",
                "content": ""
            },
            {
                "imageUrl": "",
                "imageData": "",
                "imagefileName": "",
                "link": "",
                "link_target": "_self",
                "tab_name": "",
                "subtitle": "",
                "title": "",
                "content": ""
            },
            {
                "imageUrl": "",
                "imageData": "",
                "imagefileName": "",
                "link": "",
                "link_target": "_self",
                "tab_name": "",
                "subtitle": "",
                "title": "",
                "content": ""
            },
            {
                "imageUrl": "",
                "imageData": "",
                "imagefileName": "",
                "link": "",
                "link_target": "_self",
                "tab_name": "",
                "subtitle": "",
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
<div class="row justify-content-center">
  <div class="col-md-12 text-center margin-five-bottom">
    <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Advanced Component</span>
    <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
  </div>
</div>

<div class="row">
  <div class="col-12 tab-style-01 without-number wow animate__fadeIn">
    <!-- start tab navigation -->
    <ul class="nav nav-tabs text-uppercase justify-content-center text-center alt-font font-weight-500 margin-7-rem-bottom md-margin-5-rem-bottom sm-margin-20px-bottom">
      <!--li class="nav-item"><a class="nav-link"  data-bs-toggle="tab" href="#planning-tab">Planning</a><span class="tab-border bg-extra-dark-gray"></span></li-->
      <li class="nav-item" v-for="(node, index) of advancedData.slides">
        <a class="nav-link" v-bind:class="{active: index === 0}" data-bs-toggle="tab" :href="'#'+node.tab_name+'-tab'">{{node.tab_name}}</a>
        <span class="tab-border bg-extra-dark-gray"></span></li>
    </ul>
    <!-- end tab navigation -->
    <div class="tab-content">
      <!-- start tab item -->
      <div :id="''+node.tab_name+'-tab'" v-for="(node, index) of advancedData.slides"  v-bind:class="['tab-pane fade', (index === 0 ? 'in active show': '')]">
        <div class="row align-items-center">
          <div class="col-12 col-md-6 text-end sm-margin-40px-bottom">
            <img :src="node.imageData" alt="" />
          </div>
          <div class="col-12 col-lg-5 offset-lg-1 col-md-6 text-center text-sm-start">
            <span class="alt-font text-medium text-gradient-sky-blue-pink text-uppercase font-weight-500 margin-15px-bottom d-inline-block">{{node.subtitle}}</span>
            <h5 class="alt-font font-weight-600 text-extra-dark-gray margin-35px-bottom md-margin-30px-bottom">{{node.title}}</h5>
            <p class="w-85 lg-w-100">{{node.content}}</p>
            <a :href="node.link" class="btn btn-fancy btn-medium btn-dark-gray margin-20px-top">More</a>
          </div>
        </div>
      </div>
      <!-- end tab item -->
    </div>
  </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

```javascript
function isState(index) {
    if(index == 0) return true;
    else false;
}
```

### ㅇㄴ

