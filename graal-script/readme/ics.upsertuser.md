---
description: Content Hub 만 가능
---

# $ICS.upsertUser()

Content Hub를 통해서 ICS 내에서 사용자의 정보를 추가할 경우 사용할 수 있는 객체입니다.

## 사용 예

### Code

```xml
<c:script sourceKey="contents" targetKey="xx0">
$ICS.upsertUser([
{userId:'id value', userNm:'name value'},
{userId:'id value', userNm:'name value'}
]);

</c:script>

<c:out sourceKey="xx0"/>
```
