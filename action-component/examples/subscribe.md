# Subscribe

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_07.png)

뉴스레터 신청이나, 회원가입 등을 할때 사용자로 부터 받는 데이터를 접수받는 구성입니다. ICS는 사용자로부터 데이터를 받지 않기 때문에 이 데이터를 받기 위해서 외부 서비스 API를 사용하여 구현하였습니다.&#x20;

사용된 외부 서비스는 restdb.io 서비스로 API를 기반으로 인증된 시스템에서 GET, POST, UPDATE, DELETE 를 할수 있도록 지원합니다.  자세한 정보는 https://restdb.io 를 참고하세요.&#x20;

신청정보를 접수 처리하는 정보 이외에 좌측의 이미지와 타이틀, 메시지등의 정보는 component에서 관리됩니다.

## 샘플 URL

[https://isd.i-on.net/new/ac/sample10/exam\_01.html](https://isd.i-on.net/new/ac/sample10/exam\_01.html)

## Component 구성&#x20;

### 기본설정

Basic Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### 필드설정&#x20;

필드는 3가지로 구성하였습니다.

1.  Background Image  (이미지 타입)

    관련이미지로 노출될 파일을 직접 등록하거나, 외부 이미지 경로를 입력합니다.&#x20;


2.  Title (텍스트타입)

    타이틀 정보를 입력합니다.

    &#x20;
3.  Message (텍스트타입)

    링크로 연결될 URL정보를 입력합니다.



### vue.js

#### Sample Data

```json
{
    "sb_bg_image": {
        "select": "file",
        "name": "GettyImages-jv11323798.jpg",
        "type": "image/jpeg",
        "size": 1092704,
        "lastModified": 1634706103948
    },
    "sb_title": "Give me your e-mail address",
    "sb_message": "We'll send you the new news of Ion by e-mail.",
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### 템플릿

```html
<div class="row justify-content-center">
    <div class="col-md-12 text-center margin-seven-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
        <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
    </div>
</div>
<div class="row m-0 justify-content-center">
    <div class="col-12 col-xl-10 col-lg-11 bg-white box-shadow-large">
        <div class="row">
            <div class="col-12 col-md-6 cover-background sm-h-350px" :style="'background-image:url('+sb_bg_image.url+');'"></div>
            <div class="col-12 col-md-6 padding-6-rem-all lg-padding-5-rem-all md-padding-3-rem-all sm-padding-5-rem-all xs-padding-3-half-rem-all">
                <h5 class="alt-font font-weight-700 text-extra-dark-gray text-uppercase margin-20px-bottom">{{sb_title}}</h5>
                <p>{{sb_message}}</p>
                <div class="margin-10px-top d-inline-block w-100">
                    <input class="bg-light-gray border-radius-4px border-0 medium-input margin-20px-bottom required" type="text" name="name" placeholder="Your name" />
                    <input class="bg-light-gray border-radius-4px border-0 medium-input margin-20px-bottom required" type="email" name="email" placeholder="Your email address" />
                    <input type="hidden" name="redirect" value="">
                    <button class="btn btn-large btn-gradient-tan-geraldine btn-round-edge w-100 mb-0 submit" type="submit" onclick="sendSubscribe(); return false;">get started now</button>
                    <div style="font-size:12px;padding:10px 0px;">Interworked with <a href="https://restdb.io" target="_blank">https://restdb.io</a></div>                            
                    <div class="form-results border-radius-4px d-none"></div>
                </div>
            </div>
        </div>
    </div>
</div>
```



### JS

#### Add External javascript (CDN Links)

(none)



#### Javscript

(none)