---
description: Content Hub 만 가능
---

# $H.ldap()

LDAP으로 부터 정보를 받아오기위해 아이온커뮤니케이션즈에서 제공하는 객제 $H.ldap()입니다. ICS를 ldap을 사용하는 기업과 연계하여 계정관리를 하는 경우, ldap으로 부터 필요한 정보를 요청하기 위해서 이 객체를 이용합니다.&#x20;

LDAP 접근경로, 아이디, 비밀번호, 필터 를 이용하여 LDAP  사용자 정보를 가져올 수 있습니다.

LDAP의 계정 정보를 ICS로 가져오게 되면, 동일한 사용자의 계정으로 ICS에서도 로그인을 할 수 있으므로, LDAP계정 연동할 경우에 유용합니다.

## 사용 예&#x20;

### Code

```xml
<c:script targetKey="xx1"><![CDATA[
var result= $H.ldap("ldap://ipaddress:port", "uid=ID,ou=People,dc=i-on,dc=net", "password", "objectclass=inetOrgPerson");
var list = JSON.parse(result); 

var users = [];
list.ldap.forEach(function(node){ 
    users.push({
        userid : node.attributes.uid,
        usernm : node.attributes.cn,
        email : node.attributes.mail
    });
});

return list.ldap ;
]]></c:script>

<c:out sourceKey="xx1"/>
```
