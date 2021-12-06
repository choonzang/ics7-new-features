# Accordians

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_04.png)

Accordians Type 구성입니다. 슬롯을 추가할수록 항목이 밑으로 증가 됩니다. FAQ메뉴에서 자주 사용되기도 하는데, 일정표형태로 구현된 Component입니다.&#x20;

하나의 슬롯 안에는 시간, 제목, 설명, 작성자의 정보를 관리하고 있습니다.&#x20;

## 참고 URL

[https://isd.i-on.net/new/ac/sample07/exam\_01.html](https://isd.i-on.net/new/ac/sample07/exam\_01.html)

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
      <span class="label">Time</span>
      <input name="time_schedule" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
    </div>
    <div style="display: flex; padding-top: 5px;">
      <span class="label">Title</span>
      <input name="title" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
    </div>
    <div style="display:flex;padding-top: 5px;">
      <textarea name="content" style="flex: 1 1 0%; height: 50px;padding: 0 3px 0 3px;" placeholder="내용" ></textarea>
    </div>
    <div style="display: flex; padding-top: 5px;">
      <span class="label">Writer</span>
      <input name="bywriter" type="text" style="flex: 1 1 0%; margin-right: 5px;" placeholder="">
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
      tplEl.find('input[name=time_schedule]').val(_item.time_schedule);
      tplEl.find('input[name=bywriter]').val(_item.writer);
      tplEl.find('input[name=title]').val(_item.title);
      tplEl.find('textarea[name=content]').val(_item.content);
    }
    
    $('#slidesjs-item-list').append(tplEl);
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
      time_schedule : $(this).find('input[name=time_schedule]').val(),
      writer : $(this).find('input[name=bywriter]').val(),
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
                "time_schedule": "08:00~09:00",
                "writer": "dsadasdasd",
                "title": "E-commerce for enterprise",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
            },
            {
                "time_schedule": "09:00~10:00",
                "writer": "",
                "title": "post covid-19 for enterprise",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
            },
            {
                "time_schedule": "10:00~12:00",
                "writer": "",
                "title": "Big Brother",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
            },
            {
                "time_schedule": "12:10~13:00",
                "writer": "",
                "title": "Solution for enterprise",
                "content": "ICE Commerce는 다변화되는 시장의 흐름에 대응 할 수 있는 최적의 커머스 솔루션입니다. 편리한 전시관리 기능을 기반으로 상품을 노출 시키고 수집 된 고객 데이터를 바탕으로 전략적인 마케팅 기획을 세울 수 있습니다."
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
  <div class="col-md-12 text-center margin-seven-bottom">
    <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Advanced Component</span>        
    <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
  </div>
</div>
<div class="row justify-content-center">
  <div class="col-12 col-lg-10 px-0">
    <div class="panel-group accordion-event accordion-style-04" id="accordion4" data-active-icon="icon-feather-minus" data-inactive-icon="icon-feather-plus">
      <!-- start accordion item -->
      <div class="panel border-color-black-transparent" v-for="(node, index) of advancedData.slides">

        <div v-bind:class="['panel-heading', (index === 0 ? 'active-accordion': '')]">
          <span class="panel-time">{{node.time_schedule}}</span>
          <a class="accordion-toggle" data-bs-toggle="collapse" data-bs-parent="accordion4" :href="'#accordion-style-4-'+(index+1)+''">
            <div class="panel-title">
              <span class="text-extra-dark-gray d-inline-block font-weight-700">{{node.title}}</span>
              <i v-bind:class="['text-extra-dark-gray feather', (index === 0 ? 'icon-feather-minus': 'indicator icon-feather-plus')]"></i>
            </div>
          </a>
          <span class="panel-speaker">{{node.writer}}</span>
        </div>

        <div :id="'accordion-style-4-'+(index+1)+''" v-bind:class="['panel-collapse collapse', (index === 0 ? 'show': '')]" data-bs-parent="#accordion4">
          <div class="panel-body">{{node.content}}</div>
        </div>
      </div>
      <!-- end accordion item -->

    </div>
  </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

(none)
