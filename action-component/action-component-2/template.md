# Template에 적용하기

생성된 Action Component를 사이트의 템플릿에 적용하기 위해서는 아래의 태그를 사용해야 합니다.

\[\[--Acmpt--]] 와 \[\[--AcmptJSLink--]]는 반드시 함께 사용되어야 하며, 위 기능을 사용시 관련된 js, css는 "\_\_icsFiles/acmpt"경로로 (호스트 정보 변경 시) 자동으로 포함되어 디플로이 됩니다.&#x20;



## \[\[--Acmpt--]] Action Tag

Action Component로 등록된 요소를 템플릿 내에 배치할 때 사용하는 액션태그 입니다. 단독으로 사용할 수 없으며, 다음에 설명할 \[\[--ACMPTJSLINK--]]와 혼용해야 합니다. &#x20;

List, Story template에서 사용할수 있으며, 아래 Attribute의 속성을 반드시 입력해야 합니다.

| Attribute | Value         | Description                                                                                              |
| --------- | ------------- | -------------------------------------------------------------------------------------------------------- |
| acmptId   | value         | **Action Component ID 를 입력함**                                                                            |
| accId     | value         | **Action Component에서 입력된 데이터를 저장할 데이터의 ID를 지정합니다. 임의 지정이 가능하고, 타 아이디와 중첩되지 않도록 유의해야함.**                  |
| realtime  | true or false | **true 시, Action Component 내에서 변경이 있을 경우, Dynamic으로 부터 데이터를 직접 Load 하여, Deploy 과정 없이 바로 서비스에 반영됨**       |
| public    | true or false | **true 시, 사이트에서도 단축키(Ctrl+F1)를 통해 Action Component로 편집기능을 활성화 함 (단, ICS Admin 에 로그인이 안되있을 경우, 사용이 불가함)** |

### 사용예

\[\[--ACMPT,acmptId:type\_01,accId:xxxxxx--]]



## \[\[--AcmptJSLink--]] Action Tag

Action Component 의 동작을 위해 필요한 Action Component javascript Utility를 불러오는 태그입니다. 다만, 해당 템플릿이 jQuery 를 사용하는 경우, 충돌이 발생할 수 있기 때문에 아래 Attribute의 속성을 통해서 사용여부를 선택하여 중복 선언이 되 않도록 해야 합니다.&#x20;

이 태그는 Action Component의 동작을 위해 필요한 Action Tag이므로, jQuery가 선언되는 HTML문서 하단 영역에 선언하는것이 좋습니다.

| Attribute     | Value         | Description                                                              |
| ------------- | ------------- | ------------------------------------------------------------------------ |
| excludeJQuery | true or false | **Action Component Javascript Utility에서 jQuery에 대한 선언을 제외할 것인지를 선택합니다.** |

### 사용예

\[\[--AcmptJSLink,excludeJQuery:true--]]





## Template 내에 사용 예시&#x20;

```
<html>
    <head>
    </head>
<body>
    <section>
        <div>
        <!-- type_01이라는 Action Component를 불러옴 -->
        [[--Acmpt,acmptID:type_01,accID:main_map,realtime:true,public:true--]]
        </div>
    </section>
    [[--AcmptJSLink,excludeJQuery:false--]]
</body>
</html>
```
