# Accordions

## 개요

![](<../../.gitbook/assets/스크린샷 2021-12-06 오후 4.11.36.png>)

Accordions Type 구성입니다. 슬롯을 추가할수록 항목이 밑으로 증가 됩니다. FAQ메뉴에서 자주 사용되기도 하는데, 일정표형태로 구현된 Component입니다.

하나의 슬롯 안에는 시간, 제목, 설명, 작성자의 정보를 관리하고 있습니다.

## 참고 URL

[https://isd.i-on.net/new/ac/sample07/exam\_01.html](https://isd.i-on.net/new/ac/sample07/exam\_01.html)

## Component 구성

### 기본설정

Multiple Value Action Component

popup width : 600, popup height : 500

Option , width : 100%



### 필드설정&#x20;

필드는 4개로 구성되어있습니다. &#x20;

1.  Time(Text Type) &#x20;

    시간정보를 입력합니다.

    &#x20;
2.  Title(Text Type)

    타이틀을 입력합니다.


3.  Description (Multi Text Type)

    설명글을 입력합니다.


4.  Writer (Text Type)

    작성자를 입력합니다.



### vue.js

#### Sample Data

```json
{
    "multipleData": [
        {
            "m_time": "",
            "m_title": "",
            "m_desc": "",
            "m_writer": ""
        },
        {
            "m_time": "",
            "m_title": "",
            "m_desc": "",
            "m_writer": ""
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
      <div class="col-md-12 text-center margin-seven-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Multi Value Component</span>        
        <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-12 col-lg-10 px-0">
        <div class="panel-group accordion-event accordion-style-04" id="accordion4" data-active-icon="icon-feather-minus" data-inactive-icon="icon-feather-plus">
          <!-- start accordion item -->
          <div class="panel border-color-black-transparent" v-for="(node, index) of multipleData">

            <div v-bind:class="['panel-heading', (index === 0 ? 'active-accordion': '')]">
              <span class="panel-time">{{node.m_time}}</span>
              <a class="accordion-toggle" data-bs-toggle="collapse" data-bs-parent="accordion4" :href="'#accordion-style-4-'+(index+1)+''">
                <div class="panel-title">
                  <span class="text-extra-dark-gray d-inline-block font-weight-700">{{node.m_title}}</span>
                  <i v-bind:class="['text-extra-dark-gray feather', (index === 0 ? 'icon-feather-minus': 'indicator icon-feather-plus')]"></i>
                </div>
              </a>
              <span class="panel-speaker">{{node.m_writer}}</span>
            </div>

            <div :id="'accordion-style-4-'+(index+1)+''" v-bind:class="['panel-collapse collapse', (index === 0 ? 'show': '')]" data-bs-parent="#accordion4">
              <div class="panel-body">{{node.m_desc}}</div>
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
