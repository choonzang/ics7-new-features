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


```

#### Javascript \[JSON -> form]

```javascript
/*! Select2 4.0.1 | https://github.com/select2/select2/blob/master/LICENSE.md */!function(a){"function"==typeof define&&define.amd?define(["jquery"],a):a("object"==typeof exports?require("jquery"):jQuery)}(function(a){var b=function(){if(a&&a.fn&&a.fn.select2&&a.fn.select2.amd)var b=a.fn.select2.amd;var b;return function(){if(!b||!b.requirejs){b?c=b:b={};var a,c,d;!function(b){function e(a,b){return u.call(a,b)}function f(a,b){var c,d,e,f,g,h,i,j,k,l,m,n=b&&b.split("/"),o=s.map,p=o&&o["*"]||{};if(a&&"."===a.charAt(0))if(b){for(a=a.split("/"),g=a.length-1,s.nodeIdCompat&&w.test(a[g])&&(a[g]=a[g].replace(w,"")),a=n.slice(0,n.length-1).concat(a),k=0;k<a.length;k+=1)if(m=a[k],"."===m)a.splice(k,1),k-=1;else if(".."===m){if(1===k&&(".."===a[2]||".."===a[0]))break;k>0&&(a.splice(k-1,2),k-=2)}a=a.join("/")}else 0===a.indexOf("./")&&(a=a.substring(2));if((n||p)&&o){for(c=a.split("/"),k=c.length;k>0;k-=1){if(d=c.slice(0,k).join("/"),n)for(l=n.length;l>0;l-=1)if(e=o[n.slice(0,l).join("/")],e&&(e=e[d])){f=e,h=k;break}if(f)break;!i&&p&&p[d]&&(i=p[d],j=k)}!f&&i&&(f=i,h=j),f&&(c.splice(0,h,f),a=c.join("/"))}return a}function g(a,c){return function(){var d=v.call(arguments,0);return"string"!=typeof d[0]&&1===d.length&&d.push(null),n.apply(b,d.concat([a,c]))}}function h(a){return function(b){return f(b,a)}}function i(a){return function(b){q[a]=b}}function j(a){if(e(r,a)){var c=r[a];delete r[a],t[a]=!0,m.apply(b,c)}if(!e(q,a)&&!e(t,a))throw new Error("No "+a);return q[a]}function k(a){var b,c=a?a.indexOf("!"):-1;return c>-1&&(b=a.substring(0,c),a=a.substring(c+1,a.length)),[b,a]}function l(a){return function(){return s&&s.config&&s.config[a]||{}}}var m,n,o,p,q={},r={},s={},t={},u=Object.prototype.hasOwnProperty,v=[].slice,w=/\.js$/;o=function(a,b){var c,d=k(a),e=d[0];return a=d[1],e&&(e=f(e,b),c=j(e)),e?a=c&&c.normalize?c.normalize(a,h(b)):f(a,b):(a=f(a,b),d=k(a),e=d[0],a=d[1],e&&(c=j(e))),{f:e?e+"!"+a:a,n:a,pr:e,p:c}},p={require:function(a){return g(a)},exports:function(a){var b=q[a];return"undefined"!=typeof b?b:q[a]={}},module:function(a){return{id:a,uri:"",exports:q[a],config:l(a)}}},m=function(a,c,d,f){var h,k,l,m,n,s,u=[],v=typeof d;if(f=f||a,"undefined"===v||"function"===v){for(c=!c.length&&d.length?["require","exports","module"]:c,n=0;n<c.length;n+=1)if(m=o(c[n],f),k=m.f,"require"===k)u[n]=p.require(a);else if("exports"===k)u[n]=p.exports(a),s=!0;else if("module"===k)h=u[n]=p.module(a);else if(e(q,k)||e(r,k)||e(t,k))u[n]=j(k);else{if(!m.p)throw new Error(a+" missing "+k);m.p.load(m.n,g(f,!0),i(k),{}),u[n]=q[k]}l=d?d.apply(q[a],u):void 0,a&&(h&&h.exports!==b&&h.exports!==q[a]?q[a]=h.exports:l===b&&s||(q[a]=l))}else a&&(q[a]=d)},a=c=n=function(a,c,d,e,f){if("string"==typeof a)return p[a]?p[a](c):j(o(a,c).f);if(!a.splice){if(s=a,s.deps&&n(s.deps,s.callback),!c)return;c.splice?(a=c,c=d,d=null):a=b}return c=c||function(){},"function"==typeof d&&(d=e,e=f),e?m(b,a,c,d):setTimeout(function(){m(b,a,c,d)},4),n},n.config=function(a){return n(a)},a._defined=q,d=function(a,b,c){if("string"!=typeof a)throw new Error("See almond README: incorrect module build, no module name");b.splice||(c=b,b=[]),e(q,a)||e(r,a)||(r[a]=[a,b,c])},d.amd={jQuery:!0}}(),b.requirejs=a,b.require=c,b.define=d}}(),b.define("almond",function(){}),b.define("jquery",[],function(){var b=a||$;return null==b&&console&&console.error&&console.error("Select2: An instance of jQuery or a jQuery-compatible library was not found. Make sure that you are including jQuery before Select2 on your web page."),b}),b.define("select2/utils",["jquery"],function(a){function b(a){var b=a.prototype,c=[];for(var d in b){var e=b[d];"function"==typeof e&&"constructor"!==d&&c.push(d)}return c}var c={};c.Extend=function(a,b){function c(){this.constructor=a}var d={}.hasOwnProperty;for(var e in b)d.call(b,e)&&(a[e]=b[e]);return c.prototype=b.prototype,a.prototype=new c,a.__super__=b.prototype,a},c.Decorate=function(a,c){function d(){var b=Array.prototype.unshift,d=c.prototype.constructor.length,e=a.prototype.constructor;d>0&&(b.call(arguments,a.prototype.constructor),e=c.prototype.constructor),e.apply(this,arguments)}function e(){this.constructor=d}var f=b(c),g=b(a);c.displayName=a.displayName,d.prototype=new e;for(var h=0;h<g.length;h++){var i=g[h];d.prototype[i]=a.prototype[i]}for(var j=(function(a){var b=function(){};a in d.prototype&&(b=d.prototype[a]);var e=c.prototype[a];return function(){var a=Array.prototype.unshift;return a.call(arguments,b),e.apply(this,arguments)}}),k=0;k<f.length;k++){var l=f[k];d.prototype[l]=j(l)}return d};var d=function(){this.listeners={}};return d.prototype.on=function(a,b){this.listeners=this.listeners||{},a in this.listeners?this.listeners[a].push(b):this.listeners[a]=[b]},d.prototype.trigger=function(a){var b=Array.prototype.slice;this.listeners=this.listeners||{},a in this.listeners&&this.invoke(this.listeners[a],b.call(arguments,1)),"*"in this.listeners&&this.invoke(this.listeners["*"],arguments)},d.prototype.invoke=function(a,b){for(var c=0,d=a.length;d>c;c++)a[c].apply(this,b)},c.Observable=d,c.generateChars=function(a){for(var b="",c=0;a>c;c++){var d=Math.floor(36*Math.random());b+=d.toString(36)}return b},c.bind=function(a,b){return function(){a.apply(b,arguments)}},c._convertData=function(a){for(var b in a){var c=b.split("-"),d=a;if(1!==c.length){for(var e=0;e<c.length;e++){var f=c[e];f=f.substring(0,1).toLowerCase()+f.substring(1),f in d||(d[f]={}),e==c.length-1&&(d[f]=a[b]),d=d[f]}delete a[b]}}return a},c.hasScroll=function(b,c){var d=a(c),e=c.style.overflowX,f=c.style.overflowY;return e!==f||"hidden"!==f&&"visible"!==f?"scroll"===e||"scroll"===f?!0:d.innerHeight()<c.scrollHeight||d.innerWidth()<c.scrollWidth:!1},c.escapeMarkup=function(a){var b={"\\":"&#92;","&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;","/":"&#47;"};return"string"!=typeof a?a:String(a).replace(/[&<>"'\/\\]/g,function(a){return b[a]})},c.appendMany=function(b,c){if("1.7"===a.fn.jquery.substr(0,3)){var d=a();a.map(c,function(a){d=d.add(a)}),c=d}b.append(c)},c}),b.define("select2/results",["jquery","./utils"],function(a,b){function c(a,b,d){this.$element=a,this.data=d,this.options=b,c.__super__.constructor.call(this)}return b.Extend(c,b.Observable),c.prototype.render=function(){var b=a('<ul class="select2-results__options" role="tree"></ul>');return this.options.get("multiple")&&b.attr("aria-multiselectable","true"),this.$results=b,b},c.prototype.clear=function(){this.$results.empty()},c.prototype.displayMessage=function(b){var c=this.options.get("escapeMarkup");this.clear(),this.hideLoading();var d=a('<li role="treeitem" aria-live="assertive" class="select2-results__option"></li>'),e=this.options.get("translations").get(b.message);d.append(c(e(b.args))),d[0].className+=" select2-results__message",this.$results.append(d)},c.prototype.hideMessages=function(){this.$results.find(".select2-results__message").remove()},c.prototype.append=function(a){this.hideLoading();var b=[];if(null==a.results||0===a.results.length)return void(0===this.$results.children().length&&this.trigger("results:message",{message:"noResults"}));a.results=this.sort(a.results);for(var c=0;c<a.results.length;c++){var d=a.results[c],e=this.option(d);b.push(e)}this.$results.append(b)},c.prototype.position=function(a,b){var c=b.find(".select2-results");c.append(a)},c.prototype.sort=function(a){var b=this.options.get("sorter");return b(a)},c.prototype.setClasses=function(){var b=this;this.data.current(function(c){var d=a.map(c,function(a){return a.id.toString()}),e=b.$results.find(".select2-results__option[aria-selected]");e.each(function(){var b=a(this),c=a.data(this,"data"),e=""+c.id;null!=c.element&&c.element.selected||null==c.element&&a.inArray(e,d)>-1?b.attr("aria-selected","true"):b.attr("aria-selected","false")});var f=e.filter("[aria-selected=true]");f.length>0?f.first().trigger("mouseenter"):e.first().trigger("mouseenter")})},c.prototype.showLoading=function(a){this.hideLoading();var b=this.options.get("translations").get("searching"),c={disabled:!0,loading:!0,text:b(a)},d=this.option(c);d.className+=" loading-results",this.$results.prepend(d)},c.prototype.hideLoading=function(){this.$results.find(".loading-results").remove()},c.prototype.option=function(b){var c=document.createElement("li");c.className="select2-results__option";var d={role:"treeitem","aria-selected":"false"};b.disabled&&(delete d["aria-selected"],d["aria-disabled"]="true"),null==b.id&&delete d["aria-selected"],null!=b._resultId&&(c.id=b._resultId),b.title&&(c.title=b.title),b.children&&(d.role="group",d["aria-label"]=b.text,delete d["aria-selected"]);for(var e in d){var f=d[e];c.setAttribute(e,f)}if(b.children){var g=a(c),h=document.createElement("strong");h.className="select2-results__group";a(h);this.template(b,h);for(var i=[],j=0;j<b.children.length;j++){var k=b.children[j],l=this.option(k);i.push(l)}var m=a("<ul></ul>",{"class":"select2-results__options select2-results__options--nested"});m.append(i),g.append(h),g.append(m)}else this.template(b,c);return a.data(c,"data",b),c},c.prototype.bind=function(b,c){var d=this,e=b.id+"-results";this.$results.attr("id",e),b.on("results:all",function(a){d.clear(),d.append(a.data),b.isOpen()&&d.setClasses()}),b.on("results:append",function(a){d.append(a.data),b.isOpen()&&d.setClasses()}),b.on("query",function(a){d.hideMessages(),d.showLoading(a)}),b.on("select",function(){b.isOpen()&&d.setClasses()}),b.on("unselect",function(){b.isOpen()&&d.setClasses()}),b.on("open",function(){d.$results.attr("aria-expanded","true"),d.$results.attr("aria-hidden","false"),d.setClasses(),d.ensureHighlightVisible()}),b.on("close",function(){d.$results.attr("aria-expanded","false"),d.$results.attr("aria-hidden","true"),d.$results.removeAttr("aria-activedescendant")}),b.on("results:toggle",function(){var a=d.getHighlightedResults();0!==a.length&&a.trigger("mouseup")}),b.on("results:select",function(){var a=d.getHighlightedResults();if(0!==a.length){var b=a.data("data");"true"==a.attr("aria-selected")?d.trigger("close",{}):d.trigger("select",{data:b})}}),b.on("results:previous",function(){var a=d.getHighlightedResults(),b=d.$results.find("[aria-selected]"),c=b.index(a);if(0!==c){var e=c-1;0===a.length&&(e=0);var f=b.eq(e);f.trigger("mouseenter");var g=d.$results.offset().top,h=f.offset().top,i=d.$results.scrollTop()+(h-g);0===e?d.$results.scrollTop(0):0>h-g&&d.$results.scrollTop(i)}}),b.on("results:next",function(){var a=d.getHighlightedResults(),b=d.$results.find("[aria-selected]"),c=b.index(a),e=c+1;if(!(e>=b.length)){var f=b.eq(e);f.trigger("mouseenter");var g=d.$results.offset().top+d.$results.outerHeight(!1),h=f.offset().top+f.outerHeight(!1),i=d.$results.scrollTop()+h-g;0===e?d.$results.scrollTop(0):h>g&&d.$results.scrollTop(i)}}),b.on("results:focus",function(a){a.element.addClass("select2-results__option--highlighted")}),b.on("results:message",function(a){d.displayMessage(a)}),a.fn.mousewheel&&this.$results.on("mousewheel",function(a){var b=d.$results.scrollTop(),c=d.$results.get(0).scrollHeight-d.$results.scrollTop()+a.deltaY,e=a.deltaY>0&&b-a.deltaY<=0,f=a.deltaY<0&&c<=d.$results.height();e?(d.$results.scrollTop(0),a.preventDefault(),a.stopPropagation()):f&&(d.$results.scrollTop(d.$results.get(0).scrollHeight-d.$results.height()),a.preventDefault(),a.stopPropagation())}),this.$results.on("mouseup",".select2-results__option[aria-selected]",function(b){var c=a(this),e=c.data("data");return"true"===c.attr("aria-selected")?void(d.options.get("multiple")?d.trigger("unselect",{originalEvent:b,data:e}):d.trigger("close",{})):void d.trigger("select",{originalEvent:b,data:e})}),this.$results.on("mouseenter",".select2-results__option[aria-selected]",function(b){var c=a(this).data("data");d.getHighlightedResults().removeClass("select2-results__option--highlighted"),d.trigger("results:focus",{data:c,element:a(this)})})},c.prototype.getHighlightedResults=function(){var a=this.$results.find(".select2-results__option--highlighted");return a},c.prototype.destroy=function(){this.$results.remove()},c.prototype.ensureHighlightVisible=function(){var a=this.getHighlightedResults();if(0!==a.length){var b=this.$results.find("[aria-selected]"),c=b.index(a),d=this.$results.offset().top,e=a.offset().top,f=this.$results.scrollTop()+(e-d),g=e-d;f-=2*a.outerHeight(!1),2>=c?this.$results.scrollTop(0):(g>this.$results.outerHeight()||0>g)&&this.$results.scrollTop(f)}},c.prototype.template=function(b,c){var d=this.options.get("templateResult"),e=this.options.get("escapeMarkup"),f=d(b,c);null==f?c.style.display="none":"string"==typeof f?c.innerHTML=e(f):a(c).append(f)},c}),b.define("select2/keys",[],function(){var a={BACKSPACE:8,TAB:9,ENTER:13,SHIFT:16,CTRL:17,ALT:18,ESC:27,SPACE:32,PAGE_UP:33,PAGE_DOWN:34,END:35,HOME:36,LEFT:37,UP:38,RIGHT:39,DOWN:40,DELETE:46};return a}),b.define("select2/selection/base",["jquery","../utils","../keys"],function(a,b,c){function d(a,b){this.$element=a,this.options=b,d.__super__.constructor.call(this)}return b.Extend(d,b.Observable),d.prototype.render=function(){var b=a('<span class="select2-selection" role="combobox"  aria-haspopup="true" aria-expanded="false"></span>');return this._tabindex=0,null!=this.$element.data("old-tabindex")?this._tabindex=this.$element.data("old-tabindex"):null!=this.$element.attr("tabindex")&&(this._tabindex=this.$element.attr("tabindex")),b.attr("title",this.$element.attr("title")),b.attr("tabindex",this._tabindex),this.$selection=b,b},d.prototype.bind=function(a,b){var d=this,e=(a.id+"-container",a.id+"-results");this.container=a,this.$selection.on("focus",function(a){d.trigger("focus",a)}),this.$selection.on("blur",function(a){d._handleBlur(a)}),this.$selection.on("keydown",function(a){d.trigger("keypress",a),a.which===c.SPACE&&a.preventDefault()}),a.on("results:focus",function(a){d.$selection.attr("aria-activedescendant",a.data._resultId)}),a.on("selection:update",function(a){d.update(a.data)}),a.on("open",function(){d.$selection.attr("aria-expanded","true"),d.$selection.attr("aria-owns",e),d._attachCloseHandler(a)}),a.on("close",function(){d.$selection.attr("aria-expanded","false"),d.$selection.removeAttr("aria-activedescendant"),d.$selection.removeAttr("aria-owns"),d.$selection.focus(),d._detachCloseHandler(a)}),a.on("enable",function(){d.$selection.attr("tabindex",d._tabindex)}),a.on("disable",function(){d.$selection.attr("tabindex","-1")})},d.prototype._handleBlur=function(b){var c=this;window.setTimeout(function(){document.activeElement==c.$selection[0]||a.contains(c.$selection[0],document.activeElement)||c.trigger("blur",b)},1)},d.prototype._attachCloseHandler=function(b){a(document.body).on("mousedown.select2."+b.id,function(b){var c=a(b.target),d=c.closest(".select2"),e=a(".select2.select2-container--open");e.each(function(){var b=a(this);if(this!=d[0]){var c=b.data("element");c.select2("close")}})})},d.prototype._detachCloseHandler=function(b){a(document.body).off("mousedown.select2."+b.id)},d.prototype.position=function(a,b){var c=b.find(".selection");c.append(a)},d.prototype.destroy=function(){this._detachCloseHandler(this.container)},d.prototype.update=function(a){throw new Error("The `update` method must be defined in child classes.")},d}),b.define("select2/selection/single",["jquery","./base","../utils","../keys"],function(a,b,c,d){function e(){e.__super__.constructor.apply(this,arguments)}return c.Extend(e,b),e.prototype.render=function(){var a=e.__super__.render.call(this);return a.addClass("select2-selection--single"),a.html('<span class="select2-selection__rendered"></span><span class="select2-selection__arrow" role="presentation"><b role="presentation"></b></span>'),a},e.prototype.bind=function(a,b){var c=this;e.__super__.bind.apply(this,arguments);var d=a.id+"-container";this.$selection.find(".select2-selection__rendered").attr("id",d),this.$selection.attr("aria-labelledby",d),this.$selection.on("mousedown",function(a){1===a.which&&c.trigger("toggle",{originalEvent:a})}),this.$selection.on("focus",function(a){}),this.$selection.on("blur",function(a){}),a.on("selection:update",function(a){c.update(a.data)})},e.prototype.clear=function(){this.$selection.find(".select2-selection__rendered").empty()},e.prototype.display=function(a,b){var c=this.options.get("templateSelection"),d=this.options.get("escapeMarkup");return d(c(a,b))},e.prototype.selectionContainer=function(){return a("<span></span>")},e.prototype.update=function(a){if(0===a.length)return void this.clear();var b=a[0],c=this.$selection.find(".select2-selection__rendered"),d=this.display(b,c);c.empty().append(d),c.prop("title",b.title||b.text)},e}),b.define("select2/selection/multiple",["jquery","./base","../utils"],function(a,b,c){function d(a,b){d.__super__.constructor.apply(this,arguments)}return c.Extend(d,b),d.prototype.render=function(){var a=d.__super__.render.call(this);return a.addClass("select2-selection--multiple"),a.html('<ul class="select2-selection__rendered"></ul>'),a},d.prototype.bind=function(b,c){var e=this;d.__super__.bind.apply(this,arguments),this.$selection.on("click",function(a){e.trigger("toggle",{originalEvent:a})}),this.$selection.on("click",".select2-selection__choice__remove",function(b){if(!e.options.get("disabled")){var c=a(this),d=c.parent(),f=d.data("data");e.trigger("unselect",{originalEvent:b,data:f})}})},d.prototype.clear=function(){this.$selection.find(".select2-selection__rendered").empty()},d.prototype.display=function(a,b){var c=this.options.get("templateSelection"),d=this.options.get("escapeMarkup");return d(c(a,b))},d.prototype.selectionContainer=function(){var b=a('<li class="select2-selection__choice"><span class="select2-selection__choice__remove" role="presentation">&times;</span></li>');return b},d.prototype.update=function(a){if(this.clear(),0!==a.length){for(var b=[],d=0;d<a.length;d++){var e=a[d],f=this.selectionContainer(),g=this.display(e,f);f.append(g),f.prop("title",e.title||e.text),f.data("data",e),b.push(f)}var h=this.$selection.find(".select2-selection__rendered");c.appendMany(h,b)}},d}),b.define("select2/selection/placeholder",["../utils"],function(a){function b(a,b,c){this.placeholder=this.normalizePlaceholder(c.get("placeholder")),a.call(this,b,c)}return b.prototype.normalizePlaceholder=function(a,b){return"string"==typeof b&&(b={id:"",text:b}),b},b.prototype.createPlaceholder=function(a,b){var c=this.selectionContainer();return c.html(this.display(b)),c.addClass("select2-selection__placeholder").removeClass("select2-selection__choice"),c},b.prototype.update=function(a,b){var c=1==b.length&&b[0].id!=this.placeholder.id,d=b.length>1;if(d||c)return a.call(this,b);this.clear();var e=this.createPlaceholder(this.placeholder);this.$selection.find(".select2-selection__rendered").append(e)},b}),b.define("select2/selection/allowClear",["jquery","../keys"],function(a,b){function c(){}return c.prototype.bind=function(a,b,c){var d=this;a.call(this,b,c),null==this.placeholder&&this.options.get("debug")&&window.console&&console.error&&console.error("Select2: The `allowClear` option should be used in combination with the `placeholder` option."),this.$selection.on("mousedown",".select2-selection__clear",function(a){d._handleClear(a)}),b.on("keypress",function(a){d._handleKeyboardClear(a,b)})},c.prototype._handleClear=function(a,b){if(!this.options.get("disabled")){var c=this.$selection.find(".select2-selection__clear");if(0!==c.length){b.stopPropagation();for(var d=c.data("data"),e=0;e<d.length;e++){var f={data:d[e]};if(this.trigger("unselect",f),f.prevented)return}this.$element.val(this.placeholder.id).trigger("change"),this.trigger("toggle",{})}}},c.prototype._handleKeyboardClear=function(a,c,d){d.isOpen()||(c.which==b.DELETE||c.which==b.BACKSPACE)&&this._handleClear(c)},c.prototype.update=function(b,c){if(b.call(this,c),!(this.$selection.find(".select2-selection__placeholder").length>0||0===c.length)){var d=a('<span class="select2-selection__clear">&times;</span>');d.data("data",c),this.$selection.find(".select2-selection__rendered").prepend(d)}},c}),b.define("select2/selection/search",["jquery","../utils","../keys"],function(a,b,c){function d(a,b,c){a.call(this,b,c)}return d.prototype.render=function(b){var c=a('<li class="select2-search select2-search--inline"><input class="select2-search__field" type="search" tabindex="-1" autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" role="textbox" aria-autocomplete="list" /></li>');this.$searchContainer=c,this.$search=c.find("input");var d=b.call(this);return this._transferTabIndex(),d},d.prototype.bind=function(a,b,d){var e=this;a.call(this,b,d),b.on("open",function(){e.$search.trigger("focus")}),b.on("close",function(){e.$search.val(""),e.$search.removeAttr("aria-activedescendant"),e.$search.trigger("focus")}),b.on("enable",function(){e.$search.prop("disabled",!1),e._transferTabIndex()}),b.on("disable",function(){e.$search.prop("disabled",!0)}),b.on("focus",function(a){e.$search.trigger("focus")}),b.on("results:focus",function(a){e.$search.attr("aria-activedescendant",a.id)}),this.$selection.on("focusin",".select2-search--inline",function(a){e.trigger("focus",a)}),this.$selection.on("focusout",".select2-search--inline",function(a){e._handleBlur(a)}),this.$selection.on("keydown",".select2-search--inline",function(a){a.stopPropagation(),e.trigger("keypress",a),e._keyUpPrevented=a.isDefaultPrevented();var b=a.which;if(b===c.BACKSPACE&&""===e.$search.val()){var d=e.$searchContainer.prev(".select2-selection__choice");if(d.length>0){var f=d.data("data");e.searchRemoveChoice(f),a.preventDefault()}}});var f=document.documentMode,g=f&&11>=f;this.$selection.on("input.searchcheck",".select2-search--inline",function(a){return g?void e.$selection.off("input.search input.searchcheck"):void e.$selection.off("keyup.search")}),this.$selection.on("keyup.search input.search",".select2-search--inline",function(a){if(g&&"input"===a.type)return void e.$selection.off("input.search input.searchcheck");var b=a.which;b!=c.SHIFT&&b!=c.CTRL&&b!=c.ALT&&b!=c.TAB&&e.handleSearch(a)})},d.prototype._transferTabIndex=function(a){this.$search.attr("tabindex",this.$selection.attr("tabindex")),this.$selection.attr("tabindex","-1")},d.prototype.createPlaceholder=function(a,b){this.$search.attr("placeholder",b.text)},d.prototype.update=function(a,b){var c=this.$search[0]==document.activeElement;this.$search.attr("placeholder",""),a.call(this,b),this.$selection.find(".select2-selection__rendered").append(this.$searchContainer),this.resizeSearch(),c&&this.$search.focus()},d.prototype.handleSearch=function(){if(this.resizeSearch(),!this._keyUpPrevented){var a=this.$search.val();this.trigger("query",{term:a})}this._keyUpPrevented=!1},d.prototype.searchRemoveChoice=function(a,b){this.trigger("unselect",{data:b}),this.$search.val(b.text),this.handleSearch()},d.prototype.resizeSearch=function(){this.$search.css("width","25px");var a="";if(""!==this.$search.attr("placeholder"))a=this.$selection.find(".select2-selection__rendered").innerWidth();else{var b=this.$search.val().length+1;a=.75*b+"em"}this.$search.css("width",a)},d}),b.define("select2/selection/eventRelay",["jquery"],function(a){function b(){}return b.prototype.bind=function(b,c,d){var e=this,f=["open","opening","close","closing","select","selecting","unselect","unselecting"],g=["opening","closing","selecting","unselecting"];b.call(this,c,d),c.on("*",function(b,c){if(-1!==a.inArray(b,f)){c=c||{};var d=a.Event("select2:"+b,{params:c});e.$element.trigger(d),-1!==a.inArray(b,g)&&(c.prevented=d.isDefaultPrevented())}})},b}),b.define("select2/translation",["jquery","require"],function(a,b){function c(a){this.dict=a||{}}return c.prototype.all=function(){return this.dict},c.prototype.get=function(a){return this.dict[a]},c.prototype.extend=function(b){this.dict=a.extend({},b.all(),this.dict)},c._cache={},c.loadPath=function(a){if(!(a in c._cache)){var d=b(a);c._cache[a]=d}return new c(c._cache[a])},c}),b.define("select2/diacritics",[],function(){var a={"Ⓐ":"A","Ａ":"A","À":"A","Á":"A","Â":"A","Ầ":"A","Ấ":"A","Ẫ":"A","Ẩ":"A","Ã":"A","Ā":"A","Ă":"A","Ằ":"A","Ắ":"A","Ẵ":"A","Ẳ":"A","Ȧ":"A","Ǡ":"A","Ä":"A","Ǟ":"A","Ả":"A","Å":"A","Ǻ":"A","Ǎ":"A","Ȁ":"A","Ȃ":"A","Ạ":"A","Ậ":"A","Ặ":"A","Ḁ":"A","Ą":"A","Ⱥ":"A","Ɐ":"A","Ꜳ":"AA","Æ":"AE","Ǽ":"AE","Ǣ":"AE","Ꜵ":"AO","Ꜷ":"AU","Ꜹ":"AV","Ꜻ":"AV","Ꜽ":"AY","Ⓑ":"B","Ｂ":"B","Ḃ":"B","Ḅ":"B","Ḇ":"B","Ƀ":"B","Ƃ":"B","Ɓ":"B","Ⓒ":"C","Ｃ":"C","Ć":"C","Ĉ":"C","Ċ":"C","Č":"C","Ç":"C","Ḉ":"C","Ƈ":"C","Ȼ":"C","Ꜿ":"C","Ⓓ":"D","Ｄ":"D","Ḋ":"D","Ď":"D","Ḍ":"D","Ḑ":"D","Ḓ":"D","Ḏ":"D","Đ":"D","Ƌ":"D","Ɗ":"D","Ɖ":"D","Ꝺ":"D","Ǳ":"DZ","Ǆ":"DZ","ǲ":"Dz","ǅ":"Dz","Ⓔ":"E","Ｅ":"E","È":"E","É":"E","Ê":"E","Ề":"E","Ế":"E","Ễ":"E","Ể":"E","Ẽ":"E","Ē":"E","Ḕ":"E","Ḗ":"E","Ĕ":"E","Ė":"E","Ë":"E","Ẻ":"E","Ě":"E","Ȅ":"E","Ȇ":"E","Ẹ":"E","Ệ":"E","Ȩ":"E","Ḝ":"E","Ę":"E","Ḙ":"E","Ḛ":"E","Ɛ":"E","Ǝ":"E","Ⓕ":"F","Ｆ":"F","Ḟ":"F","Ƒ":"F","Ꝼ":"F","Ⓖ":"G","Ｇ":"G","Ǵ":"G","Ĝ":"G","Ḡ":"G","Ğ":"G","Ġ":"G","Ǧ":"G","Ģ":"G","Ǥ":"G","Ɠ":"G","Ꞡ":"G","Ᵹ":"G","Ꝿ":"G","Ⓗ":"H","Ｈ":"H","Ĥ":"H","Ḣ":"H","Ḧ":"H","Ȟ":"H","Ḥ":"H","Ḩ":"H","Ḫ":"H","Ħ":"H","Ⱨ":"H","Ⱶ":"H","Ɥ":"H","Ⓘ":"I","Ｉ":"I","Ì":"I","Í":"I","Î":"I","Ĩ":"I","Ī":"I","Ĭ":"I","İ":"I","Ï":"I","Ḯ":"I","Ỉ":"I","Ǐ":"I","Ȉ":"I","Ȋ":"I","Ị":"I","Į":"I","Ḭ":"I","Ɨ":"I","Ⓙ":"J","Ｊ":"J","Ĵ":"J","Ɉ":"J","Ⓚ":"K","Ｋ":"K","Ḱ":"K","Ǩ":"K","Ḳ":"K","Ķ":"K","Ḵ":"K","Ƙ":"K","Ⱪ":"K","Ꝁ":"K","Ꝃ":"K","Ꝅ":"K","Ꞣ":"K","Ⓛ":"L","Ｌ":"L","Ŀ":"L","Ĺ":"L","Ľ":"L","Ḷ":"L","Ḹ":"L","Ļ":"L","Ḽ":"L","Ḻ":"L","Ł":"L","Ƚ":"L","Ɫ":"L","Ⱡ":"L","Ꝉ":"L","Ꝇ":"L","Ꞁ":"L","Ǉ":"LJ","ǈ":"Lj","Ⓜ":"M","Ｍ":"M","Ḿ":"M","Ṁ":"M","Ṃ":"M","Ɱ":"M","Ɯ":"M","Ⓝ":"N","Ｎ":"N","Ǹ":"N","Ń":"N","Ñ":"N","Ṅ":"N","Ň":"N","Ṇ":"N","Ņ":"N","Ṋ":"N","Ṉ":"N","Ƞ":"N","Ɲ":"N","Ꞑ":"N","Ꞥ":"N","Ǌ":"NJ","ǋ":"Nj","Ⓞ":"O","Ｏ":"O","Ò":"O","Ó":"O","Ô":"O","Ồ":"O","Ố":"O","Ỗ":"O","Ổ":"O","Õ":"O","Ṍ":"O","Ȭ":"O","Ṏ":"O","Ō":"O","Ṑ":"O","Ṓ":"O","Ŏ":"O","Ȯ":"O","Ȱ":"O","Ö":"O","Ȫ":"O","Ỏ":"O","Ő":"O","Ǒ":"O","Ȍ":"O","Ȏ":"O","Ơ":"O","Ờ":"O","Ớ":"O","Ỡ":"O","Ở":"O","Ợ":"O","Ọ":"O","Ộ":"O","Ǫ":"O","Ǭ":"O","Ø":"O","Ǿ":"O","Ɔ":"O","Ɵ":"O","Ꝋ":"O","Ꝍ":"O","Ƣ":"OI","Ꝏ":"OO","Ȣ":"OU","Ⓟ":"P","Ｐ":"P","Ṕ":"P","Ṗ":"P","Ƥ":"P","Ᵽ":"P","Ꝑ":"P","Ꝓ":"P","Ꝕ":"P","Ⓠ":"Q","Ｑ":"Q","Ꝗ":"Q","Ꝙ":"Q","Ɋ":"Q","Ⓡ":"R","Ｒ":"R","Ŕ":"R","Ṙ":"R","Ř":"R","Ȑ":"R","Ȓ":"R","Ṛ":"R","Ṝ":"R","Ŗ":"R","Ṟ":"R","Ɍ":"R","Ɽ":"R","Ꝛ":"R","Ꞧ":"R","Ꞃ":"R","Ⓢ":"S","Ｓ":"S","ẞ":"S","Ś":"S","Ṥ":"S","Ŝ":"S","Ṡ":"S","Š":"S","Ṧ":"S","Ṣ":"S","Ṩ":"S","Ș":"S","Ş":"S","Ȿ":"S","Ꞩ":"S","Ꞅ":"S","Ⓣ":"T","Ｔ":"T","Ṫ":"T","Ť":"T","Ṭ":"T","Ț":"T","Ţ":"T","Ṱ":"T","Ṯ":"T","Ŧ":"T","Ƭ":"T","Ʈ":"T","Ⱦ":"T","Ꞇ":"T","Ꜩ":"TZ","Ⓤ":"U","Ｕ":"U","Ù":"U","Ú":"U","Û":"U","Ũ":"U","Ṹ":"U","Ū":"U","Ṻ":"U","Ŭ":"U","Ü":"U","Ǜ":"U","Ǘ":"U","Ǖ":"U","Ǚ":"U","Ủ":"U","Ů":"U","Ű":"U","Ǔ":"U","Ȕ":"U","Ȗ":"U","Ư":"U","Ừ":"U","Ứ":"U","Ữ":"U","Ử":"U","Ự":"U","Ụ":"U","Ṳ":"U","Ų":"U","Ṷ":"U","Ṵ":"U","Ʉ":"U","Ⓥ":"V","Ｖ":"V","Ṽ":"V","Ṿ":"V","Ʋ":"V","Ꝟ":"V","Ʌ":"V","Ꝡ":"VY","Ⓦ":"W","Ｗ":"W","Ẁ":"W","Ẃ":"W","Ŵ":"W","Ẇ":"W","Ẅ":"W","Ẉ":"W","Ⱳ":"W","Ⓧ":"X","Ｘ":"X","Ẋ":"X","Ẍ":"X","Ⓨ":"Y","Ｙ":"Y","Ỳ":"Y","Ý":"Y","Ŷ":"Y","Ỹ":"Y","Ȳ":"Y","Ẏ":"Y","Ÿ":"Y","Ỷ":"Y","Ỵ":"Y","Ƴ":"Y","Ɏ":"Y","Ỿ":"Y","Ⓩ":"Z","Ｚ":"Z","Ź":"Z","Ẑ":"Z","Ż":"Z","Ž":"Z","Ẓ":"Z","Ẕ":"Z","Ƶ":"Z","Ȥ":"Z","Ɀ":"Z","Ⱬ":"Z","Ꝣ":"Z","ⓐ":"a","ａ":"a","ẚ":"a","à":"a","á":"a","â":"a","ầ":"a","ấ":"a","ẫ":"a","ẩ":"a","ã":"a","ā":"a","ă":"a","ằ":"a","ắ":"a","ẵ":"a","ẳ":"a","ȧ":"a","ǡ":"a","ä":"a","ǟ":"a","ả":"a","å":"a","ǻ":"a","ǎ":"a","ȁ":"a","ȃ":"a","ạ":"a","ậ":"a","ặ":"a","ḁ":"a","ą":"a","ⱥ":"a","ɐ":"a","ꜳ":"aa","æ":"ae","ǽ":"ae","ǣ":"ae","ꜵ":"ao","ꜷ":"au","ꜹ":"av","ꜻ":"av","ꜽ":"ay","ⓑ":"b","ｂ":"b","ḃ":"b","ḅ":"b","ḇ":"b","ƀ":"b","ƃ":"b","ɓ":"b","ⓒ":"c","ｃ":"c","ć":"c","ĉ":"c","ċ":"c","č":"c","ç":"c","ḉ":"c","ƈ":"c","ȼ":"c","ꜿ":"c","ↄ":"c","ⓓ":"d","ｄ":"d","ḋ":"d","ď":"d","ḍ":"d","ḑ":"d","ḓ":"d","ḏ":"d","đ":"d","ƌ":"d","ɖ":"d","ɗ":"d","ꝺ":"d","ǳ":"dz","ǆ":"dz","ⓔ":"e","ｅ":"e","è":"e","é":"e","ê":"e","ề":"e","ế":"e","ễ":"e","ể":"e","ẽ":"e","ē":"e","ḕ":"e","ḗ":"e","ĕ":"e","ė":"e","ë":"e","ẻ":"e","ě":"e","ȅ":"e","ȇ":"e","ẹ":"e","ệ":"e","ȩ":"e","ḝ":"e","ę":"e","ḙ":"e","ḛ":"e","ɇ":"e","ɛ":"e","ǝ":"e","ⓕ":"f","ｆ":"f","ḟ":"f","ƒ":"f","ꝼ":"f","ⓖ":"g","ｇ":"g","ǵ":"g","ĝ":"g","ḡ":"g","ğ":"g","ġ":"g","ǧ":"g","ģ":"g","ǥ":"g","ɠ":"g","ꞡ":"g","ᵹ":"g","ꝿ":"g","ⓗ":"h","ｈ":"h","ĥ":"h","ḣ":"h","ḧ":"h","ȟ":"h","ḥ":"h","ḩ":"h","ḫ":"h","ẖ":"h","ħ":"h","ⱨ":"h","ⱶ":"h","ɥ":"h","ƕ":"hv","ⓘ":"i","ｉ":"i","ì":"i","í":"i","î":"i","ĩ":"i","ī":"i","ĭ":"i","ï":"i","ḯ":"i","ỉ":"i","ǐ":"i","ȉ":"i","ȋ":"i","ị":"i","į":"i","ḭ":"i","ɨ":"i","ı":"i","ⓙ":"j","ｊ":"j","ĵ":"j","ǰ":"j","ɉ":"j","ⓚ":"k","ｋ":"k","ḱ":"k","ǩ":"k","ḳ":"k","ķ":"k","ḵ":"k","ƙ":"k","ⱪ":"k","ꝁ":"k","ꝃ":"k","ꝅ":"k","ꞣ":"k","ⓛ":"l","ｌ":"l","ŀ":"l","ĺ":"l","ľ":"l","ḷ":"l","ḹ":"l","ļ":"l","ḽ":"l","ḻ":"l","ſ":"l","ł":"l","ƚ":"l","ɫ":"l","ⱡ":"l","ꝉ":"l","ꞁ":"l","ꝇ":"l","ǉ":"lj","ⓜ":"m","ｍ":"m","ḿ":"m","ṁ":"m","ṃ":"m","ɱ":"m","ɯ":"m","ⓝ":"n","ｎ":"n","ǹ":"n","ń":"n","ñ":"n","ṅ":"n","ň":"n","ṇ":"n","ņ":"n","ṋ":"n","ṉ":"n","ƞ":"n","ɲ":"n","ŉ":"n","ꞑ":"n","ꞥ":"n","ǌ":"nj","ⓞ":"o","ｏ":"o","ò":"o","ó":"o","ô":"o","ồ":"o","ố":"o","ỗ":"o","ổ":"o","õ":"o","ṍ":"o","ȭ":"o","ṏ":"o","ō":"o","ṑ":"o","ṓ":"o","ŏ":"o","ȯ":"o","ȱ":"o","ö":"o","ȫ":"o","ỏ":"o","ő":"o","ǒ":"o","ȍ":"o","ȏ":"o","ơ":"o","ờ":"o","ớ":"o","ỡ":"o","ở":"o","ợ":"o","ọ":"o","ộ":"o","ǫ":"o","ǭ":"o","ø":"o","ǿ":"o","ɔ":"o","ꝋ":"o","ꝍ":"o","ɵ":"o","ƣ":"oi","ȣ":"ou","ꝏ":"oo","ⓟ":"p","ｐ":"p","ṕ":"p","ṗ":"p","ƥ":"p","ᵽ":"p","ꝑ":"p","ꝓ":"p","ꝕ":"p","ⓠ":"q","ｑ":"q","ɋ":"q","ꝗ":"q","ꝙ":"q","ⓡ":"r","ｒ":"r","ŕ":"r","ṙ":"r","ř":"r","ȑ":"r","ȓ":"r","ṛ":"r","ṝ":"r","ŗ":"r","ṟ":"r","ɍ":"r","ɽ":"r","ꝛ":"r","ꞧ":"r","ꞃ":"r","ⓢ":"s","ｓ":"s","ß":"s","ś":"s","ṥ":"s","ŝ":"s","ṡ":"s","š":"s","ṧ":"s","ṣ":"s","ṩ":"s","ș":"s","ş":"s","ȿ":"s","ꞩ":"s","ꞅ":"s","ẛ":"s","ⓣ":"t","ｔ":"t","ṫ":"t","ẗ":"t","ť":"t","ṭ":"t","ț":"t","ţ":"t","ṱ":"t","ṯ":"t","ŧ":"t","ƭ":"t","ʈ":"t","ⱦ":"t","ꞇ":"t","ꜩ":"tz","ⓤ":"u","ｕ":"u","ù":"u","ú":"u","û":"u","ũ":"u","ṹ":"u","ū":"u","ṻ":"u","ŭ":"u","ü":"u","ǜ":"u","ǘ":"u","ǖ":"u","ǚ":"u","ủ":"u","ů":"u","ű":"u","ǔ":"u","ȕ":"u","ȗ":"u","ư":"u","ừ":"u","ứ":"u","ữ":"u","ử":"u","ự":"u","ụ":"u","ṳ":"u","ų":"u","ṷ":"u","ṵ":"u","ʉ":"u","ⓥ":"v","ｖ":"v","ṽ":"v","ṿ":"v","ʋ":"v","ꝟ":"v","ʌ":"v","ꝡ":"vy","ⓦ":"w","ｗ":"w","ẁ":"w","ẃ":"w","ŵ":"w","ẇ":"w","ẅ":"w","ẘ":"w","ẉ":"w","ⱳ":"w","ⓧ":"x","ｘ":"x","ẋ":"x","ẍ":"x","ⓨ":"y","ｙ":"y","ỳ":"y","ý":"y","ŷ":"y","ỹ":"y","ȳ":"y","ẏ":"y","ÿ":"y","ỷ":"y","ẙ":"y","ỵ":"y","ƴ":"y","ɏ":"y","ỿ":"y","ⓩ":"z","ｚ":"z","ź":"z","ẑ":"z","ż":"z","ž":"z","ẓ":"z","ẕ":"z","ƶ":"z","ȥ":"z","ɀ":"z","ⱬ":"z","ꝣ":"z","Ά":"Α","Έ":"Ε","Ή":"Η","Ί":"Ι","Ϊ":"Ι","Ό":"Ο","Ύ":"Υ","Ϋ":"Υ","Ώ":"Ω","ά":"α","έ":"ε","ή":"η","ί":"ι","ϊ":"ι","ΐ":"ι","ό":"ο","ύ":"υ","ϋ":"υ","ΰ":"υ","ω":"ω","ς":"σ"};return a}),b.define("select2/data/base",["../utils"],function(a){function b(a,c){b.__super__.constructor.call(this)}return a.Extend(b,a.Observable),b.prototype.current=function(a){throw new Error("The `current` method must be defined in child classes.")},b.prototype.query=function(a,b){throw new Error("The `query` method must be defined in child classes.")},b.prototype.bind=function(a,b){},b.prototype.destroy=function(){},b.prototype.generateResultId=function(b,c){var d=b.id+"-result-";return d+=a.generateChars(4),d+=null!=c.id?"-"+c.id.toString():"-"+a.generateChars(4)},b}),b.define("select2/data/select",["./base","../utils","jquery"],function(a,b,c){function d(a,b){this.$element=a,this.options=b,d.__super__.constructor.call(this)}return b.Extend(d,a),d.prototype.current=function(a){var b=[],d=this;this.$element.find(":selected").each(function(){var a=c(this),e=d.item(a);b.push(e)}),a(b)},d.prototype.select=function(a){var b=this;if(a.selected=!0,c(a.element).is("option"))return a.element.selected=!0,void this.$element.trigger("change");if(this.$element.prop("multiple"))this.current(function(d){var e=[];a=[a],a.push.apply(a,d);for(var f=0;f<a.length;f++){var g=a[f].id;-1===c.inArray(g,e)&&e.push(g)}b.$element.val(e),b.$element.trigger("change")});else{var d=a.id;this.$element.val(d),this.$element.trigger("change")}},d.prototype.unselect=function(a){
var b=this;if(this.$element.prop("multiple"))return a.selected=!1,c(a.element).is("option")?(a.element.selected=!1,void this.$element.trigger("change")):void this.current(function(d){for(var e=[],f=0;f<d.length;f++){var g=d[f].id;g!==a.id&&-1===c.inArray(g,e)&&e.push(g)}b.$element.val(e),b.$element.trigger("change")})},d.prototype.bind=function(a,b){var c=this;this.container=a,a.on("select",function(a){c.select(a.data)}),a.on("unselect",function(a){c.unselect(a.data)})},d.prototype.destroy=function(){this.$element.find("*").each(function(){c.removeData(this,"data")})},d.prototype.query=function(a,b){var d=[],e=this,f=this.$element.children();f.each(function(){var b=c(this);if(b.is("option")||b.is("optgroup")){var f=e.item(b),g=e.matches(a,f);null!==g&&d.push(g)}}),b({results:d})},d.prototype.addOptions=function(a){b.appendMany(this.$element,a)},d.prototype.option=function(a){var b;a.children?(b=document.createElement("optgroup"),b.label=a.text):(b=document.createElement("option"),void 0!==b.textContent?b.textContent=a.text:b.innerText=a.text),a.id&&(b.value=a.id),a.disabled&&(b.disabled=!0),a.selected&&(b.selected=!0),a.title&&(b.title=a.title);var d=c(b),e=this._normalizeItem(a);return e.element=b,c.data(b,"data",e),d},d.prototype.item=function(a){var b={};if(b=c.data(a[0],"data"),null!=b)return b;if(a.is("option"))b={id:a.val(),text:a.text(),disabled:a.prop("disabled"),selected:a.prop("selected"),title:a.prop("title")};else if(a.is("optgroup")){b={text:a.prop("label"),children:[],title:a.prop("title")};for(var d=a.children("option"),e=[],f=0;f<d.length;f++){var g=c(d[f]),h=this.item(g);e.push(h)}b.children=e}return b=this._normalizeItem(b),b.element=a[0],c.data(a[0],"data",b),b},d.prototype._normalizeItem=function(a){c.isPlainObject(a)||(a={id:a,text:a}),a=c.extend({},{text:""},a);var b={selected:!1,disabled:!1};return null!=a.id&&(a.id=a.id.toString()),null!=a.text&&(a.text=a.text.toString()),null==a._resultId&&a.id&&null!=this.container&&(a._resultId=this.generateResultId(this.container,a)),c.extend({},b,a)},d.prototype.matches=function(a,b){var c=this.options.get("matcher");return c(a,b)},d}),b.define("select2/data/array",["./select","../utils","jquery"],function(a,b,c){function d(a,b){var c=b.get("data")||[];d.__super__.constructor.call(this,a,b),this.addOptions(this.convertToOptions(c))}return b.Extend(d,a),d.prototype.select=function(a){var b=this.$element.find("option").filter(function(b,c){return c.value==a.id.toString()});0===b.length&&(b=this.option(a),this.addOptions(b)),d.__super__.select.call(this,a)},d.prototype.convertToOptions=function(a){function d(a){return function(){return c(this).val()==a.id}}for(var e=this,f=this.$element.find("option"),g=f.map(function(){return e.item(c(this)).id}).get(),h=[],i=0;i<a.length;i++){var j=this._normalizeItem(a[i]);if(c.inArray(j.id,g)>=0){var k=f.filter(d(j)),l=this.item(k),m=c.extend(!0,{},l,j),n=this.option(m);k.replaceWith(n)}else{var o=this.option(j);if(j.children){var p=this.convertToOptions(j.children);b.appendMany(o,p)}h.push(o)}}return h},d}),b.define("select2/data/ajax",["./array","../utils","jquery"],function(a,b,c){function d(a,b){this.ajaxOptions=this._applyDefaults(b.get("ajax")),null!=this.ajaxOptions.processResults&&(this.processResults=this.ajaxOptions.processResults),d.__super__.constructor.call(this,a,b)}return b.Extend(d,a),d.prototype._applyDefaults=function(a){var b={data:function(a){return c.extend({},a,{q:a.term})},transport:function(a,b,d){var e=c.ajax(a);return e.then(b),e.fail(d),e}};return c.extend({},b,a,!0)},d.prototype.processResults=function(a){return a},d.prototype.query=function(a,b){function d(){var d=f.transport(f,function(d){var f=e.processResults(d,a);e.options.get("debug")&&window.console&&console.error&&(f&&f.results&&c.isArray(f.results)||console.error("Select2: The AJAX results did not return an array in the `results` key of the response.")),b(f)},function(){});e._request=d}var e=this;null!=this._request&&(c.isFunction(this._request.abort)&&this._request.abort(),this._request=null);var f=c.extend({type:"GET"},this.ajaxOptions);"function"==typeof f.url&&(f.url=f.url.call(this.$element,a)),"function"==typeof f.data&&(f.data=f.data.call(this.$element,a)),this.ajaxOptions.delay&&""!==a.term?(this._queryTimeout&&window.clearTimeout(this._queryTimeout),this._queryTimeout=window.setTimeout(d,this.ajaxOptions.delay)):d()},d}),b.define("select2/data/tags",["jquery"],function(a){function b(b,c,d){var e=d.get("tags"),f=d.get("createTag");if(void 0!==f&&(this.createTag=f),b.call(this,c,d),a.isArray(e))for(var g=0;g<e.length;g++){var h=e[g],i=this._normalizeItem(h),j=this.option(i);this.$element.append(j)}}return b.prototype.query=function(a,b,c){function d(a,f){for(var g=a.results,h=0;h<g.length;h++){var i=g[h],j=null!=i.children&&!d({results:i.children},!0),k=i.text===b.term;if(k||j)return f?!1:(a.data=g,void c(a))}if(f)return!0;var l=e.createTag(b);if(null!=l){var m=e.option(l);m.attr("data-select2-tag",!0),e.addOptions([m]),e.insertTag(g,l)}a.results=g,c(a)}var e=this;return this._removeOldTags(),null==b.term||null!=b.page?void a.call(this,b,c):void a.call(this,b,d)},b.prototype.createTag=function(b,c){var d=a.trim(c.term);return""===d?null:{id:d,text:d}},b.prototype.insertTag=function(a,b,c){b.unshift(c)},b.prototype._removeOldTags=function(b){var c=(this._lastTag,this.$element.find("option[data-select2-tag]"));c.each(function(){this.selected||a(this).remove()})},b}),b.define("select2/data/tokenizer",["jquery"],function(a){function b(a,b,c){var d=c.get("tokenizer");void 0!==d&&(this.tokenizer=d),a.call(this,b,c)}return b.prototype.bind=function(a,b,c){a.call(this,b,c),this.$search=b.dropdown.$search||b.selection.$search||c.find(".select2-search__field")},b.prototype.query=function(a,b,c){function d(a){e.trigger("select",{data:a})}var e=this;b.term=b.term||"";var f=this.tokenizer(b,this.options,d);f.term!==b.term&&(this.$search.length&&(this.$search.val(f.term),this.$search.focus()),b.term=f.term),a.call(this,b,c)},b.prototype.tokenizer=function(b,c,d,e){for(var f=d.get("tokenSeparators")||[],g=c.term,h=0,i=this.createTag||function(a){return{id:a.term,text:a.term}};h<g.length;){var j=g[h];if(-1!==a.inArray(j,f)){var k=g.substr(0,h),l=a.extend({},c,{term:k}),m=i(l);null!=m?(e(m),g=g.substr(h+1)||"",h=0):h++}else h++}return{term:g}},b}),b.define("select2/data/minimumInputLength",[],function(){function a(a,b,c){this.minimumInputLength=c.get("minimumInputLength"),a.call(this,b,c)}return a.prototype.query=function(a,b,c){return b.term=b.term||"",b.term.length<this.minimumInputLength?void this.trigger("results:message",{message:"inputTooShort",args:{minimum:this.minimumInputLength,input:b.term,params:b}}):void a.call(this,b,c)},a}),b.define("select2/data/maximumInputLength",[],function(){function a(a,b,c){this.maximumInputLength=c.get("maximumInputLength"),a.call(this,b,c)}return a.prototype.query=function(a,b,c){return b.term=b.term||"",this.maximumInputLength>0&&b.term.length>this.maximumInputLength?void this.trigger("results:message",{message:"inputTooLong",args:{maximum:this.maximumInputLength,input:b.term,params:b}}):void a.call(this,b,c)},a}),b.define("select2/data/maximumSelectionLength",[],function(){function a(a,b,c){this.maximumSelectionLength=c.get("maximumSelectionLength"),a.call(this,b,c)}return a.prototype.query=function(a,b,c){var d=this;this.current(function(e){var f=null!=e?e.length:0;return d.maximumSelectionLength>0&&f>=d.maximumSelectionLength?void d.trigger("results:message",{message:"maximumSelected",args:{maximum:d.maximumSelectionLength}}):void a.call(d,b,c)})},a}),b.define("select2/dropdown",["jquery","./utils"],function(a,b){function c(a,b){this.$element=a,this.options=b,c.__super__.constructor.call(this)}return b.Extend(c,b.Observable),c.prototype.render=function(){var b=a('<span class="select2-dropdown"><span class="select2-results"></span></span>');return b.attr("dir",this.options.get("dir")),this.$dropdown=b,b},c.prototype.bind=function(){},c.prototype.position=function(a,b){},c.prototype.destroy=function(){this.$dropdown.remove()},c}),b.define("select2/dropdown/search",["jquery","../utils"],function(a,b){function c(){}return c.prototype.render=function(b){var c=b.call(this),d=a('<span class="select2-search select2-search--dropdown"><input class="select2-search__field" type="search" tabindex="-1" autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" role="textbox" /></span>');return this.$searchContainer=d,this.$search=d.find("input"),c.prepend(d),c},c.prototype.bind=function(b,c,d){var e=this;b.call(this,c,d),this.$search.on("keydown",function(a){e.trigger("keypress",a),e._keyUpPrevented=a.isDefaultPrevented()}),this.$search.on("input",function(b){a(this).off("keyup")}),this.$search.on("keyup input",function(a){e.handleSearch(a)}),c.on("open",function(){e.$search.attr("tabindex",0),e.$search.focus(),window.setTimeout(function(){e.$search.focus()},0)}),c.on("close",function(){e.$search.attr("tabindex",-1),e.$search.val("")}),c.on("results:all",function(a){if(null==a.query.term||""===a.query.term){var b=e.showSearch(a);b?e.$searchContainer.removeClass("select2-search--hide"):e.$searchContainer.addClass("select2-search--hide")}})},c.prototype.handleSearch=function(a){if(!this._keyUpPrevented){var b=this.$search.val();this.trigger("query",{term:b})}this._keyUpPrevented=!1},c.prototype.showSearch=function(a,b){return!0},c}),b.define("select2/dropdown/hidePlaceholder",[],function(){function a(a,b,c,d){this.placeholder=this.normalizePlaceholder(c.get("placeholder")),a.call(this,b,c,d)}return a.prototype.append=function(a,b){b.results=this.removePlaceholder(b.results),a.call(this,b)},a.prototype.normalizePlaceholder=function(a,b){return"string"==typeof b&&(b={id:"",text:b}),b},a.prototype.removePlaceholder=function(a,b){for(var c=b.slice(0),d=b.length-1;d>=0;d--){var e=b[d];this.placeholder.id===e.id&&c.splice(d,1)}return c},a}),b.define("select2/dropdown/infiniteScroll",["jquery"],function(a){function b(a,b,c,d){this.lastParams={},a.call(this,b,c,d),this.$loadingMore=this.createLoadingMore(),this.loading=!1}return b.prototype.append=function(a,b){this.$loadingMore.remove(),this.loading=!1,a.call(this,b),this.showLoadingMore(b)&&this.$results.append(this.$loadingMore)},b.prototype.bind=function(b,c,d){var e=this;b.call(this,c,d),c.on("query",function(a){e.lastParams=a,e.loading=!0}),c.on("query:append",function(a){e.lastParams=a,e.loading=!0}),this.$results.on("scroll",function(){var b=a.contains(document.documentElement,e.$loadingMore[0]);if(!e.loading&&b){var c=e.$results.offset().top+e.$results.outerHeight(!1),d=e.$loadingMore.offset().top+e.$loadingMore.outerHeight(!1);c+50>=d&&e.loadMore()}})},b.prototype.loadMore=function(){this.loading=!0;var b=a.extend({},{page:1},this.lastParams);b.page++,this.trigger("query:append",b)},b.prototype.showLoadingMore=function(a,b){return b.pagination&&b.pagination.more},b.prototype.createLoadingMore=function(){var b=a('<li class="select2-results__option select2-results__option--load-more"role="treeitem" aria-disabled="true"></li>'),c=this.options.get("translations").get("loadingMore");return b.html(c(this.lastParams)),b},b}),b.define("select2/dropdown/attachBody",["jquery","../utils"],function(a,b){function c(b,c,d){this.$dropdownParent=d.get("dropdownParent")||a(document.body),b.call(this,c,d)}return c.prototype.bind=function(a,b,c){var d=this,e=!1;a.call(this,b,c),b.on("open",function(){d._showDropdown(),d._attachPositioningHandler(b),e||(e=!0,b.on("results:all",function(){d._positionDropdown(),d._resizeDropdown()}),b.on("results:append",function(){d._positionDropdown(),d._resizeDropdown()}))}),b.on("close",function(){d._hideDropdown(),d._detachPositioningHandler(b)}),this.$dropdownContainer.on("mousedown",function(a){a.stopPropagation()})},c.prototype.destroy=function(a){a.call(this),this.$dropdownContainer.remove()},c.prototype.position=function(a,b,c){b.attr("class",c.attr("class")),b.removeClass("select2"),b.addClass("select2-container--open"),b.css({position:"absolute",top:-999999}),this.$container=c},c.prototype.render=function(b){var c=a("<span></span>"),d=b.call(this);return c.append(d),this.$dropdownContainer=c,c},c.prototype._hideDropdown=function(a){this.$dropdownContainer.detach()},c.prototype._attachPositioningHandler=function(c,d){var e=this,f="scroll.select2."+d.id,g="resize.select2."+d.id,h="orientationchange.select2."+d.id,i=this.$container.parents().filter(b.hasScroll);i.each(function(){a(this).data("select2-scroll-position",{x:a(this).scrollLeft(),y:a(this).scrollTop()})}),i.on(f,function(b){var c=a(this).data("select2-scroll-position");a(this).scrollTop(c.y)}),a(window).on(f+" "+g+" "+h,function(a){e._positionDropdown(),e._resizeDropdown()})},c.prototype._detachPositioningHandler=function(c,d){var e="scroll.select2."+d.id,f="resize.select2."+d.id,g="orientationchange.select2."+d.id,h=this.$container.parents().filter(b.hasScroll);h.off(e),a(window).off(e+" "+f+" "+g)},c.prototype._positionDropdown=function(){var b=a(window),c=this.$dropdown.hasClass("select2-dropdown--above"),d=this.$dropdown.hasClass("select2-dropdown--below"),e=null,f=(this.$container.position(),this.$container.offset());f.bottom=f.top+this.$container.outerHeight(!1);var g={height:this.$container.outerHeight(!1)};g.top=f.top,g.bottom=f.top+g.height;var h={height:this.$dropdown.outerHeight(!1)},i={top:b.scrollTop(),bottom:b.scrollTop()+b.height()},j=i.top<f.top-h.height,k=i.bottom>f.bottom+h.height,l={left:f.left,top:g.bottom};if("static"!==this.$dropdownParent[0].style.position){var m=this.$dropdownParent.offset();l.top-=m.top,l.left-=m.left}c||d||(e="below"),k||!j||c?!j&&k&&c&&(e="below"):e="above",("above"==e||c&&"below"!==e)&&(l.top=g.top-h.height),null!=e&&(this.$dropdown.removeClass("select2-dropdown--below select2-dropdown--above").addClass("select2-dropdown--"+e),this.$container.removeClass("select2-container--below select2-container--above").addClass("select2-container--"+e)),this.$dropdownContainer.css(l)},c.prototype._resizeDropdown=function(){var a={width:this.$container.outerWidth(!1)+"px"};this.options.get("dropdownAutoWidth")&&(a.minWidth=a.width,a.width="auto"),this.$dropdown.css(a)},c.prototype._showDropdown=function(a){this.$dropdownContainer.appendTo(this.$dropdownParent),this._positionDropdown(),this._resizeDropdown()},c}),b.define("select2/dropdown/minimumResultsForSearch",[],function(){function a(b){for(var c=0,d=0;d<b.length;d++){var e=b[d];e.children?c+=a(e.children):c++}return c}function b(a,b,c,d){this.minimumResultsForSearch=c.get("minimumResultsForSearch"),this.minimumResultsForSearch<0&&(this.minimumResultsForSearch=1/0),a.call(this,b,c,d)}return b.prototype.showSearch=function(b,c){return a(c.data.results)<this.minimumResultsForSearch?!1:b.call(this,c)},b}),b.define("select2/dropdown/selectOnClose",[],function(){function a(){}return a.prototype.bind=function(a,b,c){var d=this;a.call(this,b,c),b.on("close",function(){d._handleSelectOnClose()})},a.prototype._handleSelectOnClose=function(){var a=this.getHighlightedResults();if(!(a.length<1)){var b=a.data("data");null!=b.element&&b.element.selected||null==b.element&&b.selected||this.trigger("select",{data:b})}},a}),b.define("select2/dropdown/closeOnSelect",[],function(){function a(){}return a.prototype.bind=function(a,b,c){var d=this;a.call(this,b,c),b.on("select",function(a){d._selectTriggered(a)}),b.on("unselect",function(a){d._selectTriggered(a)})},a.prototype._selectTriggered=function(a,b){var c=b.originalEvent;c&&c.ctrlKey||this.trigger("close",{})},a}),b.define("select2/i18n/en",[],function(){return{errorLoading:function(){return"The results could not be loaded."},inputTooLong:function(a){var b=a.input.length-a.maximum,c="Please delete "+b+" character";return 1!=b&&(c+="s"),c},inputTooShort:function(a){var b=a.minimum-a.input.length,c="Please enter "+b+" or more characters";return c},loadingMore:function(){return"Loading more results…"},maximumSelected:function(a){var b="You can only select "+a.maximum+" item";return 1!=a.maximum&&(b+="s"),b},noResults:function(){return"No results found"},searching:function(){return"Searching…"}}}),b.define("select2/defaults",["jquery","require","./results","./selection/single","./selection/multiple","./selection/placeholder","./selection/allowClear","./selection/search","./selection/eventRelay","./utils","./translation","./diacritics","./data/select","./data/array","./data/ajax","./data/tags","./data/tokenizer","./data/minimumInputLength","./data/maximumInputLength","./data/maximumSelectionLength","./dropdown","./dropdown/search","./dropdown/hidePlaceholder","./dropdown/infiniteScroll","./dropdown/attachBody","./dropdown/minimumResultsForSearch","./dropdown/selectOnClose","./dropdown/closeOnSelect","./i18n/en"],function(a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z,A,B,C){function D(){this.reset()}D.prototype.apply=function(l){if(l=a.extend({},this.defaults,l),null==l.dataAdapter){if(null!=l.ajax?l.dataAdapter=o:null!=l.data?l.dataAdapter=n:l.dataAdapter=m,l.minimumInputLength>0&&(l.dataAdapter=j.Decorate(l.dataAdapter,r)),l.maximumInputLength>0&&(l.dataAdapter=j.Decorate(l.dataAdapter,s)),l.maximumSelectionLength>0&&(l.dataAdapter=j.Decorate(l.dataAdapter,t)),l.tags&&(l.dataAdapter=j.Decorate(l.dataAdapter,p)),(null!=l.tokenSeparators||null!=l.tokenizer)&&(l.dataAdapter=j.Decorate(l.dataAdapter,q)),null!=l.query){var C=b(l.amdBase+"compat/query");l.dataAdapter=j.Decorate(l.dataAdapter,C)}if(null!=l.initSelection){var D=b(l.amdBase+"compat/initSelection");l.dataAdapter=j.Decorate(l.dataAdapter,D)}}if(null==l.resultsAdapter&&(l.resultsAdapter=c,null!=l.ajax&&(l.resultsAdapter=j.Decorate(l.resultsAdapter,x)),null!=l.placeholder&&(l.resultsAdapter=j.Decorate(l.resultsAdapter,w)),l.selectOnClose&&(l.resultsAdapter=j.Decorate(l.resultsAdapter,A))),null==l.dropdownAdapter){if(l.multiple)l.dropdownAdapter=u;else{var E=j.Decorate(u,v);l.dropdownAdapter=E}if(0!==l.minimumResultsForSearch&&(l.dropdownAdapter=j.Decorate(l.dropdownAdapter,z)),l.closeOnSelect&&(l.dropdownAdapter=j.Decorate(l.dropdownAdapter,B)),null!=l.dropdownCssClass||null!=l.dropdownCss||null!=l.adaptDropdownCssClass){var F=b(l.amdBase+"compat/dropdownCss");l.dropdownAdapter=j.Decorate(l.dropdownAdapter,F)}l.dropdownAdapter=j.Decorate(l.dropdownAdapter,y)}if(null==l.selectionAdapter){if(l.multiple?l.selectionAdapter=e:l.selectionAdapter=d,null!=l.placeholder&&(l.selectionAdapter=j.Decorate(l.selectionAdapter,f)),l.allowClear&&(l.selectionAdapter=j.Decorate(l.selectionAdapter,g)),l.multiple&&(l.selectionAdapter=j.Decorate(l.selectionAdapter,h)),null!=l.containerCssClass||null!=l.containerCss||null!=l.adaptContainerCssClass){var G=b(l.amdBase+"compat/containerCss");l.selectionAdapter=j.Decorate(l.selectionAdapter,G)}l.selectionAdapter=j.Decorate(l.selectionAdapter,i)}if("string"==typeof l.language)if(l.language.indexOf("-")>0){var H=l.language.split("-"),I=H[0];l.language=[l.language,I]}else l.language=[l.language];if(a.isArray(l.language)){var J=new k;l.language.push("en");for(var K=l.language,L=0;L<K.length;L++){var M=K[L],N={};try{N=k.loadPath(M)}catch(O){try{M=this.defaults.amdLanguageBase+M,N=k.loadPath(M)}catch(P){l.debug&&window.console&&console.warn&&console.warn('Select2: The language file for "'+M+'" could not be automatically loaded. A fallback will be used instead.');continue}}J.extend(N)}l.translations=J}else{var Q=k.loadPath(this.defaults.amdLanguageBase+"en"),R=new k(l.language);R.extend(Q),l.translations=R}return l},D.prototype.reset=function(){function b(a){function b(a){return l[a]||a}return a.replace(/[^\u0000-\u007E]/g,b)}function c(d,e){if(""===a.trim(d.term))return e;if(e.children&&e.children.length>0){for(var f=a.extend(!0,{},e),g=e.children.length-1;g>=0;g--){var h=e.children[g],i=c(d,h);null==i&&f.children.splice(g,1)}return f.children.length>0?f:c(d,f)}var j=b(e.text).toUpperCase(),k=b(d.term).toUpperCase();return j.indexOf(k)>-1?e:null}this.defaults={amdBase:"./",amdLanguageBase:"./i18n/",closeOnSelect:!0,debug:!1,dropdownAutoWidth:!1,escapeMarkup:j.escapeMarkup,language:C,matcher:c,minimumInputLength:0,maximumInputLength:0,maximumSelectionLength:0,minimumResultsForSearch:0,selectOnClose:!1,sorter:function(a){return a},templateResult:function(a){return a.text},templateSelection:function(a){return a.text},theme:"default",width:"resolve"}},D.prototype.set=function(b,c){var d=a.camelCase(b),e={};e[d]=c;var f=j._convertData(e);a.extend(this.defaults,f)};var E=new D;return E}),b.define("select2/options",["require","jquery","./defaults","./utils"],function(a,b,c,d){function e(b,e){if(this.options=b,null!=e&&this.fromElement(e),this.options=c.apply(this.options),e&&e.is("input")){var f=a(this.get("amdBase")+"compat/inputData");this.options.dataAdapter=d.Decorate(this.options.dataAdapter,f)}}return e.prototype.fromElement=function(a){var c=["select2"];null==this.options.multiple&&(this.options.multiple=a.prop("multiple")),null==this.options.disabled&&(this.options.disabled=a.prop("disabled")),null==this.options.language&&(a.prop("lang")?this.options.language=a.prop("lang").toLowerCase():a.closest("[lang]").prop("lang")&&(this.options.language=a.closest("[lang]").prop("lang"))),null==this.options.dir&&(a.prop("dir")?this.options.dir=a.prop("dir"):a.closest("[dir]").prop("dir")?this.options.dir=a.closest("[dir]").prop("dir"):this.options.dir="ltr"),a.prop("disabled",this.options.disabled),a.prop("multiple",this.options.multiple),a.data("select2Tags")&&(this.options.debug&&window.console&&console.warn&&console.warn('Select2: The `data-select2-tags` attribute has been changed to use the `data-data` and `data-tags="true"` attributes and will be removed in future versions of Select2.'),a.data("data",a.data("select2Tags")),a.data("tags",!0)),a.data("ajaxUrl")&&(this.options.debug&&window.console&&console.warn&&console.warn("Select2: The `data-ajax-url` attribute has been changed to `data-ajax--url` and support for the old attribute will be removed in future versions of Select2."),a.attr("ajax--url",a.data("ajaxUrl")),a.data("ajax--url",a.data("ajaxUrl")));var e={};e=b.fn.jquery&&"1."==b.fn.jquery.substr(0,2)&&a[0].dataset?b.extend(!0,{},a[0].dataset,a.data()):a.data();var f=b.extend(!0,{},e);f=d._convertData(f);for(var g in f)b.inArray(g,c)>-1||(b.isPlainObject(this.options[g])?b.extend(this.options[g],f[g]):this.options[g]=f[g]);return this},e.prototype.get=function(a){return this.options[a]},e.prototype.set=function(a,b){this.options[a]=b},e}),b.define("select2/core",["jquery","./options","./utils","./keys"],function(a,b,c,d){var e=function(a,c){null!=a.data("select2")&&a.data("select2").destroy(),this.$element=a,this.id=this._generateId(a),c=c||{},this.options=new b(c,a),e.__super__.constructor.call(this);var d=a.attr("tabindex")||0;a.data("old-tabindex",d),a.attr("tabindex","-1");var f=this.options.get("dataAdapter");this.dataAdapter=new f(a,this.options);var g=this.render();this._placeContainer(g);var h=this.options.get("selectionAdapter");this.selection=new h(a,this.options),this.$selection=this.selection.render(),this.selection.position(this.$selection,g);var i=this.options.get("dropdownAdapter");this.dropdown=new i(a,this.options),this.$dropdown=this.dropdown.render(),this.dropdown.position(this.$dropdown,g);var j=this.options.get("resultsAdapter");this.results=new j(a,this.options,this.dataAdapter),this.$results=this.results.render(),this.results.position(this.$results,this.$dropdown);var k=this;this._bindAdapters(),this._registerDomEvents(),this._registerDataEvents(),this._registerSelectionEvents(),this._registerDropdownEvents(),this._registerResultsEvents(),this._registerEvents(),this.dataAdapter.current(function(a){k.trigger("selection:update",{data:a})}),a.addClass("select2-hidden-accessible"),a.attr("aria-hidden","true"),this._syncAttributes(),a.data("select2",this)};return c.Extend(e,c.Observable),e.prototype._generateId=function(a){var b="";return b=null!=a.attr("id")?a.attr("id"):null!=a.attr("name")?a.attr("name")+"-"+c.generateChars(2):c.generateChars(4),b="select2-"+b},e.prototype._placeContainer=function(a){a.insertAfter(this.$element);var b=this._resolveWidth(this.$element,this.options.get("width"));null!=b&&a.css("width",b)},e.prototype._resolveWidth=function(a,b){var c=/^width:(([-+]?([0-9]*\.)?[0-9]+)(px|em|ex|%|in|cm|mm|pt|pc))/i;if("resolve"==b){var d=this._resolveWidth(a,"style");return null!=d?d:this._resolveWidth(a,"element")}if("element"==b){var e=a.outerWidth(!1);return 0>=e?"auto":e+"px"}if("style"==b){var f=a.attr("style");if("string"!=typeof f)return null;for(var g=f.split(";"),h=0,i=g.length;i>h;h+=1){var j=g[h].replace(/\s/g,""),k=j.match(c);if(null!==k&&k.length>=1)return k[1]}return null}return b},e.prototype._bindAdapters=function(){this.dataAdapter.bind(this,this.$container),this.selection.bind(this,this.$container),this.dropdown.bind(this,this.$container),this.results.bind(this,this.$container)},e.prototype._registerDomEvents=function(){var b=this;this.$element.on("change.select2",function(){b.dataAdapter.current(function(a){b.trigger("selection:update",{data:a})})}),this._sync=c.bind(this._syncAttributes,this),this.$element[0].attachEvent&&this.$element[0].attachEvent("onpropertychange",this._sync);var d=window.MutationObserver||window.WebKitMutationObserver||window.MozMutationObserver;null!=d?(this._observer=new d(function(c){a.each(c,b._sync)}),this._observer.observe(this.$element[0],{attributes:!0,subtree:!1})):this.$element[0].addEventListener&&this.$element[0].addEventListener("DOMAttrModified",b._sync,!1)},e.prototype._registerDataEvents=function(){var a=this;this.dataAdapter.on("*",function(b,c){a.trigger(b,c)})},e.prototype._registerSelectionEvents=function(){var b=this,c=["toggle","focus"];this.selection.on("toggle",function(){b.toggleDropdown()}),this.selection.on("focus",function(a){b.focus(a)}),this.selection.on("*",function(d,e){-1===a.inArray(d,c)&&b.trigger(d,e)})},e.prototype._registerDropdownEvents=function(){var a=this;this.dropdown.on("*",function(b,c){a.trigger(b,c)})},e.prototype._registerResultsEvents=function(){var a=this;this.results.on("*",function(b,c){a.trigger(b,c)})},e.prototype._registerEvents=function(){var a=this;this.on("open",function(){a.$container.addClass("select2-container--open")}),this.on("close",function(){a.$container.removeClass("select2-container--open")}),this.on("enable",function(){a.$container.removeClass("select2-container--disabled")}),this.on("disable",function(){a.$container.addClass("select2-container--disabled")}),this.on("blur",function(){a.$container.removeClass("select2-container--focus")}),this.on("query",function(b){a.isOpen()||a.trigger("open",{}),this.dataAdapter.query(b,function(c){a.trigger("results:all",{data:c,query:b})})}),this.on("query:append",function(b){this.dataAdapter.query(b,function(c){a.trigger("results:append",{data:c,query:b})})}),this.on("keypress",function(b){var c=b.which;a.isOpen()?c===d.ESC||c===d.TAB||c===d.UP&&b.altKey?(a.close(),b.preventDefault()):c===d.ENTER?(a.trigger("results:select",{}),b.preventDefault()):c===d.SPACE&&b.ctrlKey?(a.trigger("results:toggle",{}),b.preventDefault()):c===d.UP?(a.trigger("results:previous",{}),b.preventDefault()):c===d.DOWN&&(a.trigger("results:next",{}),b.preventDefault()):(c===d.ENTER||c===d.SPACE||c===d.DOWN&&b.altKey)&&(a.open(),b.preventDefault())})},e.prototype._syncAttributes=function(){this.options.set("disabled",this.$element.prop("disabled")),this.options.get("disabled")?(this.isOpen()&&this.close(),this.trigger("disable",{})):this.trigger("enable",{})},e.prototype.trigger=function(a,b){var c=e.__super__.trigger,d={open:"opening",close:"closing",select:"selecting",unselect:"unselecting"};if(void 0===b&&(b={}),a in d){var f=d[a],g={prevented:!1,name:a,args:b};if(c.call(this,f,g),g.prevented)return void(b.prevented=!0)}c.call(this,a,b)},e.prototype.toggleDropdown=function(){this.options.get("disabled")||(this.isOpen()?this.close():this.open())},e.prototype.open=function(){this.isOpen()||this.trigger("query",{})},e.prototype.close=function(){this.isOpen()&&this.trigger("close",{})},e.prototype.isOpen=function(){return this.$container.hasClass("select2-container--open")},e.prototype.hasFocus=function(){return this.$container.hasClass("select2-container--focus")},e.prototype.focus=function(a){this.hasFocus()||(this.$container.addClass("select2-container--focus"),this.trigger("focus",{}))},e.prototype.enable=function(a){this.options.get("debug")&&window.console&&console.warn&&console.warn('Select2: The `select2("enable")` method has been deprecated and will be removed in later Select2 versions. Use $element.prop("disabled") instead.'),(null==a||0===a.length)&&(a=[!0]);var b=!a[0];this.$element.prop("disabled",b)},e.prototype.data=function(){this.options.get("debug")&&arguments.length>0&&window.console&&console.warn&&console.warn('Select2: Data can no longer be set using `select2("data")`. You should consider setting the value instead using `$element.val()`.');var a=[];return this.dataAdapter.current(function(b){a=b}),a},e.prototype.val=function(b){if(this.options.get("debug")&&window.console&&console.warn&&console.warn('Select2: The `select2("val")` method has been deprecated and will be removed in later Select2 versions. Use $element.val() instead.'),null==b||0===b.length)return this.$element.val();var c=b[0];a.isArray(c)&&(c=a.map(c,function(a){return a.toString()})),this.$element.val(c).trigger("change")},e.prototype.destroy=function(){this.$container.remove(),this.$element[0].detachEvent&&this.$element[0].detachEvent("onpropertychange",this._sync),null!=this._observer?(this._observer.disconnect(),this._observer=null):this.$element[0].removeEventListener&&this.$element[0].removeEventListener("DOMAttrModified",this._sync,!1),this._sync=null,this.$element.off(".select2"),this.$element.attr("tabindex",this.$element.data("old-tabindex")),this.$element.removeClass("select2-hidden-accessible"),this.$element.attr("aria-hidden","false"),this.$element.removeData("select2"),this.dataAdapter.destroy(),this.selection.destroy(),this.dropdown.destroy(),this.results.destroy(),this.dataAdapter=null,this.selection=null,this.dropdown=null,this.results=null},e.prototype.render=function(){var b=a('<span class="select2 select2-container"><span class="selection"></span><span class="dropdown-wrapper" aria-hidden="true"></span></span>');return b.attr("dir",this.options.get("dir")),this.$container=b,this.$container.addClass("select2-container--"+this.options.get("theme")),b.data("element",this.$element),b},e}),b.define("jquery-mousewheel",["jquery"],function(a){return a}),b.define("jquery.select2",["jquery","jquery-mousewheel","./select2/core","./select2/defaults"],function(a,b,c,d){if(null==a.fn.select2){var e=["open","close","destroy"];a.fn.select2=function(b){if(b=b||{},"object"==typeof b)return this.each(function(){var d=a.extend(!0,{},b);new c(a(this),d)}),this;if("string"==typeof b){var d;return this.each(function(){var c=a(this).data("select2");null==c&&window.console&&console.error&&console.error("The select2('"+b+"') method was called on an element that is not using Select2.");var e=Array.prototype.slice.call(arguments,1);d=c[b].apply(c,e)}),a.inArray(b,e)>-1?this:d}throw new Error("Invalid arguments for Select2: "+b)}}return null==a.fn.select2.defaults&&(a.fn.select2.defaults=d),c}),{define:b.define,require:b.require}}(),c=b.require("jquery.select2");return a.fn.select2.amd=b,c});



/**
 * @license Copyright © 2016 Mateusz Zawartka
 * @version 0.100.77
 * MIT license
 */

;
(function ($, window, document, undefined) {
  var hasTouch = 'ontouchstart' in document;

  /**
   * Add a dot at the beginning of a string
   * @returns {string}
   */
  String.prototype.dot = function () {
    return '.' + this;
  };

  /**
   * For each chunk prepend the current string
   * @param chunk
   * @param knife
   * @param innerGlue
   * @param outerGlue
   * @returns {string}
   */
  String.prototype.eachHas = function (chunk, knife, innerGlue, outerGlue) {
    var subject   = this,
        opt       = [],
        knife     = knife || ', ',
        innerGlue = innerGlue || ' ',
        outerGlue = outerGlue || knife,
        chunks    = chunk.split(knife);

    chunks.forEach(function (chunk, c) {
      opt.push(subject + innerGlue + chunk);
    });

    return opt.join(outerGlue);
  };

  /**
   * Pad a string with a specified value, till a min length has been reached
   * @param val
   * @param minLength
   * @returns {String}
   */
  String.prototype.padLength = function (val, minLength) {
    var subject = this;
    while (subject.length < minLength) {
      subject = val + subject;
    }
    return subject;
  };

  /**
   * Join a sibling string by a delimiter
   * @param sibling
   * @param delimiter
   * @returns {string}
   */
  String.prototype.join = function (sibling, delimiter) {
    var delimiter = typeof delimiter === 'string' ? delimiter : " ";
    return this + delimiter + sibling;
  };

  Function.prototype.setName = function (name) {
    Object.defineProperty(this, 'name', {
      get: function () {
        return name;
      }
    });
    return this;
  };

  Function.prototype.clone = function () {
    var newfun = new Function('return ' + this.toString())();
    for (var key in this)
      newfun[key] = this[key];
    return newfun;
  };


  /**
   * Detect CSS pointer-events property
   * events are normally disabled on the dragging element to avoid conflicts
   * https://github.com/ausi/Feature-detection-technique-for-pointer-events/blob/master/modernizr-pointerevents.js
   */
  var hasPointerEvents = (function () {
    var el    = document.createElement('div'),
        docEl = document.documentElement;
    if (!('pointerEvents' in el.style)) {
      return false;
    }
    el.style.pointerEvents = 'auto';
    el.style.pointerEvents = 'x';
    docEl.appendChild(el);
    var supports = window.getComputedStyle && window.getComputedStyle(el, '').pointerEvents === 'auto';
    docEl.removeChild(el);
    return !!supports;
  })();

  /**
   * @version-control +0.1.0 slide animation duration option, default is 0
   * @version-control +0.0.1 max depth default set to 20
   * @dev-since 0.13.29
   * @version-control +0.1.0 option endItemEditBtnClass
   * @version-control +0.1.0 option itemAddBtnClass
   * @version-control +0.1.0 option refuseConfirmDelay (ms), default is 2000ms
   * @version-control +0.1.0 option addBtnSelector
   * @dev-since 0.48.53
   * @version-control +0.5.0 enhancement setup expandBtnHTML, collapseBtnHTML and editBtnHTML in your HTML markup #21
   * @version-control +0.1.0 option expandBtnClass
   * @version-control +0.1.0 option collapseBtnClass
   * @version-control +0.1.0 option event
   * @version-control +0.5.0 deprecated option onItemExpand
   * @version-control +0.5.0 deprecated option onItemCollapse
   * @version-control +0.1.0 option onItemExpanded
   * @version-control +0.1.0 option onItemCollapsed
   * @version-control +0.1.0 option paramsDataKey
   * @version-control +0.0.0 fix commenting typos
   * @dev-since 0.87.53
   * @version-control +0.1.0 deprecated option group (see option allowListMerging)
   * @version-control +0.1.0 option onItemMaxDepth
   * @version-control +0.1.0 option onItemSetParent
   * @version-control +0.1.0 option onItemUnsetParent
   */
  var defaults = {
    listNodeName:           'ol',
    itemNodeName:           'li',
    rootClass:              'dd',
    listClass:              'dd-list',
    itemClass:              'dd-item',
    itemBlueprintClass:     'dd-item-blueprint',
    dragClass:              'dd-dragel',
    handleClass:            'dd-handle',
    collapsedClass:         'dd-collapsed',
    placeClass:             'dd-placeholder',
    noDragClass:            'dd-nodrag', // Items with this class will be undraggable
    emptyClass:             'dd-empty',
    contentClass:           'dd3-content',
    itemAddBtnClass:        'item-add',
    removeBtnClass:         'item-remove',
    itemRemoveBtnConfirmClass: 'confirm-class',
    addBtnSelector:         '', // Provide a global selector for an add button
    addBtnClass:            'dd-new-item',
    editBoxClass:           'dd-edit-box',
    inputSelector:          'input, select, textarea', // Selects input fields to serialize to JSON
    collapseBtnClass:       'collapse',
    expandBtnClass:         'expand',
    endEditBtnClass:        'end-edit',
    itemBtnContainerClass:  'dd-button-container',
    itemNameClass:          'item-name',
    data:                   '', // JSON data to build an instance from (don't forget to call parseJson)
    allowListMerging:       false,   // Accept incoming items from foreign lists e.g:
                                    // true – accept all
                                    // false – deny all
                                    // ['domenu-2'] – accept from instances matching #domenu-2
    select2:                {

      support:     false, // Enable Select2 support
      selectWidth: '45%', // Any CSS-supported value is valid
      params:      {}     // Provide Select2 params
    },
    slideAnimationDuration: 0,
    maxDepth:               5,    // Item nesting limit
    threshold:              15,   // Dragging sensitivity
    refuseConfirmDelay:     2000, // Time (in ms) to wait on confirmation of an item removal
    newItemFadeIn:          350,  // Set 0 for no fadeIn effect
    event:                  {
      onToJson:           [],
      onParseJson:        [],
      onSaveEditBoxInput: [],
      onItemDrag:         [],
      onItemAddChildItem: [],
      onItemDrop:         [],
      onItemAdded:        [],
      onItemExpanded:     [],
      onItemCollapsed:    [],
      onItemRemoved:      [],
      onItemStartEdit:    [],
      onItemEndEdit:      [],
      onCreateItem:       [],
      onItemMaxDepth:     [],
      onItemSetParent:    [],
      onItemUnsetParent:  []
    },
    paramsDataKey:          '__domenu_params' // The property under which internal settings will be serialized
  };

  /**
   * @dev-since 0.48.53
   * @version-control +0.0.0 prevent event overlapping with deep clone
   * @param element
   * @param options
   * @constructor
   */
  function Plugin(element, options) {
    // After $(...).domenu() is called 1:
    this.w = $(document);
    this.$instance = $(element);
    this.options = $.extend(true, {}, defaults, options);
    // 2:
    this.init();
  }

  Plugin.prototype = {

    init:                             function () {
      // Plugin {w: m.fn.init[1], $instance: m.fn.init[1], options: Object, mouse: Object, isTouch: false…}
      var plugin = this,
          opt    = this.options;

      plugin.reset();

      plugin.$placeholder = $('<div class="' + plugin.options.placeClass + '"/>');

      // forEach itemNodeName=li element
      $.each(this.$instance.find(plugin.options.itemNodeName), function (k, el) {
        // pass the li element
        // If an element is a parent then it contains another li elements
        // and can be collapsed and expanded
        plugin.setParent($(el));
      });

      plugin.$instance.on('click', 'button', function (e) {
        // Don't do anything when dragging
        if (plugin.$dragItem) {
          return;
        }
        var target = $(e.currentTarget),
            action = target.data('action'),
            item   = target.parent(plugin.options.itemNodeName);
        // Some internal click handlers communicating through
        // jQuery object data
        if (action === 'collapse') {
          plugin.collapseItem(item);
        }

        if (action === 'expand') {
          plugin.expandItem(item);
        }
      });

      // Declaring some custom event handlers
      var onStartEvent = function (e) {
            var handle = $(e.target);

            // Identify if the object is draggable
            if (!handle.hasClass(plugin.options.handleClass)) {
              if (handle.closest(plugin.options.noDragClass.dot()).length) {
                return;
              }
              handle = handle.closest(plugin.options.handleClass.dot());
            }

            // If the element is not draggable, or is while dragging
            // then don't do anything
            if (!handle.length || plugin.$dragItem) return;

            // Same here making sure if the object can be draggeds
            plugin.isTouch = /^touch/.test(e.type);
            if (plugin.isTouch && e.touches.length !== 1) {
              return;
            }

            // Don't do whatever browsers do by default
            e.preventDefault();
            // At this point object is identified as available to drag
            // so start dragging
            plugin.dragStart(e.touches ? e.touches[0] : e);
          },

          onMoveEvent  = function (e) {
            if (plugin.$dragItem) {
              e.preventDefault();
              plugin.dragMove(e.touches ? e.touches[0] : e);
            }
          },

          onEndEvent   = function (e) {
            if (plugin.$dragItem) {
              e.preventDefault();
              plugin.dragStop(e.touches ? e.touches[0] : e);
            }
          };

      // If thouch events are avialable, start listening for those events
      if (hasTouch) {
        plugin.$instance[0].addEventListener('touchstart', onStartEvent, false);
        window.addEventListener('touchmove', onMoveEvent, false);
        window.addEventListener('touchend', onEndEvent, false);
        window.addEventListener('touchcancel', onEndEvent, false);
      }

      // Start listening for the events below
      plugin.$instance.on('mousedown', onStartEvent);
      // list.w = $(document)
      plugin.w.on('mousemove', onMoveEvent);
      plugin.w.on('mouseup', onEndEvent);

      // @dev-since 0.13.29
      // @version-control +0.1.0 support global add button selector
      if (opt.addBtnSelector) this.addNewListItemListener($(opt.addBtnSelector));
      else this.addNewListItemListener(this.$instance.find(opt.addBtnClass.dot()));
    },
    /**
     * @dev-since 0.13.29
     * @version-control +0.1.0 default add button removed
     * @dev-since 0.48.53
     * @version-control +0.1.0 fix onItemAdded event for addNewListItemListener
     * @version-control +0.5.0 enhancement remember items folding (collapse state)
     * @param addBtn
     * @param parent
     */
    addNewListItemListener:           function (addBtn, parent) {
      var _this = this,
          opt   = this.options;
      addBtn.on('click', function (e) {
        var list = _this.$instance.find(opt.listClass.dot()).first(),
            item = _this.createNewListItem();
        if (!item) return;


        item.css('display', 'none');
        list.prepend(item);
        item.fadeIn(opt.newItemFadeIn);

        // Call item addition event listeners
        _this.options.event.onItemAdded.forEach(function (cb, i) {
          cb($(item), e);
        });
      });
    },
    /**
     * @dev-since 0.13.29
     * @version-control +0.0.5 support end edit on click
     * @param event
     */
    clickEndEditEventHandler:         function (item) {
      var _this      = this,
          opt        = _this.options,
          endEditBtn = item.find(opt.endEditBtnClass.dot()).first();

      endEditBtn.on('click', null, {forced: true}, _this.keypressEnterEndEditEventHandler.bind(_this));
    },
    /**
     * @version-control +0.0.1 lazy keypressEnterEndEditEventHandler binding
     * @version-control +0.0.1 prevent slide animation bubbling
     * @version-control +0.0.2 slide animation duration support
     */
    clickStartEditEventHandler:       function (event) {
      var opt          = this.options,
          _this        = this,
          item         = $(event.target).parents(opt.itemClass.dot()).first(),
          spn          = item.find(opt.itemNameClass.dot()).first(),
          firstInput   = item.find(opt.inputSelector).first(),
          btnContainer = item.find(opt.itemBtnContainerClass.dot()).first(),
          edtBox       = item.find(opt.editBoxClass.dot()).first();

      var igniteKeypressEnterEndEditEventHandler = function (el) {
        el.each(function (c, item) {
          var item                             = $(item),
              keypressEnterEndEditEventHandler = _this.keypressEnterEndEditEventHandler;

          if (item.data('domenu_keypressEnterEndEditEventHandler')) return;

          item.data('domenu_keypressEnterEndEditEventHandler', true);

          item.on('keypress', keypressEnterEndEditEventHandler.bind(_this));
        });
      };


      // Setup on click endEdit event listener
      if (item.data('domenu_clickEndEditEventHandler') !== true) {
        _this.clickEndEditEventHandler(item);
        item.data('domenu_clickEndEditEventHandler', true);
      }

      // Hide the span
      spn.stop().hide(opt.slideAnimationDuration, function () {

        // Use either the default title or the user specified title as the value for the input
        if (firstInput.get(0).nodeName !== 'SELECT')
          firstInput.val(spn.text());
        else firstInput.val(firstInput.find('option:contains(' + spn.text() + ')').val());


        // Hide the remove button
        btnContainer.stop().hide(opt.slideAnimationDuration, function () {
          // Show the edit panel
          edtBox.stop().show(opt.slideAnimationDuration, function () {
            edtBox.children().first('input').select().focus();
            // Be ready to close the edit mode
            igniteKeypressEnterEndEditEventHandler(item);
          });
        });
      });

      // Call start edit event listeners
      opt.event.onItemStartEdit.forEach(function (cb, i) {
        cb(item, event);
      });
    },
    /**
     * @version-control +0.1.0 support default value tokens and placeholder tokens
     * @param token
     * @param input
     * @returns {*}
     */
    resolveToken:                     function (token, input) {
      if (typeof token !== "string") return;

      var out       = token,
          tagRegex  = /\{\?[a-z\-\.]+\}/ig,
          tags      = out.match(tagRegex),
          tagsCount = tags && tags.length || 0;

      // As long as there are tags available
      for (var currentTag = 0; currentTag < tagsCount; currentTag++) {

        // Process each tag and replace it it in the output string
        switch (tags[currentTag]) {
          case "{?date.gregorian-slashed-DMY}":
            var dateTime = new Date(Date.now()),
                date     = dateTime.getDay().toString().padLength('0', 2) + '/' +
                  dateTime.getMonth().toString().padLength('0', 2) + '/' +
                  dateTime.getFullYear();

            out = out.replace(tags[currentTag], date);
            break;

          case "{?date.mysql-datetime}":
            var date = new Date(Date.now());
            date = date.getUTCFullYear() + '-' +
              ('00' + (date.getUTCMonth() + 1)).slice(-2) + '-' +
              ('00' + date.getUTCDate()).slice(-2) + ' ' +
              ('00' + date.getUTCHours()).slice(-2) + ':' +
              ('00' + date.getUTCMinutes()).slice(-2) + ':' +
              ('00' + date.getUTCSeconds()).slice(-2);
            out = out.replace(tags[currentTag], date);
            break;

          case "{?numeric.increment}":
            // We begin with 1 - evaluate to true on check..
            this.incrementIncrement = this.incrementIncrement || 1;
            out = out.replace(tags[currentTag], this.incrementIncrement);
            this.incrementIncrement += 1;
            break;

          case "{?value}":
            out = out.replace(tags[currentTag], input.value);
            break;

          default:
            out = token;
            break;
        }
      }

      return out;
    },
    /**
     * @version-control +0.0.1 shared way to save input state
     * @version-control +0.0.5 tokens support
     * @param inputCollection jQuery Selection
     */
    saveEditBoxInput:                 function (inputCollection) {
      var _this = this,
          opt   = this.options,
          $item;

      inputCollection.each(function (c, input) {
        var itemDataValue     = $(input).parents(opt.itemClass.dot().join(',').join(opt.itemBlueprintClass.dot())).first().data(input.getAttribute('name')),
            inputDefaultValue = $(input).data('default-value') || '';
        $item = $(input).parents(opt.itemClass.dot()).first();
        if (!(itemDataValue || input.value)) var tokenizedDefault = _this.resolveToken(inputDefaultValue, $(input));
        $item.data(input.getAttribute('name'), $(input).val() || itemDataValue || tokenizedDefault);
      });

      // Call on save edit box event listeners
      opt.event.onSaveEditBoxInput.forEach(function (cb, i) {
        cb($item, inputCollection);
      });
    },
    /**
     * @version-control +0.1.0 dynamic inputs
     * @version-control +0.0.1 prevent slide bubbling
     * @version-control +0.0.2 slide animation duration support
     * @dev-since 0.13.29
     * @version-control +0.0.1 removeBtn first
     * @version-control +0.0.2 support add button
     * @param event
     */
    keypressEnterEndEditEventHandler: function (event) {
      var _this           = this,
          opt             = this.options,
          item            = $(event.target).parents(opt.itemClass.dot()).first(),
          edtBox          = item.find(opt.editBoxClass.dot()).first(),
          inputCollection = item.find(opt.inputSelector),
          spn             = item.find('span').first(),
          btnContainer    = item.find(opt.itemBtnContainerClass.dot()).first();

      // Listen only to the Enter key, unless you'll forced otherwise
      if (event.keyCode !== 13 && !(event.data && event.data.forced && event.data.forced === true)) return;

      // Set title
      _this.determineAndSetItemTitle(item);

      // Don't leave empty strings
      if (spn.text() === '') spn.text(_this.determineAndSetItemTitle(item));

      // Hide the edit box
      edtBox.stop().slideUp(opt.slideAnimationDuration, function () {

        // Save inputs
        _this.saveEditBoxInput(inputCollection);

        // Show the button container
        btnContainer.attr('style', '');

        // Call end edit event listeners
        opt.event.onItemEndEdit.forEach(function (cb, i) {
          cb($(item), event);
        });

        // Show the span content
        spn.stop().slideDown(opt.slideAnimationDuration);
      });


    },
    resolveInputDataEntryByName:      function (name) {
      var item = this.$instance
      opt = this.options,

        item.find(opt.editBoxClass.dot().join(opt.inputSelector)).each(function (i, input) {
          if (input.getAttribute('name') === name) return $(input).data('name');
        })
    },
    setItemTitle:                     function (item, title) {
      var _this = this,
          opt   = this.options;
      item.find(opt.contentClass.dot().join('span')).first().text(title);
    },
    determineAndSetItemTitle:         function (item) {
      var _this                                 = this,
          opt                                   = this.options,
          firstInput                            = item.find(opt.inputSelector).first(),
          firstInputText                        = firstInput.find('option:selected').first().text() || firstInput.text(),
          firstInputValue                       = item.find(opt.editBoxClass.dot().eachHas(opt.inputSelector)).first().val(),
          itemDataValue                         = item.data(item.find(opt.inputSelector).first().attr('name')),
          firstEditBoxInputPlaceholderValue     = item.find(opt.editBoxClass.dot().eachHas(opt.inputSelector)).first().attr('placeholder'),
          firstEditBoxInputDataPlaceholderValue = item.find(opt.editBoxClass.dot().eachHas(opt.inputSelector)).first().data('placeholder'),
          choice                                = firstInputText || firstInputValue || itemDataValue || _this.resolveToken(firstEditBoxInputDataPlaceholderValue) || firstEditBoxInputPlaceholderValue;

      item.find(opt.contentClass.dot().join('span')).first().text(choice);
    },
    /**
     * @version-control +0.0.4 fix fill inputs with placeholders #3
     * @version-control +0.1.0 fix populate inputs with values whenever possible #5
     * @dev-since 0.24.53
     * @version-control +0.5.0 feature create missing options
     * @param item
     * @param inputCollection
     */
    setInputCollectionPlaceholders:   function (item, inputCollection) {
      var _this = this;
      $(inputCollection).each(function (c, input) {
        if (input.nodeName === 'SELECT') {
          $(input).find('option[selected="selected"]').removeAttr('selected');
          var selectedOption = $(input).find('option[value="' + item.data($(input).attr('name')) + '"]');
          if (selectedOption.length !== 0) selectedOption.attr('selected', 'selected');
          else if (item.data($(input).attr('name'))) $(input).append('<option value="' + item.data($(input).attr('name')) + '">' + item.data($(input).attr('name')) + '</option>');
          else return;
        }
        // Set the placeholder value of the input
        $(input).attr('placeholder', _this.resolveToken($(input).data('placeholder'), $(input)) || $(input).attr('placeholder'));
        // And set the value of the input
        $(input).val(item.data($(input).attr('name')));
      });
    },
    /**
     * @version-control +0.0.5 support dynamic inputs
     * @version-control +0.0.5 support tokenization
     * @version-control +0.0.2 support dyanmic titles
     * @dev-since 0.13.29
     * @version-control +0.1.0 feature confirm item deletion
     * @version-control +0.1.0 feature add a child item
     * @version-control +0.0.1 support itemAddChildItem onItemAdded events
     * @dev-since 0.48.53
     * @version-control +0.5.0 feature mixing instances items (data) together
     * @param data
     * @returns {*}
     */
    createNewListItem:                function (data) {
      var _this           = this,
          el              = this.$instance,
          opt             = this.options,
          blueprint       = el.find(opt.itemBlueprintClass.dot()).first().clone(),
          inputCollection = blueprint.find(opt.editBoxClass.dot()).find(opt.inputSelector);

      /**
       * @dev-since 0.13.29
       * @version-control +0.1.0 fix ghost parent elements
       * @dev-since 0.24.53
       * @version-control +0.1.0 fix onItemRemoved event listener
       * @dev-since 0.99.77
       * @version-control +0.1.0 feature added id as second argument to the callback
       */
      blueprint.remove = function () {
        var parent = blueprint.parents(_this.options.itemClass.dot()).first();
        var id = blueprint.data("id");

        jQuery(this).remove();
        _this.unsetEmptyParent(parent);
        jQuery.each(opt.event.onItemRemoved, function (i, cb) {
          cb(blueprint, id);
        });
      };

      blueprint.setParameter = function (key, value) {
        blueprint.data(opt.paramsDataKey, $.extend(true, blueprint.data(opt.paramsDataKey), {key: value}));
      };

      blueprint.getParameter = function (key) {
        return blueprint.data(key);
      };

      // Use user supplied JSON data to fill the data fields
      $.each(data || {}, function (key, value) {
        blueprint.data(key, value);
      });


      /**
       * @dev-since 0.87.53
       * @version-control +0.0.5 fix item id #19
       */
      blueprint.data('id', blueprint.data('id') || _this.getHighestId() + 1);

      // Set the item-class
      /*
       * @dev-since 0.48.53
       * @version-control +0.1.0 feature inherit blueprint's HTML user-set classes #21
       */
      var currentBlueprintClass = blueprint.attr('class'),
          blueprintClass        = opt.itemClass + currentBlueprintClass.replace(opt.itemBlueprintClass, '');
      blueprint.attr('class', blueprintClass);

      // Set intial input values (needed on deserialization)
      this.setInputCollectionPlaceholders(blueprint, inputCollection);

      // Save input state
      this.saveEditBoxInput(inputCollection);

      // Set title
      this.determineAndSetItemTitle(blueprint);

      // Parse tokens etc..
      this.setInputCollectionPlaceholders(inputCollection);

      // Set the remove button click event handler
      blueprint.find(opt.removeBtnClass.dot()).first().on('click', function (e) {
        var rmvBtn       = $(this),
            confirmClass = rmvBtn.data(opt.itemRemoveBtnConfirmClass);

        // When there is a confirmation class...
        if (confirmClass) {

          // And that class has been already applied to the item, then just remove the item
          if (rmvBtn.hasClass(confirmClass)) blueprint.remove();

          // If the confirmation class hasn't been yet applied to the item, then apply the class...
          else {
            rmvBtn.addClass(confirmClass);

            // but only for a limited amount of time
            var revertAddClass = setTimeout(function () {
              rmvBtn.removeClass(confirmClass);
            }, opt.refuseConfirmDelay);
          }

          // When there is no confirmation class just remove the item
        } else {
          blueprint.remove();

          // Call item remove event listeners
          opt.event.onItemRemoved.forEach(function (cb, i) {
            cb(blueprint, e);
          });
        }
      });

      // Set the add button click event handler
      blueprint.find(opt.itemAddBtnClass.dot()).first().on('click', function (event) {
        _this.itemAddChildItem(blueprint);

        // Call item addition event listeners
        opt.event.onItemAdded.forEach(function (cb, i) {
          cb(blueprint, event);
        });

        // Call item add child item event listeners
        opt.event.onItemAddChildItem.forEach(function (cb, i) {
          cb(blueprint, event);
        });
      });

      // Setup editing; on every mouse click clickStartEditEventHandler will be called
      blueprint.find('span').first().get(0).addEventListener('click', _this.clickStartEditEventHandler.bind(this));

      if (_this.options.select2.support) {
        blueprint.find('select').css('width', _this.options.select2.selectWidth);
        blueprint.find('select').select2(_this.options.select2.params);
      }

      blueprint.data(opt.paramsDataKey, blueprint.data(opt.paramsDataKey) || {});

      // Call onCreateItem event listeners
      opt.event.onCreateItem.forEach(function (cb, i) {
        var callbackResponse = cb(blueprint, blueprint.data());
        blueprint = typeof  callbackResponse === "undefined" ? blueprint : callbackResponse;
      });

      // Give back a ready itemClass element
      return blueprint;
    },
    /**
     * @dev-since 0.87.53
     * @version-control +0.0.1 fix max depth item add child item
     * @version-control +0.0.3 fix stuck last child item
     */
    itemAddChildItem:                 function ($parentElement) {
      var _this    = this,
          opt      = _this.options,
          listElement,
          $newItem = _this.createNewListItem();

      if (!$newItem) return;
      else if ($parentElement.parents(opt.listClass.dot()).length > opt.maxDepth) {
        var $addButton = $parentElement.find(opt.itemAddBtnClass.dot());
        $addButton.addClass(opt.removeBtnClass);

        setTimeout(function() {
          $addButton.removeClass(opt.removeBtnClass);
        }, opt.refuseConfirmDelay);

        opt.event.onItemMaxDepth.forEach(function (cb, i) {
          cb();
        });
        return;
      }

      if ($parentElement.children(opt.listClass.dot()).length) $parentElement.children(opt.listClass.dot()).first().append($newItem);
      else {
        listElement = $('<' + opt.listNodeName + '/>').addClass(opt.listClass);
        listElement.append($newItem);
        $parentElement.append(listElement);
      }
      _this.setParent($parentElement);
    },
    getHighestId:                     function () {
      var opt = this.options,
          el  = this.$instance,
          id  = 0;

      el.find(opt.itemNodeName).each(function (i, e) {
        var eId = $(e).data('id');
        if (eId > id) return id = eId;
      });

      return id;
    },
    /**
     * @version-control +0.0.2 itemClass li prefix support
     * @returns {*}
     */
    serialize:                        function () {
      // Call toJson event listeners
      this.options.event.onToJson.forEach(function (cb, i) {
        cb();
      });

      var data,
          depth = 0,
          list  = this;
      step = function (level, depth) {
        var array = [],
            items = level.children(list.options.itemNodeName);
        items.each(function () {
          var li           = $(this),
              sub          = li.children(list.options.listNodeName),
              filteredData = {};

          // Filter out domenu_ prefixed data values
          $.each(li.data(), function (key, i) {

            // Skip when the prefix is present
            if (key.indexOf('domenu_') === 0) return;

            // Include the value if not skipped
            filteredData[key] = li.data(key);
          });

          var item = $.extend({}, filteredData);

          if (sub.length) {
            item.children = step(sub, depth + 1);
          }

          array.push(item);
        });
        return array;
      };
      data = step(list.$instance.find(list.options.listNodeName).first(), depth);
      return data;
    },
    deserialize:                      function (data, override) {
      var data  = JSON.parse(data) || JSON.parse(this.options.data),
          _this = this,
          opt   = this.options,
          list  = _this.$instance.find(opt.listClass.dot()).first();

      if (override) list.children().remove();

      var processItem = function (i, pref) {
        if (i.children) {
          var cref = $('<ol class="' + opt.listClass + '"></ol>'),
              item = _this.createNewListItem(i);

          if (!item) return;

          pref.append(item);
          item.append(cref);
          _this.setParent(item, true);
          jQuery.each(i.children, function (i, e) {
            processItem(e, cref);
          })
        } else {
          var item = _this.createNewListItem(i);

          if (!item) return;

          pref.append(item);
        }
      }

      jQuery.each(data, function (i, e) {
        processItem(e, list);
      })

      _this.$instance.find(_this.options.itemClass.dot()).each(function (i, item) {
        if ($(item).data(_this.options.paramsDataKey).collapsed) _this.collapseItem($(item));
      });

      // Call start edit event listeners
      this.options.event.onParseJson.forEach(function (cb, i) {
        cb();
      });
    },
    serialise:                        function () {
      return this.serialize();
    },

    reset: function () {
      this.mouse = {
        offsetX:                0,
        offsetY:                0,
        startX:                 0,
        startY:                 0,
        lastX:                  0,
        lastY:                  0,
        nowX:                   0,
        nowY:                   0,
        lastCurrentDistXChange: 0,
        lastCurrentDistYChange: 0,
        isMovingOnXAxis:        null,
        dirX:                   0,
        dirY:                   0,
        lastDirX:               0,
        lastDirY:               0,
        distAxX:                0,
        distAxY:                0,
        distXtotal:             0,
        distYtotal:             0
      };
      this.isTouch = false;
      this.moving = false;
      this.$dragItem = null;
      this.dragRootEl = null;
      this.dragDepth = 0;
      this.hasNewRoot = false;
      this.$pointEl = null;
    },

    expandItem: function ($item) {
      $item.removeClass(this.options.collapsedClass);
      $item.children(this.options.listClass.dot()).children(this.options.itemClass.dot()).show();
      $item.children(this.options.expandBtnClass.dot()).hide();
      $item.children(this.options.collapseBtnClass.dot()).show();
      $item.data(this.options.paramsDataKey, $.extend(true, $item.data(this.options.paramsDataKey), {collapsed: false}));

      // Call start edit event listeners
      this.options.event.onItemExpanded.forEach(function (cb, i) {
        cb($item);
      });
    },

    collapseItem: function ($item) {
      $item.addClass(this.options.collapsedClass);
      $item.children(this.options.listClass.dot()).children(this.options.itemClass.dot()).hide();
      $item.children(this.options.collapseBtnClass.dot()).hide();
      $item.children(this.options.expandBtnClass.dot()).show();
      $item.data(this.options.paramsDataKey, $.extend(true, $item.data(this.options.paramsDataKey), {collapsed: true}));

      // Call start edit event listeners
      this.options.event.onItemCollapsed.forEach(function (cb, i) {
        cb($item);
      });
    },

    expandAll:                          function (cb) {
      var list            = this,
          recursiveExpand = function ($item) {
            if (!cb || !cb($item)) return;
            list.expandItem($item);
            var listBag = $item.children(list.options.listNodeName);
            if (listBag.length) {
              jQuery.each(listBag, function (i, item) {
                recursiveExpand($(item));
              });
            }
          };

      list.$instance.find(this.options.collapsedClass.dot()).each(function (e, item) {
        recursiveExpand($(item));
      });
    },
    /**
     * @version-control +0.0.1 collapse all fix
     * @param cb
     */
    collapseAll:                        function (cb) {
      var list              = this,
          recursiveCollapse = function ($item) {
            if (!cb || !cb($item)) return;
            var listBag = $item.children(list.options.listNodeName);
            if (listBag.length) {
              list.collapseItem($item);
              jQuery.each(listBag, function (i, item) {
                recursiveCollapse($(item));
              });
            }
          };

      list.$instance.find(list.options.listNodeName).children(list.options.itemClass.dot()).each(function (e, item) {
        recursiveCollapse($(item));
      });
    },
    /**
     * @dev-since 0.13.29
     * @version-control +0.0.5 prevent setting multiple parents on a parent element
     * @param li
     * @param force
     */
    setParent:                          function ($item, force) {
      var opt = this.options;
      // If the specified selector targets any element
      if ($item.children(this.options.listNodeName).length || force) {
        // LI STRUCTURE
        // <li class="dd-item dd3-item" data-id="15">
        //  <button data-action="collapse" type="button">Collapse</button>
        //  <button data-action="expand" type="button" style="display: none;">Expand</button>
        //     <div class="dd-handle dd3-handle">Drag</div><div class="dd3-content">Item 15</div>
        //     <ol class="dd-list">
        //         <li class="dd-item dd3-item" data-id="16">
        //             <div class="dd-handle dd3-handle">Drag</div><div class="dd3-content">Item 16</div>
        //         </li>
        //         <li class="dd-item dd3-item" data-id="17">
        //             <div class="dd-handle dd3-handle">Drag</div><div class="dd3-content">Item 17</div>
        //         </li>
        //         <li class="dd-item dd3-item" data-id="18">
        //             <div class="dd-handle dd3-handle">Drag</div><div class="dd3-content">Item 18</div>
        //         </li>
        //     </ol>
        // </li>
        $item.children('[data-action="collapse"]').show();
        // make sure handle is the first element
        var handle = $item.find(this.options.handleClass.dot()).first().clone();
        $item.find(this.options.handleClass.dot()).first().remove();
        $item.prepend(handle);
      }
      // If the selector gets targeted within the li element
      // hide it
      $item.children('[data-action="expand"]').hide();

      // Call start edit event listeners
      opt.event.onItemSetParent.forEach(function (cb, i) {
        cb($item);
      });
    },
    /**
     * @dev-since 0.13.29
     * @version-control +0.1.0 fix clean item data when unsetting a parent #4
     * @dev-since 0.48.53
     * @version-control +0.1.0 fix disappearing lists on unsetParent with multiple list instances
     * @param $item
     */
    unsetParent:                        function ($item) {
      var opt = this.options;

      $item.removeClass(this.options.collapsedClass);
      // Clear collapse/expand controls from the parent
      $item.children('[data-action]').hide();
      $item.children(this.options.listNodeName).remove();
      $item.removeData('children');

      // Call start edit event listeners
      opt.event.onItemUnsetParent.forEach(function (cb, i) {
        cb($item, event);
      });
    },
    /**
     * @dev-since 0.13.29
     * @version-control +0.0.5 unsetEmptyParent
     * @param parent
     */
    unsetEmptyParent:                   function (parent) {
      var _this = this;
      if (parent.find(this.options.itemClass.dot()).length === 0) _this.unsetParent(parent);
    },
    // How many list items does an element have?
    getChildrenCount:                   function ($placeholder) {
      return $placeholder.parents(this.options.listClass.dot()).length + this.$dragItem.find(this.options.listClass.dot()).length - 1;
    },
    updatePlaceholderMaxDepthApperance: function () {
      if (this.getChildrenCount(this.$placeholder) >= this.options.maxDepth) {
        this.$placeholder.addClass('max-depth');
      } else {
        this.$placeholder.removeClass('max-depth');
      }
    },
    dragStart:                          function (e) {
      var mouse    = this.mouse,
          opt      = this.options,
          target   = $(e.target),
          dragItem = target.closest(this.options.itemNodeName);

      /**
       * @dev-since 0.48.53
       * @version-control +0.2.0 enhancement adding noDragClass to an item makes it undraggable
       */
      if (dragItem.attr('class').match(opt.noDragClass)) return;

      this.$placeholder.css('height', dragItem.height());

      mouse.offsetX = e.offsetX !== undefined ? e.offsetX : e.pageX - target.offset().left;
      mouse.offsetY = e.offsetY !== undefined ? e.offsetY : e.pageY - target.offset().top;
      mouse.startX = mouse.lastX = e.pageX;
      mouse.startY = mouse.lastY = e.pageY;

      this.dragRootEl = this.$instance;

      // Define the state as dragging so no other elements get attached due
      // to the identification process in init onStartDrag
      this.$dragItem = $(document.createElement(this.options.listNodeName))
      .addClass(this.options.listClass + ' ' + this.options.dragClass);
      this.$dragItem.css('width', dragItem.width());

      // this.$placeholder -> $('<div class="' + list.options.placeClass + '"/>');
      // Put the targeted element into the $dragItem which will work as a kind of a bag
      // while dragging
      dragItem.after(this.$placeholder);
      dragItem[0].parentNode.removeChild(dragItem[0]);
      dragItem.appendTo(this.$dragItem);

      $(document.body).append(this.$dragItem);
      // Adjust the dragging bag ($dragItem) initial position within the
      // element
      this.$dragItem.css({
        'left': e.pageX - mouse.offsetX,
        'top':  e.pageY - mouse.offsetY
      });

      this.updatePlaceholderMaxDepthApperance();

      // Call start drag event listeners
      this.options.event.onItemDrag.forEach(function (cb, i) {
        cb($(dragItem), e);
      });
    },
    dragStop:                           function (e) {
      var el    = this.$dragItem.children(this.options.itemNodeName).first(),
          _this = this;

      el[0].parentNode.removeChild(el[0]);
      this.$placeholder.replaceWith(el);

      this.$dragItem.remove();
      this.$instance.trigger('change');
      if (this.hasNewRoot) {
        this.dragRootEl.trigger('change');
      }
      this.reset();

      this.mouse.distXtotal = 0;
      this.mouse.distYtotal = 0;

      // Call end drag event listeners
      this.options.event.onItemDrop.forEach(function (cb, i) {
        cb($(el), e);
      });

      if ($(el).parents(this.options.rootClass).data('domenu-id') !== $(this.$instance).data('domenu-id')) {
        $(el).parents(this.options.rootClass.dot()).domenu()._plugin.options.event.onItemDrop.forEach(function (cb, i) {
          cb(el, e);
        });
      }
    },


    /**
     * @dev-since 0.24.53
     * @version-control +0.10.0 enchancement of item dragging/repositioning
     * @version-control +0.3.0  fix unsetting parents
     */
    dragMove: function (e) {
      var list, parent, prev, next, depth, $rootListOfPointingElement, hasRootChanged,
          isEmpty = false,
          opt     = this.options,
          mouse   = this.mouse;

      /**
       * @dev-since 0.87.53
       * @version-control +0.0.5 fix ghost first movement
       * @type {number|Number}
       */
      // mouse position last events
      mouse.lastX = mouse.nowX || e.pageX;
      mouse.lastY = mouse.nowY || e.pageY;

      // mouse position this events
      mouse.nowX = e.pageX;
      mouse.nowY = e.pageY;

      // distance mouse moved between events
      mouse.lastCurrentDistXChange = mouse.nowX - mouse.lastX;
      mouse.lastCurrentDistYChange = mouse.nowY - mouse.lastY;

      // set the direction mouse was moving for future events
      mouse.lastDirX = mouse.dirX;
      mouse.lastDirY = mouse.dirY;

      // direction mouse is now moving (on both axis)
      // 0 for no direction, 1 for right -1 for left
      mouse.dirX = mouse.lastCurrentDistXChange === 0 ? 0 : mouse.lastCurrentDistXChange > 0 ? 1 : -1;
      mouse.dirY = mouse.lastCurrentDistYChange === 0 ? 0 : mouse.lastCurrentDistYChange > 0 ? 1 : -1;

      /**
       * @dev-since 0.87.53
       * @version-control 0.0.5 fix telepathic child dragging
       * @type {number}
       */
      // placeELSP – placeholder pixel strand, how far removed is the $dragItem from placeEL in pixels?
      // placeELSEF – placeholder elastic strand factor, how far removed is the $dragItem from placeEL in elastic units?
      var placeElSPY = Math.abs(this.$placeholder.offset().top - this.$dragItem.offset().top),
          placeElSPX = Math.abs(this.$placeholder.offset().left - this.$dragItem.offset().left),
          placeElSEF = (2 / Math.PI) * Math.atan((Math.PI / 2) * (placeElSPY + placeElSPX) * 0.1 / opt.threshold);

      // Placeholder will be dragged around, the member list will actually
      // hide itself and replace the placeholder on dragStop
      this.$dragItem.css({
        // Place element on the document following the mouse
        // position change
        //
        // e.pageX position of the mouse relative to the whole page
        // e.offsetX position of the mouse relative to .dd3-handle
        // mouse absolute position - the position offset in the element =
        // = begin offset of the element
        'left': e.pageX - mouse.offsetX,
        'top':  e.pageY - mouse.offsetY
      });

      this.$pointEl = $(document.elementFromPoint(e.pageX - document.body.scrollLeft, e.pageY - (window.pageYOffset || document.documentElement.scrollTop)));

      // find parent list of item under cursor
      $rootListOfPointingElement = this.$pointEl.closest(opt.rootClass.dot());
      hasRootChanged = this.dragRootEl.data('domenu-id') !== $rootListOfPointingElement.data('domenu-id');

      if ($rootListOfPointingElement.length && !hasRootChanged) {
        this.$placeholder.css({
          'opacity': 1
        });
      } else {
        this.$placeholder.css({
          // fade out the placeholder as the distance of the cursor and placeholder increases
          'opacity': 1 - placeElSEF
        });
      }

      // do nothing when the root list is not found and the mouse is removed far away from the placeholder
      if ($rootListOfPointingElement.length === 0 && placeElSEF > 0.4) return;

      // axis mouse is moving on: 1 for x-axis, 0 for y-axis
      var isMovingOnXAxis = Math.abs(mouse.lastCurrentDistXChange) > Math.abs(mouse.lastCurrentDistYChange) &&
      // the difference of covered distance between both axis must be at least 2px for isMovingOnXAxis to change
      Math.abs(mouse.lastCurrentDistXChange - mouse.lastCurrentDistYChange) > 2 ? true : false;

      // intialize variables on first move event
      if (mouse.moving === false) {
        mouse.isMovingOnXAxis = isMovingOnXAxis;
        mouse.moving = true;
      }

      function setTotalDistance(x, y) {
        mouse.distXtotal = x;
        mouse.distYtotal = y;

        if (x == 0) mouse.lastX = mouse.startX = mouse.nowX;
        if (y == 0) mouse.lastY = mouse.startY = mouse.nowY;
      }

      setTotalDistance(mouse.nowX - mouse.startX, mouse.nowY - mouse.startY);
      mouse.isMovingOnXAxis = isMovingOnXAxis;

      this.updatePlaceholderMaxDepthApperance();

      if (this.$pointEl.parents(opt.rootClass.dot()).length === 0) setTotalDistance(0, 0);

      /**
       * move horizontal only to right
       */
      if (Math.abs(mouse.distXtotal) >= opt.threshold) {
        // reset move distance on x-axis for new phase
        // this.$placeholder placeholder element
        var $precedingSiblingItem = this.$placeholder.prev(opt.itemNodeName);
        var $precedingSiblingItemList = $precedingSiblingItem.find(opt.listNodeName).last();

        // Handle moving to right
        if (mouse.distXtotal > 0 && mouse.dirX === 1 && $precedingSiblingItem.length > 0 && !$precedingSiblingItem.hasClass(opt.collapsedClass)) {
          // check if depth limit has reached
          if (this.getChildrenCount(this.$placeholder) < opt.maxDepth) {
            if ($precedingSiblingItemList.length > 0) {
              var $lastItem = $precedingSiblingItem.children(opt.listNodeName).last();
              $lastItem.append(this.$placeholder);
              setTotalDistance(0, 0);
            } else {
              var $list = $(document.createElement((opt.listNodeName))).addClass(opt.listClass);
              $list.append(this.$placeholder);
              $precedingSiblingItem.append($list);
              this.setParent($precedingSiblingItem);
              setTotalDistance(0, 0);
            }
          } else if (this.getChildrenCount(this.$placeholder) >= opt.maxDepth) {
            this.updatePlaceholderMaxDepthApperance();
            opt.event.onItemMaxDepth.forEach(function (cb, i) {
              cb($precedingSiblingItem);
            });
          }
        } else if (mouse.distXtotal < 0 && mouse.dirX === -1) {
          var $parent = this.$placeholder.parents(opt.itemClass.dot()).first();
          if ($parent.length) {
            $parent.after(this.$placeholder);
            if ($parent.children(opt.itemClass.dot()).length === 0) this.unsetEmptyParent($parent);
            setTotalDistance(0, 0);
          }
        }
      }

      // find list item under cursor
      if (!hasPointerEvents) {
        this.$dragItem[0].style.visibility = 'hidden';
      }


      /**
       * @dev-since 0.87.53
       * @version-control +0.0.5 fix disappearing list when mixing items from multiple instances
       */
      if (!this.$instance.children(this.options.listClass.dot()).length) {
        this.$instance.append($('<' + this.options.listNodeName + '/>').attr('class', this.options.listClass));
      }

      /**
       * @dev-since 0.87.53
       * @version-control +0.1.0 feature restrict list merging
       */
      if (this.options.allowListMerging !== true) {
        if (hasRootChanged && this.options.allowListMerging === false) return;
        else if (hasRootChanged && $rootListOfPointingElement.data('domenu') && $rootListOfPointingElement.data('domenu').options.allowListMerging.indexOf(this.$instance.attr('id')) === -1) return;
      }
      /**
       * @dev-since 0.48.59
       * @version-control +0.1.0 fix snapping items to an empty list  (multiple instances)
       */
      if (this.$pointEl.hasClass(opt.listClass) && !this.$pointEl.children(opt.itemClass.dot()).length) this.$pointEl.append(this.$placeholder);

      if (!this.$pointEl.parents(opt.rootClass.dot()).length || this.$pointEl.hasClass(opt.listClass) || this.$pointEl.hasClass(opt.placeClass)) return;

      if (!this.$pointEl.hasClass(opt.itemClass)) this.$pointEl = $(this.$pointEl).parents(opt.itemClass.dot()).first();

      if (!hasPointerEvents) {
        this.$dragItem[0].style.visibility = 'visible';
      }
      if (this.$pointEl.hasClass(opt.handleClass)) {
        this.$pointEl = this.$pointEl.parent(opt.itemNodeName);
      }
      // When no pointer element has been found or when the pointer element has no options.itemClass
      else if (!this.$pointEl.length || !this.$pointEl.hasClass(opt.itemClass)) {
        return;
      }


      /**
       * move vertical
       */

      if (mouse.isMovingOnXAxis === false && Math.abs(mouse.distYtotal) >= 5) {
        // check if groups match if dragging over new root
        if (hasRootChanged && opt.allowListMerging === false) {
          return;
        } else if (hasRootChanged && typeof opt.allowListMerging === "object") {
          if(opt.allowListMerging.indexOf($rootListOfPointingElement.attr('id')) === -1) return;
        }

        setTotalDistance(0, 0);

        // check depth limit
        var depth = this.dragDepth - 1 + this.$pointEl.parents(opt.listNodeName).length;
        var $placeholderParent = this.$placeholder.parent();

        if (depth > opt.maxDepth) {
          opt.event.onItemMaxDepth.forEach(function (cb, i) {
            cb(this.$dragItem);
          });
          // if empty create new list to replace empty placeholder
        }

        // note: while dragging from up to down the placeholder will push the item upwards, therefore
        // we need to calculate position using an element with absolute position
        var before = e.pageY < (this.$pointEl.offset().top + this.$pointEl.height() / 2);

        if (this.$pointEl.hasClass(opt.emptyClass)) {
          var $list = $(document.createElement(opt.listNodeName)).addClass(opt.listClass);
          $list.append(this.$placeholder);
          this.$pointEl.replaceWith($list);
        }
        // $placeholderParent !== this.$pointEl make sure we drag up/down only
        else if (before && $placeholderParent !== this.$pointEl) {
          this.$pointEl.before(this.$placeholder);
        }
        else if (mouse.dirY > 0 && $placeholderParent !== this.$pointEl) {
          this.$pointEl.after(this.$placeholder);
        }

        if ($placeholderParent.children().length === 0) {
          this.unsetEmptyParent($placeholderParent.parent());
        }

        if (this.dragRootEl.find(opt.itemNodeName).length === 0) {
          this.dragRootEl.append('<div class="' + opt.emptyClass + '"/>');
        }

        if (hasRootChanged) {
          this.dragRootEl = $rootListOfPointingElement;
          this.hasNewRoot = this.$instance[0] !== this.dragRootEl[0];
        }
      }
    }
  };

  /**
   * Works like a proxy to Plugin prototype.
   * Separates the API of the developer from the API
   * of the user.
   */
  function PublicPlugin(plugin, lists) {
    if (!plugin) throw new TypeError('expected object, got ' + typeof plugin);
    this._plugin = plugin,
      this._lists = lists;
  }

  PublicPlugin.prototype = {
    getLists:           function () {
      return this._lists;
    },
    parseJson:          function (data, override) {
      var data = data || null, override = override || false;
      this._plugin.deserialize(data, override);
      return this;
    },
    toJson:             function () {
      var data = this._plugin.serialize();
      return JSON.stringify(data);
    },
    expandAll:          function () {
      this._plugin.expandAll(function () {
        return true;
      });
      return this;
    },
    collapseAll:        function () {
      this._plugin.collapseAll(function () {
        return true;
      });
      return this;
    },
    /**
     * @desc Expand items one by one. If callback returns then the item will be expanded.
     * @callback-params $item
     * @param cb
     * @returns {PublicPlugin}
     */
    expand:             function (cb) {
      this._plugin.expandAll(cb);
      return this;
    },
    /**
     * @desc Collapse items one by one. If callback returns then the item will be expanded.
     * @callback-params $item
     * @param cb
     * @returns {PublicPlugin}
     */
    collapse:           function (cb) {
      this._plugin.collapseAll(cb);
      return this;
    },
    /**
     * @desc  Listen toParse calls
     * @callback-params
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature onParseJson event listener
     * @returns {PublicPlugin}
     */
    onParseJson:        function (callback) {
      var _this = this;
      _this._plugin.options.event.onParseJson.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc  Fires after an item becomes a parent
     * @callback-params $item
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.87.53
     * @version-control +0.1.0 feature onItemSetParent event listener
     * @returns {PublicPlugin}
     */
    onItemSetParent:    function (callback) {
      var _this = this;
      _this._plugin.options.event.onItemSetParent.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc  Fires after a parent is unset
     * @callback-params $parent
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.87.53
     * @version-control +0.1.0 feature onItemSetParent event listener
     * @returns {PublicPlugin}
     */
    onItemUnsetParent:  function (callback) {
      var _this = this;
      _this._plugin.options.event.onItemUnsetParent.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Listen to toJson calls
     * @callback-params
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen to toJson calls
     * @returns {PublicPlugin}
     */
    onToJson:           function (callback) {
      var _this = this;
      _this._plugin.options.event.onToJson.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Listen for save events
     * @callback-params jQueryCollection inputCollection
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for editBoxSave events
     * @returns {PublicPlugin}
     */
    onSaveEditBoxInput: function (callback) {
      var _this = this;
      _this._plugin.options.event.onSaveEditBoxInput.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when user starts to drag an item
     * @callback-params jQueryCollection dragItem, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for itemDrag events
     * @returns {PublicPlugin}
     */
    onItemDrag:         function (callback) {
      var _this = this;
      _this._plugin.options.event.onItemDrag.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when the user stops to drag an item
     * @callback-params jQueryCollection dragItem, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen from itemDrop events
     * @returns {PublicPlugin}
     */
    onItemDrop:         function (callback) {
      var _this = this;
      _this._plugin.options.event.onItemDrop.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when an item has been added to the list
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for itemAdded events
     * @returns {PublicPlugin}
     */
    onItemAdded:        function (callback) {
      var _this = this;
      _this._plugin.options.event.onItemAdded.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when an item has been removed
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for itemRemoved events
     * @returns {PublicPlugin}
     */
    onItemRemoved:      function (callback) {
      var _this = this;
      this._plugin.options.event.onItemRemoved.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when an item is entering the edit mode
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for itemStartEdit events
     * @returns {PublicPlugin}
     */
    onItemStartEdit:    function (callback) {
      var _this = this;
      this._plugin.options.event.onItemStartEdit.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when an item is exiting the edit mode
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since >0.0.1
     * @version-control +0.1.0 feature listen for itemEndEdit events
     * @returns {PublicPlugin}
     */
    onItemEndEdit:      function (callback) {
      var _this = this;
      this._plugin.options.event.onItemEndEdit.push(callback.bind(_this));
      return _this;
    },
    /**
     * @desc Fires when an item adds a child item
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.13.29
     * @version-control +0.1.0 feature listen for itemAddChildItem events
     * @returns {PublicPlugin}
     */
    onItemAddChildItem: function (callback) {
      var _this = this;
      this._plugin.options.event.onItemAddChildItem.push(callback.bind(_this));
      return _this;
    },

    /**
     * @desc Fires when an item is being created
     * @dev-since 0.48.53
     * @version-control +0.1.0 feature listen for onCreateItem events
     */
    onCreateItem: function (callback) {
      var _this = this;
      this._plugin.options.event.onCreateItem.push(callback.bind(_this));
      return _this;
    },

    /**
     * @desc Fires when an item has been collapsed
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.48.53
     * @version-control +0.1.0 feature listen for onItemCollapsed events
     * @returns {PublicPlugin}
     */
    onItemCollapsed: function (callback) {
      var _this = this;
      this._plugin.options.event.onItemCollapsed.push(callback.bind(_this));
      return _this;
    },

    /**
     * @desc Fires when an item has been expanded
     * @callback-params jQueryCollection item, MouseEvent event
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.48.53
     * @version-control +0.1.0 feature listen for onItemCollapsed events
     * @returns {PublicPlugin}
     */
    onItemExpanded: function (callback) {
      var _this = this;
      this._plugin.options.event.onItemExpanded.push(callback.bind(_this));
      return _this;
    },

    /**
     * @desc Fires when the max depth of an item prevents nesting additional children
     * @callback-params jQueryCollection parentElement
     * @callback-context PublicPlugin
     * @param callback
     * @dev-since 0.87.53
     * @version-control +0.1.0 feature listen for onItemMaxDepth events
     * @returns {PublicPlugin}
     */
    onItemMaxDepth: function (callback) {
      var _this = this;
      this._plugin.options.event.onItemMaxDepth.push(callback.bind(_this));
      return _this;
    },

    /**
     * @desc Setup a callback for multiple events
     * @dev-since 0.48.53
     * @param eventBag array or string containing event names
     * @version-control +0.1.0 feature listen on many events simultaneously, use '*' to listen for all events
     * @returns {PublicPlugin}
     */
    on: function (eventBag, callback) {
      var _this = this;
      if (typeof eventBag === "object") {
        eventBag.forEach(function (event, i) {
          _this._plugin.options.event[event].push(callback.bind(_this));
        });
      } else if (eventBag === "*") {
        Object.keys(_this._plugin.options.event).forEach(function (event, c) {
          _this._plugin.options.event[event].push(callback.bind(_this))
        });
      } else if (typeof eventBag === "string") {
        _this._plugin.options.event[eventBag].push(callback.bind(_this));
      }
      return _this;
    },

    getListNodes: function () {
      var opt       = this._plugin.options,
          listNodes = this._plugin.$instance.find(opt.listNodeName);
      return listNodes;
    },

    /**
     * @desc Get the current plugin configuration
     * @dev-since 0.0.1
     * @version-control +0.1.0 feature get current plugin configuration
     * @returns Object
     */
    getPluginOptions: function () {
      return this._plugin.options;
    }
  };

  /**
   * @dev-since 0.0.1
   * @version-control +0.0.1 unused variables cleanup
   * @version-control +0.0.1
   * @dev-since 0.13.29
   * @version-control +0.0.5 random key generation improvements
   */
  $.fn.domenu = function (params) {
    var lists   = this.first(),
        domenu  = $(this),
        plugin  = domenu.data("domenu") || new Plugin(this, params),
        pPlugin = new PublicPlugin(plugin, lists);

    if (params) plugin.options = $.extend(true, {}, defaults, params);
    if (!domenu.data("domenu") || params) domenu.data("domenu", plugin);
    if (!domenu.data("domenu-id")) {
      var pseudoRandomNumericKey = Math.random().toString().replace(/\D/g, '');
      domenu.data('domenu-id', pseudoRandomNumericKey);
    }

    return pPlugin || plugin;

  }
})(window.jQuery || window.Zepto, window, document);




$(document).ready(function() {

    var $domenu            = $('#domenu-1'),
        domenu             = $('#domenu-1').domenu(),
        $outputContainer   = $('#domenu-1-output'),
        $jsonOutput        = $outputContainer.find('.jsonOutput'),
        $keepChanges       = $outputContainer.find('.keepChanges'),
        $clearLocalStorage = $outputContainer.find('.clearLocalStorage');


//alert(window.localStorage.getItem('domenu-1Json'))

//var checkLegacy = JSON.stringify(_data.slides);

	$domenu.domenu({
        slideAnimationDuration: 0,
        allowListMerging: ['domenu-2'],
        select2:                {
          support: true,
          params:  {
            tags: true
          }
        },
        //data:                   window.localStorage.getItem('domenu-1Json') || '[{"title":"Account","customSelect":"select something...","select2ScrollPosition":{"x":0,"y":0}},{"title":"Settings","customSelect":"select something...","select2ScrollPosition":{"x":0,"y":0}},{"title":"Call","customSelect":"select something..."},{"title":"Support","customSelect":"select something..."},{"title":"Email","customSelect":"select something..."},{"title":"Orders","customSelect":"select something..."},{"title":"Manage","customSelect":"select something..."},{"title":"Settings","customSelect":"select something..."}]'
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

