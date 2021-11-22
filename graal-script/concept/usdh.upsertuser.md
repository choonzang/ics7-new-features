---
description: Content Hub 만 가능
---

# $H.upsertUser()- 준비중

Content Hub를 통해서 ICS 내에서 사용자의 정보를 추가할 경우 사용할 수 있는 객체입니다.&#x20;



## 사용 예&#x20;

### Code

```xml
<c:script sourceKey="contents" targetKey="xx0">
$H.upsertUser([{userId:'id value', userNm:'name value'},{userId:'id value', userNm:'name value'}]);

</c:script>

<c:out sourceKey="xx0"/>
```
