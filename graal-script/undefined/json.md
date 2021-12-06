# 직접 JSON 생성 및 활용

## \[\[--ArtJSON--]] Action Tag

Graal Script를 사용하기위해 ICS내의 콘텐츠를 JSON으로 생성하는 과정이 필요합니다. 이때 간단하게 JSON data를 생성해주는 \[\[--ArtJSON--]] 태그를 통해 사이트 카테고리내에 아티클 정보를 JSON형식으로 출력해주는 액션태그 입니다.

Story Template 내에서는 단독으로 사용이 가능한 \[\[--Art\~ --]]태그 이며, \[\[--ActionStart--]] \~ \[\[--ActionEnd--]] 사이에서도 사용할 수 있습니다.

| Attribute | Value         | Description                                                                                                               |
| --------- | ------------- | ------------------------------------------------------------------------------------------------------------------------- |
| pretty    | true or false | **JSON 출력 시, 포맷을 보기 편하도록 정렬하여 출력함**                                                                                       |
| comma     | true or false | **JSON 출력 시, 데이터 row에 따라 형식에 맞게 “,”를 붙여줌**                                                                                |
| except    | key1;key2;... | <p><strong>return 된 데이터 중에서 JSON으로 출력할 key를 제외함.</strong></p><p><strong>제외할 key를 여러개 설정하기 위해서는 ; 으로 추가하여 붙여줌</strong></p> |

Attribute에 따라 JSON 유형을 만들어 내면, Graal Script를 통해서 템플릿을 개발하거나, 외부에 제공할 JSON 파일을 생성하여 서버에 배포할 수 있습니다.

## 사용 예

### Template Code

```
[[--ScriptStart--]]
//javascript 변수 안에 ArtJSON으로 생성된  JSON 값을 선언합니다.
var result = [
[[--ActionStart,sitecategoryID,row:*--]]
[[--ARTJSON,pretty:false,COMMA:true,EXCEPT:content;keyword;modday;catid--]]
[[--ActionEnd--]]
];

//result의 row수 만큼 반복문을 실행하여 print 합니다.
result.forEach(function(node){
    print(node.artid +' '+ node.subject+'<br/><br/>')
});

[[--ScriptEnd--]]
```

### Result

{% hint style="info" %}
예시 콘텐츠 입니다
{% endhint %}

> 1185984 Key Factors to a Productive IT Work Culture
>
> 1185983 The Big Deal in Digital Innovation
>
> 1185982 I-ON Communications to Attend Mobile World Congress 2021
>
> 1185978 I-ON participates in 1:1 online business meetings with overseas buyers and investors
>
> 1185977 \[Column] E-commerce is growing. So should your business!
>
> 1185976 I-ON Communications to release Contact Share
>
> 1185975 I-ON Communications resumes to stretch its global business after
>
> 1185974 I-ON Communications to participate at GMV 2020

## 샘플 URL

[https://isd.i-on.net/new/gst/artjson/exam\_01.html](https://isd.i-on.net/new/gst/artjson/exam\_01.html)
