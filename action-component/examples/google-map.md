# Google Map

## 개요

![](<../../.gitbook/assets/스크린샷 2021-12-02 오전 10.48.40.png>)

지도에 위치를 표시하여 사용할 수 있도록 구글맵을 연계하여 서비스를 제공하는 Google Map Action Component입니다.  주소를 입력하거나, 위치명을 입력하면, 해당 위치를 중심으로 지도를 표시해줍니다.  &#x20;

고정된 영역에 정보 변경해서 버튼 클릭을 유도하는 Call To Action Type입니다. 하나의 슬롯안에 배경이미지, 타이틀, 링크가 존재하고, 마케터는 이 정보를 변경관리하도록 합니다

## 참고  URL

[https://isd.i-on.net/new/ac/sample12/exam\_01.html](https://isd.i-on.net/new/ac/sample12/exam\_01.html) &#x20;



## Component 구성

### 기본설정&#x20;

Option , width : 100%

popup width : 600, popup height : 500&#x20;

Basic Action Component



### 필드설정&#x20;

필드는 3가지로 구성하였습니다.

1.  위성 (불린 타입)

    위성지도를 사용할지를 선합니다.&#x20;


2.  주소 (텍스트 타입)

    지도를 표시할 위치의 주소 또는 지역명을 입력합니다.지배경으로 노출될 이미지 파일을 직접 등록하거나, 외부 이미지 경로를 입력합니다.&#x20;


3.  &#x20;Zoom (슬라이드 바 타입)

    지도의 확대 비율을 선택합니다. 1\~19



### vue.js

#### Sample Data

```json
{
    "address": "",
    "satellite": false,
    "zoom": 10,
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### Template

```html
<div class="container-fluid">
    <div class="row justify-content-center">
      <div class="col-md-12 text-center margin-five-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
        <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
      </div>
    </div>
  </div>  
<iframe width="100%" :height="accHeight+ 'px'" :src="'https://maps.google.com/maps?q=' + address + '&output=embed&ie=UTF8&iwloc=&z=' + zoom +'&' + (satellite ? 't=k' : '')"  frameborder="0" scrolling="no" marginheight="0" marginwidth="0"></iframe>
```



### JS

#### Add External javascript (CDN Links)

(none)

#### Javascript

(none)





##

&#x20;
