# Call To Action

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_05.png)

고정된 영역에 정보 변경해서 버튼 클릭을 유도하는 Call To Action Type입니다. 하나의 슬롯안에 배경이미지, 타이틀, 링크가 존재하고, 마케터는 이 정보를 변경관리하도록 합니다.&#x20;

## 참고 URL

[https://isd.i-on.net/new/ac/sample08/exam\_01.html](https://isd.i-on.net/new/ac/sample08/exam\_01.html)

## Component 구성&#x20;

### 기본설정

Basic Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### 필드설정&#x20;

필드는 3가지로 구성하였습니다.

1.  Image (이미지 타입)

    배경으로 노출될 이미지 파일을 직접 등록하거나, 외부 이미지 경로를 입력합니다.&#x20;


2.  Title (텍스트타입)

    타이틀 정보를 입력합니다.

    &#x20;
3.  Link (텍스트타입)

    링크로 연결될 URL정보를 입력합니다.



### vue.js

#### Sample Data

```json
{
    "ac_cta_image_1": {
        "select": "url",
        "url": "",
        "name": "",
        "type": "",
        "size": 0,
        "lastModified": ""
    },
    "ac_cta_title_01": "",
    "ac_cta_link": "",
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### 템플릿

```html
<section style="padding:130px 0px 0px 0px;">
<div class="container-fluid">
    <div class="row justify-content-center">
      <div class="col-md-12 text-center margin-five-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
        <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
      </div>
    </div>
  </div>  
</section>
<section class="parallax wow animate__fadeIn" data-parallax-background-ratio="0.5" :style="'background-image: url(' + ac_cta_image_1.url + ');'">
<div class="opacity-medium bg-dark-slate-blue"></div>
  <div class="container">
    <div class="row align-items-center justify-content-center">
      <div class="col-12 col-xl-7 col-md-8 col-sm-10 position-relative text-center text-md-start sm-margin-30px-bottom">
        <h4 class="alt-font font-weight-600 text-white mb-0">{{ac_cta_title_01}}</h4>
      </div>
      <div class="col-12 col-xl-5 col-md-4 position-relative text-center text-md-end">
        <a :href="ac_cta_link" class="btn btn-large btn-gradient-shamrock-green-light-orange">More</a>
      </div>
    </div>
  </div>
</section>
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

(none)
