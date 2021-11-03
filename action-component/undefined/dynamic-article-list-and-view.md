# Dynamic Article List & View

## 개요&#x20;

![List](../../.gitbook/assets/fireshot\_02.png)

![View ](../../.gitbook/assets/fireshot\_02\_.png)

다이나믹 서비스를 이용하여 게시판을 구성한 예제입니다. 리스트와 상세보기를 하나의 컴포넌트로 구성할 수 있으며, 리스트만 구성하고, Story Template으로 생성된 페이지로 링크되도록 구성한 두가지 타입을 제공합니다.&#x20;

마케터는 리스트의 숫자 또는 검색 조건, 정렬 값, 아티클을 가져올 사이트카테고리만 수정할 수 있습니다.&#x20;

## 참고 URL

[https://isd.i-on.net/new/ac/sample03/exam\_01.html](https://isd.i-on.net/new/ac/sample03/exam\_01.html)

[https://isd.i-on.net/new/ac/sample04/exam\_01.html](https://isd.i-on.net/new/ac/sample04/exam\_01.html)

## Component

### 기본정보&#x20;

Basic Action Component&#x20;

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### 필드설정&#x20;

필드는 다음 총 5가지로 추가되어 있습니다.&#x20;

1.  카테고리(ics\_category)

    다이나믹으로 호출할 사이트 카테고리를 선택하는 필드입니다.  아티클이 있는 사이트 카테고리를 선택하도록 합니다.
2.  listnum

    콘텐츠의 갯수를 가져오는 필드입니다. 현재는 10건으로 리스트하도 등록되어있습니다.
3.  search&#x20;

    데이터를 가져올떄, 검색에 따른 조건으로 선별되어야 할때 필드의 값을 입력합니다. 현재는 설정값 없이 공란으로 두었습니다.
4.  sort

    데이터를 가져올때, 정렬 조건을 설정할 수 있습니다. 현재는 설정값 없이 공란으로 두었습니다.
5.  template (숨김상자)&#x20;

    다이나믹에서 결과를 가져왔을 떄, 보여질 다이나믹 서비스의 결과 템플릿을 아래의 소스와 같이 숨김파일로 등록되었습니다.  마케터가 템플릿을 수정할수 있다면, "숨김상자"를 하지 않고, "긴 입력상자"를 선택하여 팝업창에서 소스 코드를 수정하도록 하면 되지만, 마케터가 수정이 불가능하다면, 파트너사가 필드를 숨김상자로 만들어 해당 템플릿 소스를 등록할 수 있습니다.

#### 1. List 만 구현하고, Story페이지는 ICS에서 배포된 페이지로 링크되는 케이스에 Dynamic Service Template

```html
<div class="col-12 col-lg-12 blog-sidebar">
  <ul class="blog-widget position-relative">
    <!-- start post item -->
    <li v-for="(node, index) of nodes">
      <div class="d-flex border-bottom border-color-extra-light-gray padding-30px-top padding-30px-bottom  padding-30px-top">
        <figure class="flex-shrink-0">
          <a href="javascript:void(0)" @click="goStoryPage(node.catid, node.artid)"><img :src="node.thumbnail" alt="" v-if="node.thumbnail"><img src="https://www.i-on.net/assets/images/company/etc-logo.svg" alt="" v-else></a>
        </figure>
        <div class="media-body flex-grow-1">
          <a href="javascript:void(0)" @click="goStoryPage(node.catid, node.artid)" class="text-extra-small alt-font d-block margin-5px-bottom">{{node.operday.substring(0,4)}}.{{node.operday.substring(4,6)}}.{{node.operday.substring(6,8)}}</a>
          <a href="javascript:void(0)" @click="goStoryPage(node.catid, node.artid)" class="alt-font font-weight-500 text-extra-dark-gray margin-5px-bottom d-block line-height-22px">{{node.artsubject}}</a>
          <span class="text-extra-small alt-font">By <a href="javascript:void(0)" @click="goStoryPage(node.catid, node.artid)">{{node.reguserid}}</a></span>
        </div>
      </div>
    </li>
    <!-- end post item -->

  </ul>
  <!-- start pagination -->
  <div class="col-12 d-flex justify-content-center margin-7-half-rem-top md-margin-5-rem-top wow animate__fadeIn" style="visibility: visible; animation-name: fadeIn;">
    <ul class="pagination pagination-style-01 text-small font-weight-500 align-items-center">
      <li class="page-item"><a class="page-link" href="javascript:void(0)" @click="setPageNo(1)" v-if="response.pageout.prev>0"><i class="feather icon-feather-arrow-left icon-extra-small d-xs-none"></i></a></li>

      <li class="page-item" v-for="page of response.pageout.pages" :class="page==response.pageout.curr ? 'active' : ''"><a class="page-link" v-if="page==response.pageout.curr" href="javascript:void(0);">{{page}}</a><a class="page-link" v-else href="javascript:void(0);" @click="setPageNo(page)">{{page}}</a>
      </li>

      <li class="page-item"><a class="page-link" href="javascript:void(0)" @click="setPageNo(response.pageout.next)" v-if="response.pageout.next>0"><i class="feather icon-feather-arrow-right icon-extra-small  d-xs-none"></i></a></li>
    </ul>
  </div>
  <!-- end pagination-->
</div>


  <textarea id="searchJS" style='display:none'>
    var _key =  $('#searchKey').val();
    if(_key == '')  {
    	return '';
    }
    if($('#searchField').val() == 'all') {
        return 'artsubject==' + _key + '||artcont==' + _key ;
    }
    return $('#searchField').val() + '==' + _key;
  </textarea>
```

#### 2. List와 View(Story) 페이지를  모두 Dynamic Service Template으로 구성

```html
<div class="col-12 blog-details-text last-paragraph-no-margin margin-6-rem-bottom" v-if="isStoryMode()">
  <ul class="list-unstyled margin-2-rem-bottom">
    <li class="d-inline-block align-middle margin-25px-right"><i class="feather icon-feather-calendar text-fast-blue margin-10px-right"></i><a href="#">{{article.operday.substring(0,4)}}.{{article.operday.substring(4,6)}}.{{article.operday.substring(6,8)}}</a></li>
    <li class="d-inline-block align-middle margin-25px-right"><i class="feather icon-feather-folder text-fast-blue margin-10px-right"></i><a href="#"></a></li>
    <li class="d-inline-block align-middle"><i class="feather icon-feather-user text-fast-blue margin-10px-right"></i>By <a href="#">{{article.reguserid}}</a></li>
  </ul>
  <h5 class="alt-font font-weight-500 text-extra-dark-gray margin-4-half-rem-bottom">{{article.artsubject}}</h5>
  <img :src="article.thumbnail" alt="" class="w-100 border-radius-6px margin-4-half-rem-bottom" style="max-width:fit-content">
  <div v-html="article.artcont" class="border-bottom border-color-extra-light-gray padding-30px-bottom"></div>


  <div class="col-12 d-flex flex-wrap align-items-center padding-15px-tb mx-auto margin-20px-bottom wow animate__fadeIn">
    <div class="col-12 col-md-9 text-center text-md-start sm-margin-10px-bottom px-0">
    </div>
    <div class="col-12 col-md-3 text-center text-md-end px-0">
      <a class="likes-count text-uppercase text-extra-dark-gray font-weight-500" href="javascript:void(0)" @click="setArticle(null)"><span>List</span></a>
    </div>
  </div>
</div>

<div class="col-12 col-lg-12 blog-sidebar" v-else>
  <ul class="blog-widget position-relative">
    <!-- start post item -->
    <li v-for="(node, index) of nodes">
      <div class="d-flex border-bottom border-color-extra-light-gray padding-30px-top padding-30px-bottom">
        <figure class="flex-shrink-0">
          <a href="javascript:void(0)" @click="setArticle(node)"><img :src="node.thumbnail" alt="" v-if="node.thumbnail"><img src="https://www.i-on.net/assets/images/company/etc-logo.svg" alt="" v-else></a>
        </figure>
        <div class="media-body flex-grow-1">
          <a href="javascript:void(0)" @click="setArticle(node)" class="text-extra-small alt-font d-block margin-5px-bottom">{{node.operday.substring(0,4)}}.{{node.operday.substring(4,6)}}.{{node.operday.substring(6,8)}}</a>
          <a href="javascript:void(0)" @click="setArticle(node)" class="alt-font font-weight-500 text-extra-dark-gray margin-5px-bottom d-block line-height-22px">{{node.artsubject}}</a>
          <span class="text-extra-small alt-font">By <a href="javascript:void(0)" @click="setArticle(node)">{{node.reguserid}}</a></span>
        </div>
      </div>
    </li>
    <!-- end post item -->

  </ul>
  <!-- start pagination -->
  <div class="col-12 d-flex justify-content-center margin-7-half-rem-top md-margin-5-rem-top wow animate__fadeIn" style="visibility: visible; animation-name: fadeIn;">
    <ul class="pagination pagination-style-01 text-small font-weight-500 align-items-center">
      <li class="page-item"><a class="page-link" href="javascript:void(0)" @click="setPageNo(1)" v-if="response.pageout.prev>0"><i class="feather icon-feather-arrow-left icon-extra-small d-xs-none"></i></a></li>

      <li class="page-item" v-for="page of response.pageout.pages" :class="page==response.pageout.curr ? 'active' : ''"><a class="page-link" v-if="page==response.pageout.curr" href="javascript:void(0);">{{page}}</a><a class="page-link" v-else href="javascript:void(0);" @click="setPageNo(page)">{{page}}</a>
      </li>

      <li class="page-item"><a class="page-link" href="javascript:void(0)" @click="setPageNo(response.pageout.next)" v-if="response.pageout.next>0"><i class="feather icon-feather-arrow-right icon-extra-small  d-xs-none"></i></a></li>
    </ul>
  </div>
  <!-- end pagination-->
</div>


  <textarea id="searchJS" style='display:none'>
    var _key =  $('#searchKey').val();
    if(_key == '')  {
    	return '';
    }
    if($('#searchField').val() == 'all') {
        return 'artsubject==' + _key + '||artcont==' + _key ;
    }
    return $('#searchField').val() + '==' + _key;
  </textarea>
```





### vue.js

#### Sample Data

```json
{
    "ics_category": {
        "catId": "us_c_pr",
        "catNm": "Press Room",
        "catPath": "US I-ON Site>Company>Press Room"
    },
    "listnum": "10",
    "search": "",
    "sort": "",
    "template": "<div class=\"col-12 col-lg-12 blog-sidebar\">\n  <ul class=\"blog-widget position-relative\">\n    <!-- start post item -->\n    <li v-for=\"(node, index) of nodes\">\n      <div class=\"d-flex border-bottom border-color-extra-light-gray padding-30px-top padding-30px-bottom  padding-30px-top\">\n        <figure class=\"flex-shrink-0\">\n          <a href=\"javascript:void(0)\" @click=\"goStoryPage(node.catid, node.artid)\"><img :src=\"node.thumbnail\" alt=\"\" v-if=\"node.thumbnail\"><img src=\"https://www.i-on.net/assets/images/company/etc-logo.svg\" alt=\"\" v-else></a>\n        </figure>\n        <div class=\"media-body flex-grow-1\">\n          <a href=\"javascript:void(0)\" @click=\"goStoryPage(node.catid, node.artid)\" class=\"text-extra-small alt-font d-block margin-5px-bottom\">{{node.operday.substring(0,4)}}.{{node.operday.substring(4,6)}}.{{node.operday.substring(6,8)}}</a>\n          <a href=\"javascript:void(0)\" @click=\"goStoryPage(node.catid, node.artid)\" class=\"alt-font font-weight-500 text-extra-dark-gray margin-5px-bottom d-block line-height-22px\">{{node.artsubject}}</a>\n          <span class=\"text-extra-small alt-font\">By <a href=\"javascript:void(0)\" @click=\"goStoryPage(node.catid, node.artid)\">{{node.reguserid}}</a></span>\n        </div>\n      </div>\n    </li>\n    <!-- end post item -->\n\n  </ul>\n  <!-- start pagination -->\n  <div class=\"col-12 d-flex justify-content-center margin-7-half-rem-top md-margin-5-rem-top wow animate__fadeIn\" style=\"visibility: visible; animation-name: fadeIn;\">\n    <ul class=\"pagination pagination-style-01 text-small font-weight-500 align-items-center\">\n      <li class=\"page-item\"><a class=\"page-link\" href=\"javascript:void(0)\" @click=\"setPageNo(1)\" v-if=\"response.pageout.prev>0\"><i class=\"feather icon-feather-arrow-left icon-extra-small d-xs-none\"></i></a></li>\n\n      <li class=\"page-item\" v-for=\"page of response.pageout.pages\" :class=\"page==response.pageout.curr ? 'active' : ''\"><a class=\"page-link\" v-if=\"page==response.pageout.curr\" href=\"javascript:void(0);\">{{page}}</a><a class=\"page-link\" v-else href=\"javascript:void(0);\" @click=\"setPageNo(page)\">{{page}}</a>\n      </li>\n\n      <li class=\"page-item\"><a class=\"page-link\" href=\"javascript:void(0)\" @click=\"setPageNo(response.pageout.next)\" v-if=\"response.pageout.next>0\"><i class=\"feather icon-feather-arrow-right icon-extra-small  d-xs-none\"></i></a></li>\n    </ul>\n  </div>\n  <!-- end pagination-->\n</div>\n\n\n  <textarea id=\"searchJS\" style='display:none'>\n    var _key =  $('#searchKey').val();\n    if(_key == '')  {\n    \treturn '';\n    }\n    if($('#searchField').val() == 'all') {\n        return 'artsubject==' + _key + '||artcont==' + _key ;\n    }\n    return $('#searchField').val() + '==' + _key;",
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
      <div class="col-12 col-lg-6 text-center margin-4-rem-bottom sm-margin-3-rem-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
        <h6 class="alt-font font-weight-600 text-extra-dark-gray text-uppercase">{{accNm}}</h6>
      </div>
    </div>
</div>
<div class="container">
  <div class="row">
    <div id="dynamicData" v-html="template" :search="search" :sort="sort" :listnum="listnum" :catid="ics_category.catId" below="true" catids="" fields=""/>
  </div>
</div>
```



### JS

#### Add External javascript (CDN Links)





#### Javscript

```javascript
ACmptUtil.vueArticle('dynamicData');
```
