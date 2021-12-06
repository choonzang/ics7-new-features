# 외부DB에서 정보 가져오기

접근이 가능한 외부DB 에 접속하여, 쿼리를 통해 얻어진 데이터를 JSON으로 받아서 javascipt로 출력합니다.&#x20;

connId 는 반드시 ICS의 "운영매니저 > 컨텐트 허브 > 연동DB정보" 에 정보를 등록하고 난 ID값으로 참조되어야 합니다.

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]
try {
        var result = $H.db({
                connId : "ICS의 콘텐츠 허브에 등록된 db정보 ID",
                query : "데이터를 가져올 쿼리"
        });
        

        var list = JSON.parse(result);
        
        //쿼리에서 얻은 JSON데이터를 출력
        print(JSON.stringify(list, null, '  ')+'<br/></br>');        
        
        //반복문으로 아티클 정보 출력               
        list.rows.forEach(function(node){
          print(node.artsubject +' ');
          print (new Date(node.credate)+'<br/><br/>');
        });

} catch(e) {
        //db접근이 실패할 경우에 대한 에러 처리 
        print('Error : ' + e)
}
[[--ScriptEnd--]]
```

### &#x20;Result

{% hint style="info" %}
예시 콘텐츠 입니다.
{% endhint %}

{ "rows": \[ { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185984, "artsubject": "Key Factors to a Productive IT Work Culture", "thumbimg": "", "credate": 1635729862536, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185983, "artsubject": "The Big Deal in Digital Innovation", "thumbimg": "", "credate": 1635729817815, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185982, "artsubject": "I-ON Communications to Attend Mobile World Congress 2021", "thumbimg": "", "credate": 1635729771340, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185978, "artsubject": "I-ON participates in 1:1 online business meetings with overseas buyers and investors", "thumbimg": "/2021/10/27/GettyImages-1244481806.jpeg", "credate": 1635302155067, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185977, "artsubject": " \[Column] E-commerce is growing. So should your business!", "thumbimg": "", "credate": 1635302108804, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185976, "artsubject": "I-ON Communications to release Contact Share", "thumbimg": "/2021/10/27/CS\_news.jpeg", "credate": 1635302071829, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185975, "artsubject": "I-ON Communications resumes to stretch its global business after pause due to Coronavirus Pandemic", "thumbimg": "/2021/10/27/GettyImages-1179837602\_1.jpeg", "credate": 1635302000216, "afields": null }, { "catid": "cck\_03030000", "creuserid": "choonzang", "artid": 1185974, "artsubject": "I-ON Communications to participate at GMV 2020", "thumbimg": "/2021/10/22/gmv\_20200512\_135322.png", "credate": 1634871115588, "afields": null } ] }



1185984 Key Factors to a Productive IT Work Culture Mon Nov 01 2021 10:24:22 GMT+0900 (KST)

1185983 The Big Deal in Digital Innovation Mon Nov 01 2021 10:23:37 GMT+0900 (KST)

1185982 I-ON Communications to Attend Mobile World Congress 2021 Mon Nov 01 2021 10:22:51 GMT+0900 (KST)

1185978 I-ON participates in 1:1 online business meetings with overseas buyers and investors Wed Oct 27 2021 11:35:55 GMT+0900 (KST)

1185977 \[Column] E-commerce is growing. So should your business! Wed Oct 27 2021 11:35:08 GMT+0900 (KST)

1185976 I-ON Communications to release Contact Share Wed Oct 27 2021 11:34:31 GMT+0900 (KST)

1185975 I-ON Communications resumes to stretch its global business after pause due to Coronavirus Pandemic Wed Oct 27 2021 11:33:20 GMT+0900 (KST)

1185974 I-ON Communications to participate at GMV 2020 Fri Oct 22 2021 11:51:55 GMT+0900 (KST)

## &#x20;샘플 URL

[https://isd.i-on.net/new/gst/db/exam\_01.html](https://isd.i-on.net/new/gst/db/exam\_01.html)
