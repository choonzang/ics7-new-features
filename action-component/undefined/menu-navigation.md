# Menu Navigation

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_09.png)

Menu Navigation 형태의 Action Component입니다. 마케터는 자유롭게 메뉴를 구성할 수 있으며, 뎁스 및 정렬을 하여 저장하면 됩니다. &#x20;

Action Component내에서 메뉴를 생성 하고, 정렬을 하게 되면 JSON 형식을 Component에 보내게 되고, 이를 사용자 화면에 보여지도록 합니다.&#x20;

## 샘플 URL

[https://isd.i-on.net/new/ac/sample05/exam\_01.html](https://isd.i-on.net/new/ac/sample05/exam\_01.html)

## Component 구성

### 기본정보&#x20;

Advanced Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### Advanced&#x20;

#### &#x20;Popup form (HTML)

```html
<style>
.dd {
  position: relative;
  display: inline-block;
  margin: 0;
  padding: 0;
  width: 100%;
  list-style:  none;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  font-size:   13px;
  line-height: 20px;
}

.dd-edit-box input,
  /*.dd-edit-box select,*/
.dd-edit-box textarea {
  border:             none;
  -webkit-box-shadow: none;
  -moz-box-shadow:    none;
  box-shadow:         none;
  background:         transparent;
  text-overflow:      ellipsis;
  outline:            none;
  font-size:          13px;
  color:              #444;
  text-shadow:        0 1px 0 #fff;
  width:              30%;
}

.dd-edit-box input::selection,
.dd-edit-box textarea::selection {
  color: #fff;
  background: #0e90d2;
}

.dd-edit-box input:focus,
.dd-edit-box textarea:focus {
  text-shadow: none;
}
.dd-button-container .custom-button-example {
  color: #000;
  text-align: center;
  padding: 1px 4px;
}

.dd-button-container > div {
  background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0.51), rgba(0, 0, 0, 0.14));
  border: 1px solid #898989;
  border-radius: 2px;
  font: normal 12px/18px Helvetica, Lato, Arial sans-serif;
  cursor: pointer;
  float: left;
  width: 20px;
  height: 20px;
  margin-right: 3px;
}


.dd-edit-box select {
  width: 30%;
}

.dd-edit-box > * {
  vertical-align: top;    
}

.dd-edit-box input, .dd-edit-box select, .dd-edit-box textarea {
  margin-bottom: 0;
}

.dd-edit-box {
  position: relative;
}

.dd-edit-box i {
  right:    0;
  overflow: hidden;
  cursor:   pointer;
  position: absolute;
  font-style: normal;
}

.dd-item-blueprint {
  display: none;
}

.dd > .dd-list {
  min-height: 80px;
}

.dd-list {
  display:    block;
  position:   relative;
  margin:     0;
  padding:    0;
  list-style: none;
}

.dd-list .dd-list {
  left: 30px;
  margin-right: 30px;
}

.dd-collapsed .dd-list {
  display: none;
}

.dd-item,
.dd-empty,
.dd-placeholder {
  text-shadow: 0 1px 0 #fff;
  display:     block;
  position:    relative;
  margin:      0;
  padding:     0;
  min-height:  20px;
  font-size:   13px;
  line-height: 20px;
}

.dd-handle {
  cursor:                move;
  display:               block;
  margin:                5px 0;
  padding:               5px 10px;
  color:                 #333;
  text-decoration:       none;
  font-weight:           bold;
  border:                1px solid #aaa;
  background:            #c8c8c8;
  background:            -webkit-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background:            -moz-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background:            linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  -webkit-border-radius: 3px;
  border-radius:         3px;
  box-sizing:            border-box;
  -moz-box-sizing:       border-box;
}

.dd-handle:hover {
  color:      #2ea8e5;
  background: #fff;
}

.dd-item > button {
  display:     inline-block;
  position:    relative;
  cursor:      pointer;
  float:       left;
  width:       24px;
  height:      20px;
  margin:      5px 5px 5px 30px;
  padding:     0;
  white-space: nowrap;
  overflow:    hidden;
  border:      0;
  background:  transparent;
  font-size:   12px;
  line-height: 1;
  text-align:  center;
  font-weight: bold;
  color:       black;
}

.dd.domenu .dd-new-item {
    background: transparent;
    border: 3px dotted #8F8F8F;
    border-radius: 11px;
    width: 100%;
    height: 35px;
    font-size: 29px;
    color: #8F8F8F;
    outline: none;
    text-align: center;
}

.dd-item .item-remove,
.dd-item .item-remove-confirm,
.dd-item .item-add {
  outline: none;
}

.dd-item .dd-button-container button {
  background-image: linear-gradient(to bottom, rgba(255, 255, 255, 0.51), rgba(0, 0, 0, 0.14));
  border:           1px solid #898989;
  border-radius:    2px;
  font:             normal 12px/18px Helvetica, Lato, Arial sans-serif;
  cursor:           pointer;
}

.dd-item .dd-button-container .item-add {
  background-color: #55b3ff;
  border-color:     #376f9c;
  color:            #ffffff;
  text-shadow:      0 1px 0 #2b77b5;
  box-shadow:       inset 0 1px 0 #cfe9ff;
  text-align: center;
}

.dd-item .dd-button-container .item-add:active {
  box-shadow: inset 0 1px 3px #376f9c;
}

.dd-item .dd-button-container .item-remove {
  background-color: #ff5555;
  border-color:     #a54b4b;
  color:            #5a1111;
  text-shadow:      0 1px 0 #ffc0c0;
  box-shadow:       inset 0 1px 0 #ffc0c0;
  transition:       background-color 0.35s;
  text-align: center;
}

.dd-item .dd-button-container .item-remove:active {

  box-shadow: inset 0 1px 5px #a54b4b;
}

.dd-item .dd-button-container .item-remove-confirm {

  background-color: #ffa155;

  transition:       background-color 0.35s;

  border-color:     #ad7232;
}

.dd-item .dd-button-container .item-remove-confirm:active {

}

.item-remove-confirm {
  background: #ffce66;
}

.dd-item .dd-button-container {
  position: absolute;
  height:   19px;
  padding:  0 5px;
  top:      4px;
  overflow: visible;
  display:  none;
  right:    0;
  z-index: 9999;
}


.dd3-item > button:first-child {
  margin-left: 30px;
}

.dd-item > button:before {
  display:     block;
  position:    absolute;
  width:       100%;
  text-align:  center;
  text-indent: 0;
}

.dd-placeholder,
.dd-empty {
  margin:          5px 0;
  padding:         0;
  min-height:      30px;
  background: #D6F2FF;
  border: 1px dashed #6C9AB1;
  box-sizing:      border-box;
  -moz-box-sizing: border-box;
}

.dd-placeholder.max-depth {
  background: #ffb3b7;
  border: 1px dashed #b14444;
}

.dd-empty {
  border:              1px dashed #bbb;
  min-height:          100px;
  background-color:    #e5e5e5;
  background-image:    -webkit-linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff),
                       -webkit-linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff);
  background-image:    -moz-linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff),
                       -moz-linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff);
  background-image:    linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff),
                       linear-gradient(45deg, #fff 25%, transparent 25%, transparent 75%, #fff 75%, #fff);
  background-size:     60px 60px;
  background-position: 0 0, 30px 30px;
}

.dd-dragel {
  height:         60px;
  position:       absolute;
  pointer-events: none;
  z-index:        9999;
}

.dd-dragel > .dd-item .dd-handle {
  margin-top: 0;
}

.dd-dragel .dd-handle {
  -webkit-box-shadow: 2px 4px 6px 0 rgba(0, 0, 0, .1);
  box-shadow:         2px 4px 6px 0 rgba(0, 0, 0, .1);
}



.dd3-content {
  display:               block;
  /*height:                100%;*/
  margin:                5px 0;
  padding:               5px 10px 5px 40px;
  color:                 #333;
  text-decoration:       none;
  font-weight:           bold;
  border:                1px solid #ccc;
  border:                1px solid #898989;
  background:            #fafafa;
  background:            -webkit-linear-gradient(top, #f4f4f4 10%, #c9c9c9 100%);
  background:            -moz-linear-gradient(top, #f4f4f4 10%, #c9c9c9 100%);
  background:            linear-gradient(top, #f4f4f4 10%, #c9c9c9 100%);
  -webkit-border-radius: 3px;
  border-radius:         3px;
  box-sizing:            border-box;
  -moz-box-sizing:       border-box;
}

.dd3-content:hover {
  color:      #2ea8e5;
  background: #c8c8c8;
  background: -webkit-linear-gradient(top, #e5e5e5 10%, #ffffff 100%);
  background: -moz-linear-gradient(top, #e5e5e5 10%, #ffffff 100%);
  background: linear-gradient(top, #e5e5e5 10%, #ffffff 100%);
}

.dd-dragel > .dd3-item > .dd3-content {
  margin: 0;
}

.dd3-handle {
  position:                   absolute;
  margin:                     0;
  left:                       0;
  top:                        0;
  cursor:                     move;
  width:                      30px;
  text-indent:                100%;
  white-space:                nowrap;
  overflow:                   hidden;
  border:                     1px solid #807b7b;
  text-shadow:                0 1px 0 #807b7b;
  background:                 #c8c8c8;
  background:                 -webkit-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background:                 -moz-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background:                 linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  border-top-right-radius:    0;
  border-bottom-right-radius: 0;
}

.dd3-handle:before {
  content:     '\2263';
  display:     block;
  position:    absolute;
  left:        0;
  top:         3px;
  width:       100%;
  text-align:  center;
  text-indent: 0;
  color:       #fff;
  font-size:   20px;
  font-weight: normal;
}

.dd3-handle:hover {
  background: #c8c8c8;
  background: -webkit-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background: -moz-linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
  background: linear-gradient(top, #c8c8c8 0%, #8c8c8c 100%);
}

.dd3-content:hover .dd-button-container {
  display:    block;
  transition: display 2s;
}

.dd .dd-new-item {
    width: 100%;
    border: 2px dashed #BDBDBD;
    background: transparent;
    border-radius: 3px;
    font-size: 21px;
    color: #BDBDBD;
    cursor: pointer;
    transition: border 0.35s ease 0s, color 0.35s ease 0s;
    outline: none;
    padding-bottom: 5px;
    text-align: center;
}

.dd .dd-new-item:hover {
    border: 2px dashed #595858;
    color: #595858;
    transition: border 0.35s ease 0s, color 0.35s ease 0s;
}

.collapse{
    display: inline-block;
    position: relative;
    cursor: pointer;
    float: left;
    
    margin: 5px 5px 5px 30px;
    padding: 0;
    white-space: nowrap;
    overflow: hidden;
    border: 0;
    background: transparent;
    font-size: 12px;
    line-height: 1;
    text-align: center;
    font-weight: bold;
    color: black;
}

.expand{
    display: inline-block;
    position: relative;
    cursor: pointer;
    float: left;
    
    margin: 5px 5px 5px 30px;
    padding: 0;
    white-space: nowrap;
    overflow: hidden;
    border: 0;
    background: transparent;
    font-size: 12px;
    line-height: 1;
    text-align: center;
    font-weight: bold;
    color: black;
}
</style>


<section>
<h3 id="user-menu">User menu</h3>
  <div class="dd" id="domenu-1">
    <div id="domenu-add-item-btn" class="dd-new-item">+</div>
    <li class="dd-item-blueprint">
      <div class="collapse" data-action="collapse" type="button" style="display: none;"></div>
      <div class="expand" data-action="expand" type="button" style="display: none;"></div>
      <div class="dd-handle dd3-handle">&nbsp;</div>
      <div class="dd3-content">
        <span class="item-name">[item_name]</span>
        <div class="dd-button-container">
          <div class="custom-button-example">&#x270E;</div>
          <div class="item-add">+</div>
          <div class="item-remove" data-confirm-class="item-remove-confirm">&times;</div>
        </div>
        <div class="dd-edit-box" style="display: none;">
          <input type="text" name="title" autocomplete="off" placeholder="Item"
                 data-placeholder="Any nice idea for the title?"
                 data-default-value="Menu List Item. {?numeric.increment}">
          <!--select name="custom-select">
            <option>select something...</option>
          </select-->
          <input type="text" name="custom-select" placeholder="link">
          <i class="end-edit">save</i>
        </div>
      </div>
    </li>

    <ol class="dd-list"></ol>
  </div>

    
  <div id="domenu-1-output" class="output-preview-container">
    <h4>JSON Output Preview (User menu)</h4>
    <textarea style="width: 100%;min-height: 150px;color: #FFF;background-color: #5e5e5e;font-size: 12px;" name="jsonOutput" class="jsonOutput"></textarea>
    <!--
    <input type="checkbox" name="keepchages" class="keepChanges" checked> Keep changes after page reload (localStorage)
    <br><br>
  -->
    <!--input type="button" name="clearLocalStorage" class="clearLocalStorage" value="Clear localStorage"-->
    <br/>
  </div>
</section>

<script src="https://isd.i-on.net/new/js/select2.js"></script>
<script src="https://isd.i-on.net/new/js/domenu_js.js"></script>
```

#### Javascript \[JSON -> form]

```javascript
$(document).ready(function() {

    var $domenu            = $('#domenu-1'),
        domenu             = $('#domenu-1').domenu(),
        $outputContainer   = $('#domenu-1-output'),
        $jsonOutput        = $outputContainer.find('.jsonOutput'),
        $keepChanges       = $outputContainer.find('.keepChanges'),
        $clearLocalStorage = $outputContainer.find('.clearLocalStorage');

	$domenu.domenu({
        slideAnimationDuration: 0,
        allowListMerging: ['domenu-2'],
        select2:                {
          support: true,
          params:  {
            tags: true
          }
        },
        data:                   JSON.stringify(_data.slides) || '[{"title":"Account","customSelect":"select something...","select2ScrollPosition":{"x":0,"y":0}},{"title":"Settings","customSelect":"select something...","select2ScrollPosition":{"x":0,"y":0}},{"title":"Call","customSelect":"select something..."},{"title":"Support","customSelect":"select something..."},{"title":"Email","customSelect":"select something..."},{"title":"Orders","customSelect":"select something..."},{"title":"Manage","customSelect":"select something..."},{"title":"Settings","customSelect":"select something..."}]'
    })
    
      // Example: initializing functionality of a custom button #21
      .onCreateItem(function(blueprint) {
        // We look with jQuery for our custom button we denoted with class "custom-button-example"
        // Note 1: blueprint holds a reference of the element which is about to be added the list
        var customButton = $(blueprint).find('.custom-button-example');

        // Here we define our custom functionality for the button,
        // we will forward the click to .dd3-content span and let
        // doMenu handle the rest
        customButton.click(function() {
          blueprint.find('.dd3-content span').first().click();
        });
      })
      // Now every element which will be parsed will go through our onCreateItem event listener, and therefore
      // initialize the functionality our custom button
      .parseJson()
      .on(['onItemCollapsed', 'onItemExpanded', 'onItemAdded', 'onSaveEditBoxInput', 'onItemDrop', 'onItemDrag', 'onItemRemoved', 'onItemEndEdit'], function(a, b, c) {
        $jsonOutput.val(domenu.toJson());
        if($keepChanges.is(':checked')) 
          window.localStorage.setItem('domenu-1Json', domenu.toJson());
      })
      .onToJson(function() {
        if(window.localStorage.length) $clearLocalStorage.show();
      });

    // Console event examples
    domenu.on('*', function(a, b, c) {
        console.log('event:', '*', 'arguments:', arguments, 'context:', this);
      })
      .onParseJson(function() {
        console.log('event: onFromJson', 'arguments:', arguments, 'context:', this);
      })
      .onToJson(function() {
        console.log('event: onToJson', 'arguments:', arguments, 'context:', this);
      })
      .onSaveEditBoxInput(function() {
        console.log('event: onSaveEditBoxInput', 'arguments:', arguments, 'context:', this);
      })
      .onItemDrag(function() {
        console.log('event: onItemDrag', 'arguments:', arguments, 'context:', this);
      })
      .onItemDrop(function() {
        console.log('event: onItemDrop', 'arguments:', arguments, 'context:', this);
      })
      .onItemAdded(function() {
        console.log('event: onItemAdded', 'arguments:', arguments, 'context:', this);
      })
      .onItemCollapsed(function() {
        console.log('event: onItemCollapsed', 'arguments:', arguments, 'context:', this);
      })
      .onItemExpanded(function() {
        console.log('event: onItemExpanded', 'arguments:', arguments, 'context:', this);
      })
      .onItemRemoved(function() {
        console.log('event: onItemRemoved', 'arguments:', arguments, 'context:', this);
      })
      .onItemStartEdit(function() {
        console.log('event: onItemStartEdit', 'arguments:', arguments, 'context:', this);
      })
      .onItemEndEdit(function() {
        console.log('event: onItemEndEdit', 'arguments:', arguments, 'context:', this);
      })
      .onItemAddChildItem(function() {
        console.log('event: onItemAddChildItem', 'arguments:', arguments, 'context:', this);
      })
      .onItemAddChildItem(function() {
        console.log('event: onItemAddChildItem', 'arguments:', arguments, 'context:', this);
      })
      .onItemAddChildItem(function() {
        console.log('event: onItemAddChildItem', 'arguments:', arguments, 'context:', this);
      })
      .onItemAddChildItem(function() {
        console.log('event: onItemAddChildItem', 'arguments:', arguments, 'context:', this);
      });


    //if(window.localStorage.length) $clearLocalStorage.show();
    //$clearLocalStorage.click(function() {
      //if(true) window.localStorage.clear();
      //if(!window.localStorage.length) $clearLocalStorage.hide();
      // Part of the reset demo routine
      //window.location.reload();	
    //});

    // Init textarea
    $jsonOutput.val(domenu.toJson());
    $keepChanges.on('click', function() {
      if(!$keepChanges.is(':checked')) window.localStorage.setItem('domenu-1KeepChanges', false);
      if($keepChanges.is(':checked')) window.localStorage.setItem('domenu-1KeepChanges', true);
    });

    if(window.localStorage.getItem('domenu-1KeepChanges') === "false") $keepChanges.attr('checked', false);
  });
```

#### Javascript \[form -> JSON]

```javascript
var _slides = $('#domenu-1-output').find('textarea[name=jsonOutput]').val();
var _checkData = JSON.parse(_slides);

return {
slides : _checkData
}
```



### vue.js

#### Sample Data

```json
{
    "advancedData": {
        "slides": [
            {
                "title": "Account",
                "customSelect": "select something...",
                "select2ScrollPosition": {
                    "x": 0,
                    "y": 0
                },
                "id": 1,
                "__domenu_params": {}
            },
            {
                "title": "Settings",
                "customSelect": "select something...",
                "select2ScrollPosition": {
                    "x": 0,
                    "y": 0
                },
                "id": 2,
                "__domenu_params": {}
            },
            {
                "title": "Call",
                "customSelect": "select something...",
                "id": 3,
                "__domenu_params": {}
            },
            {
                "title": "Support",
                "customSelect": "select something...",
                "id": 4,
                "__domenu_params": {}
            },
            {
                "title": "Email",
                "customSelect": "select something...",
                "id": 5,
                "__domenu_params": {}
            },
            {
                "title": "Orders",
                "customSelect": "select something...",
                "id": 6,
                "__domenu_params": {}
            },
            {
                "title": "Manage",
                "customSelect": "select something...",
                "id": 7,
                "__domenu_params": {}
            },
            {
                "title": "Settings",
                "customSelect": "select something...",
                "id": 8,
                "__domenu_params": {}
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
<!-- start navigation -->
<div class="navbar top-space navbar-expand-lg navbar-light bg-white header-light header-reverse-scroll" style="height:500px;display:block;">
    <div class="container-lg nav-header-container">
        <div class="col-auto col-sm-6 col-lg-2 me-auto ps-lg-0">
            <a class="navbar-brand" href="#">
                <span style="font-size:20px;font-weight:bold;font-family: 'Poppins', sans-serif;">I-0N </span><span style="font-size:14px;font-weight:600;font-family: 'Poppins', sans-serif;">Communications</span> 
            </a>
        </div>
        <div class="col-auto menu-order px-lg-0">
            <button class="navbar-toggler float-end" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-label="Toggle navigation">
                <span class="navbar-toggler-line"></span>
                <span class="navbar-toggler-line"></span>
                <span class="navbar-toggler-line"></span>
                <span class="navbar-toggler-line"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav alt-font">
                    <li class="nav-item dropdown simple-dropdown" v-for="(depth1, index) of advancedData.slides">
                        <a :href="depth1.customSelect" class="nav-link">{{depth1.title}}
                        <i class="fa fa-angle-down dropdown-toggle" data-bs-toggle="dropdown" aria-hidden="true" v-if="depth1.children"></i></a>
                        <ul class="dropdown-menu" role="menu" v-if="depth1.children">
                            <li class="dropdown" v-for="(depth2, index) of depth1.children">
                            <a data-bs-toggle="dropdown" href="javascript:void(0);" v-if="depth2.children">{{depth2.title}}<i class="fas fa-angle-right dropdown-toggle"></i></a>
                            <a :href="depth2.customSelect" v-else>{{depth2.title}}</a>
                                <ul class="dropdown-menu" v-if="depth2.children">
                                     <li v-for="(depth3, index) of depth2.children"><a :href="depth3.customSelect">{{depth3.title}}</a></li>
                                </ul>
                            </li>
                        </ul>                                                 
                    </li>                                
                </ul>
            </div>
        </div>
        <div class="col-auto text-end hidden-xs pe-0 font-size-0">
            <div class="header-search-icon search-form-wrapper">
                <a href="javascript:void(0)" class="search-form-icon header-search-form"><i class="feather icon-feather-search"></i></a>
                <!-- start search input -->
                <div class="form-wrapper">
                    <button title="Close" type="button" class="search-close alt-font">×</button>
                    <form id="search-form" role="search" method="get" class="search-form text-start" action="search-result.html">
                        <div class="search-form-box">
                            <span class="search-label alt-font text-small text-uppercase text-medium-gray">What are you looking for?</span>
                            <input class="search-input alt-font" id="search-form-input5e219ef164995" placeholder="Enter your keywords..." name="s" value="" type="text" autocomplete="off">
                            <button type="submit" class="search-button">
                                <i class="feather icon-feather-search" aria-hidden="true"></i>
                            </button>
                        </div>
                    </form>
                </div>
                <!-- end search input -->
            </div>
            <div class="header-language dropdown d-lg-inline-block">
                <a href="javascript:void(0);"><i class="feather icon-feather-globe"></i></a>
                <ul class="dropdown-menu alt-font">
                    <li><a href="javascript:void(0);" title="English"><span class="icon-country"><img src="https://isd.i-on.net/new/images/country-flag-16X16/usa.png" alt=""></span>English</a></li>
                    <li><a href="javascript:void(0);" title="England"><span class="icon-country"><img src="https://isd.i-on.net/new/images/country-flag-16X16/england.png" alt=""></span>England</a></li>
                    <li><a href="javascript:void(0);" title="France"><span class="icon-country"><img src="https://isd.i-on.net/new/images/country-flag-16X16/france.png" alt=""></span>France</a></li>
                    <li><a href="javascript:void(0);" title="Russian"><span class="icon-country"><img src="https://isd.i-on.net/new/images/country-flag-16X16/russian.png" alt=""></span>Russian</a></li>
                    <li><a href="javascript:void(0);" title="Spain"><span class="icon-country"><img src="https://isd.i-on.net/new/images/country-flag-16X16/spain.png" alt=""></span>Spain</a></li>
                </ul>
            </div>
            
        </div>
    </div>
</div>
<!-- end navigation -->
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

```javascript
/****** Change variables value as per your need ******/
var menuBreakPoint  = 991;
//var sliderBreakPoint= 991; // It will effect when you have used attribute "data-thumb-slider-md-direction" OR "data-slider-md-direction"
//var mobileAnimation = false;

/****** Get window width ******/
function getWindowWidth() {
    return $( window ).width();
}
/****** Get window height ******/
function getWindowHeight() {
    return $( window ).height();
}

/****** Menu position ******/
function menuPosition( element ) {
    var windowWidth     = getWindowWidth();
    if ( element.hasClass( 'simple-dropdown' ) ) {
        simpleDropdown  = element;
        linkDropdown    = element.find( 'a.nav-link' );
        var menuSpacing     = 30,
            menuLeftPosition= element.offset().left,
            menuWidth       = element.children( '.dropdown-menu' ).outerWidth(),
            menuDropdownCSS = ( windowWidth - menuSpacing ) - ( menuLeftPosition + menuWidth );
        if( menuDropdownCSS < 0 ) {
            element.children( '.dropdown-menu' ).css( 'left', menuDropdownCSS );
        }
    }
    if ( element.parent().hasClass( 'dropdown-menu' ) && element.parents( '.simple-dropdown' ) ) {
        var dropdownWidth   = 0,
            maxValueInArray = 0,
            lastValue       = 0,
            multiDepth      = 0;
        dropdownWidth = element.outerWidth() - linkDropdown.outerWidth();
        element.find( '.dropdown-menu' ).each( function () {
            var arr = [];
            if ( element.find( 'li' ).hasClass( 'dropdown' ) ) {
                dropdownWidth = dropdownWidth + element.outerWidth();
                element.find( 'li.dropdown' ).each( function () {
                    var dropdownMenu = element.closest( '.dropdown-menu' );
                    arr.push( dropdownMenu.outerWidth() );
                });
                maxValueInArray = lastValue + Math.max.apply( Math, arr );
                lastValue       = maxValueInArray;
                dropdownWidth   = dropdownWidth + maxValueInArray;
                multiDepth      = multiDepth + 1;
            } else if ( multiDepth < 1 ) {
                dropdownWidth = dropdownWidth + element.outerWidth();
            }
        });
        var menuRightPosition = windowWidth - ( simpleDropdown.offset().left + simpleDropdown.outerWidth() );
        if ( dropdownWidth > menuRightPosition ) {
            if( element.find( '.dropdown-menu' ).length > 0 ) {
                var menuTopPosition = element.position().top,
                    submenuObj      = element.find( '.dropdown-menu' ),
                    submenuHeight   = submenuObj.outerHeight(),
                    totalHeight     = menuTopPosition + submenuHeight + getTopSpaceHeaderHeight(),
                    windowHeight    = getWindowHeight();
                if( totalHeight > windowHeight ) {
                    submenuObj.css( 'top', '-' + ( totalHeight - windowHeight ) + 'px' );
                }
            }
            element.addClass( 'menu-left' );
        }
    }
}

/******* Navbar toggle *******/
var flag = false;
$( document ).on( 'click', '.navbar-toggle', function () {
    if ( getWindowWidth() > menuBreakPoint ) {
        if ( ! flag ) {
            flag = true;
            setTimeout( function () {
                flag = false;
            }, 500 );
            $( 'body' ).addClass( 'show-menu' );
        } else {
            if ( ! $( '.navbar-collapse' ).has( e.target ).is( '.navbar-collapse' ) && $( '.navbar-collapse ul' ).hasClass( 'show' ) ) {
                $( '.navbar-collapse' ).find( 'a.dropdown-toggle' ).addClass( 'collapsed' );
                $( '.navbar-collapse' ).find( 'ul.dropdown-menu' ).removeClass( 'show' );
                $( '.navbar-collapse a.dropdown-toggle' ).removeClass( 'active' );
            }
        }
    }
});

/****** Open menu on hover ******/
$( '.dropdown' ).on( 'mouseenter touchstart', function( e ) {

    var _this = $( this );
        _this.siblings( '.dropdown' ).removeClass( 'open' );
        _this.parents( '.navbar-nav' ).siblings( '.navbar-nav' ).find( '.dropdown' ).removeClass( 'open' );
        _this.addClass( 'open' );
    if ( getWindowWidth() > menuBreakPoint ) {
        menuPosition( _this );
        if( $( e.target ).siblings( '.dropdown-menu' ).length ) {
            e.preventDefault();
        }
    }

}).on( 'mouseleave', function( e ) {

    var _this = $( this );
    _this.removeClass( 'menu-left' );
    _this.removeClass( 'open' );
});
```

