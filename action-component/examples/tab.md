# Tab

## 개요

![](<../../.gitbook/assets/스크린샷 2021-12-06 오후 4.08.09.png>)

탭별로 관련된 콘텐츠를 보여주는 구성에 적용할 수 있는 Action Component입니다. 슬롯의 갯수만큼 탭을 생성할 수 있으며, 하나의 슬롯 안에는 이미지, 서브타이틀, 타이틀, 설명글, 링크 정보를 포함하고 있습니다.

## 참고 URL

[https://isd.i-on.net/new/ac/sample06/exam\_01.html](https://isd.i-on.net/new/ac/sample06/exam\_01.html)

## Component 구성

### 기본설정

Multiple Value Action Component

popup width : 600, popup height : 500

Option , width : 100%



### 필드설정&#x20;

필드는 6가지로 구성하였습니다.

1.  Tab Name (Text type)

    탭의 명칭을 입력합니다 .&#x20;


2.  Image (이미지 타입)

    배경으로 노출될 이미지 파일을 직접 등록하거나, 외부 이미지 경로를 입력합니다.&#x20;


3.  Title (텍스트타입)

    타이틀 정보를 입력합니다.


4.  .Description (다중 텍스트 타입)

    설명글을 입력합니다.

    &#x20;&#x20;
5.  Link (텍스트타입)

    링크로 연결될 URL정보를 입력합니다.


6.  Target (텍스트타입 )

    링크의 타겟을 선택합니다. 새창으로 열거나, 자기 창에서 열수 있습니다.&#x20;



### vue.js

#### Sample Data

```json
{
    "multipleData": [
        {
            "m_tab_name": "",
            "m_bg_image": {
                "select": "url",
                "url": "",
                "name": "",
                "type": "",
                "size": 0,
                "lastModified": ""
            },
            "m_title": "",
            "m_desc": "",
            "m_link": "",
            "m_align": "_self"
        }
    ],
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
    <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Multi Value Component</span>
    <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
  </div>
</div>

<div class="row">
  <div class="col-12 tab-style-01 without-number wow animate__fadeIn">
    <!-- start tab navigation -->
    <ul class="nav nav-tabs text-uppercase justify-content-center text-center alt-font font-weight-500 margin-7-rem-bottom md-margin-5-rem-bottom sm-margin-20px-bottom">
      <!--li class="nav-item"><a class="nav-link"  data-bs-toggle="tab" href="#planning-tab">Planning</a><span class="tab-border bg-extra-dark-gray"></span></li-->
      <li class="nav-item" v-for="(node, index) of multipleData">
        <a class="nav-link" v-bind:class="{active: index === 0}" data-bs-toggle="tab" :href="'#'+node.m_tab_name+'-tab'">{{node.m_tab_name}}</a>
        <span class="tab-border bg-extra-dark-gray"></span></li>

    </ul>
    <!-- end tab navigation -->
    <div class="tab-content">
      <!-- start tab item -->
      <div :id="''+node.m_tab_name+'-tab'" v-for="(node, index) of multipleData"  v-bind:class="['tab-pane fade', (index === 0 ? 'in active show': '')]">
        <div class="row align-items-center">
          <div class="col-12 col-md-6 text-end sm-margin-40px-bottom">
            <img :src="node.m_bg_image.url" alt="" />
          </div>
          <div class="col-12 col-lg-5 offset-lg-1 col-md-6 text-center text-sm-start">
            <span class="alt-font text-medium text-gradient-sky-blue-pink text-uppercase font-weight-500 margin-15px-bottom d-inline-block">{{node.m_subtitle}}</span>
            <h5 class="alt-font font-weight-600 text-extra-dark-gray margin-35px-bottom md-margin-30px-bottom">{{node.m_title}}</h5>
            <p class="w-85 lg-w-100">{{node.m_desc}}</p>
            <a :href="node.m_link" :target="node.m_align" class="btn btn-fancy btn-medium btn-dark-gray margin-20px-top">More</a>
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

(none)
