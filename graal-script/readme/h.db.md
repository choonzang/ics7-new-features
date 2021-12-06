---
description: Script Tag , Content Hub 사용 가능
---

# $H.db()

{% hint style="info" %}
**Good to know:** javascript 자체로 외부 DB를 Access가 불가능하기 때문에 ICS내에서 Content Hub 내에 외부DB의 계정 및 접속정보를 등록해야 합니다.
{% endhint %}

외부DB에 접근하여 쿼리한 데이터를 템플릿에 제공하기 위해서 아이온커뮤니케이션즈에서 지원하는 객체 $H.db()입니다.&#x20;

접속정보를 직접 입력하는 방식이 아니라, "ICS > Operation Manager > Content Hub > 연동DB정보"에 DB의 계정 정보를 입력하게 되면, connection ID(connId)를 생성할 수 있으며, 그 ID 를 이용하여 호출하는 방식입니다.

DB 접근 시, 의도하지 않게 접속이 되지 않을 경우, try, catch를 이용하여 이에 대한 예외 처리를 준비해야 합니다.

{% hint style="danger" %}
배포 또는 미리보기, 실 시점에 DB를 Access합니다. 이때 DB에 직접적인 부하를 줄 수 있으므로, 사용되는 쿼리는 DB의 부하를 고려한 적절한 쿼리 사용이 필요합니다. 또한 ICS에 등록된 DB 에 호출하는 query는 보안을 위해 조회성 요청으로 제한된 쿼리로만 호출이 가능합니다.&#x20;
{% endhint %}

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]

try {
        var result = $H.db({
                connId : 'OOOOO', // Content Hub > 연동DB정보 에 입력된 DB계정 정보 중에 id 를 여기에 입력합니다.
                query : "select * from *  where * order by *" // SQL query를 입력합니다.
        });
        

        var list = JSON.parse(result);
        print(JSON.stringify(list, null, '  ')); // Return된 모든 결과를 출력합니다.
        
        list.rows.forEach(function(node){
          print(node.key1 +' ');
          print (new Date(node.key2)+'<br/><br/>');
        });

} catch(error) {
        print('Error : ' + error)
}

[[--ScriptEnd--]]
```

