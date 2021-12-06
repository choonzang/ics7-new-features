# Content Hub Script

## \<c:script> \~ \</c:script>

Content Hub 는 ICS가 이 시스템과의 DB 간의 연동을 위해서 데이터를 보내거나, 받기 위한 과정에 필요한 동작을 지원합니다. 예로 타 시스템의 데이터를 마이그레이션 해오거나, 타 시스템에 데이터를 전달하 등 DB 간의 데이터 교환을 위해 필요한 동작을 정의하고 있습니다.

이 과정에서 사용되는 Thoth Script 는 스텝별로 입력 값과 출력 값을 정의하여 처리합니다. 입력된 값을 로직에 따라 처리하고, 결과값을 전달하면, 다음 스텝에서 그 출력값을 다시 입력 받아 다음 스텝을 처리할 수 있습니다. 이러한 스텝을 통해 다른 시스템으로 데이터를 전달할 수 있고, 원하는 형식에 맞춰 변경할 수 있게 됩니다.

신규 기능에서는 이 과정에서 \<c:script>라는 스텝을 제공니다. \<c:script> 영역 내에서는 javascript를 데이터의 처리를 가능하도록 하여, 데이터를 불러오거나, 업데이트하거나, SQL을 실행하는 등의 작업을 정의할 수 있습니다.

## 사용 예

### Code

```xml
<!-- 변수a 에 필요한 데이터를 정의합니다. -->
<c:set targetKey="a">
    <property name="key">Hello</property>
    <property name="name">Graal</property>
</c:set>

<!-- 변수 b를 추가한 데이터를 content라는 변수에 정의합니다. -->
<c:script sourceKey="a" targetKey="B">
    var content = [];
    var b = {"name":"Script","key":"World!!"};
    
    content.push(a);
    content.push(b);

    return content;
</c:script>

<!-- content 라는 변수로 정의된 값을 B로 정의하여 출력합니다. -->
<c:out sourceKey="B"/>
```

### Result

| name   | key     |
| ------ | ------- |
| Graal  | Hello   |
| Script | World!! |

이와같이 정의된 값을 DB에 추가하여, 외부 시스템으로 전송하거나, 출력해 볼 수 있다.
