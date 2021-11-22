---
description: Script Tag , Content Hub 사용 가능
---

# $H. http()

{% hint style="info" %}
**Good to know:** javascript에서는 외부 API를 호출하여 사용하기 위한 ajax가 있으나, Graal Script에서는 $H 객체를 제공하고 있습니다.
{% endhint %}

Graal Script 내에서 외부 API를 호출하기 위해 아이온커뮤니케이션즈는 $H.http()를 제공하고 있으며, 호출된 데이터를 Parsing하여 템플릿에 활용할 수 있습니다.&#x20;

headers, data를 넘길 시, API 제공 서비스 규격에 맞게 전달해주시면 됩니다.  다만, 외부 API를 호출 시, 의도하지 않게  API가 응답하지 않을 경우에 대한 처리를 위해 try catch를 이용하여 대비하는 것이 좋습니다.&#x20;

{% hint style="danger" %}
$H.http() 에서는 ICS 서버가 외부 서비스 API에 요청하는 방식입니다. 사전에 ICS서버에서 외부 서비스 요청할 수 있도록 방화벽의 설정이 오픈되어있어야 합니다.  &#x20;
{% endhint %}

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]

//API 호출 실패할 경우를 대비하여, try catch를 통해 에러 발생 시 처리 로직을 추가합니다.
try {
    //
     var result = $H.http('open api URL', {
      type: 'GET', // 호출 타입을 정의합니다.
      headers: {
          'key 1':'value 1', // header에 필요한 키와 값을 전달합니다.
          'key 2':'value 2'
      },
      data: {
          'param 1':'value 1', //데이터 호출에 필요한 쿼리를 parameter로 정의하거나, RAW Type의 json 형태로도 data를 넘길 수 있습니다.
          'param 2':'value 2'
      },
     });
     
    var list = JSON.parse(result);
    print (result);
    
    list.items.forEach(function(node){
      print(node.key1 + node.key2+'<br/>')
    });
} catch (error) {
// API호출 에러가 발생할 경우에 필요한 처리할 로직을 기입합니다.
    print('Error : ' + error);
}

[[--ScriptEnd--]]
```

