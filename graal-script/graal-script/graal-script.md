# Graal Script 란?

{% hint style="info" %}
**Good to know:** Java 및 JVM 기반의 언어를 실행하여 수행하는 결과를 여러 범용적인 언어를 통해서 활용할 수 있도록 상호 운영성을 보장하기 위해서 제공되는 런타임을 라이브러리 GraalVM이라고 합니다.&#x20;
{% endhint %}

Graal Script는 ICS를 개발한 java 안에서 필요한 함수를 활용할 수 있는 계기가 마련되었습니다. Graal Script는 기존의 액션태그 뿐만 아니라, Javascript으로도 템플릿 개발이 가능하도록 확장하기 위해 지원하는 스크립트입니다. 향후 다양한 요구를 반영하여 javascript 내에서 활용할 수 있는 다양 객체를 제공할 예정입니다.&#x20;

현재 적용된 Graal Script   javascript내에서 로직 처리가 끝난 이후에 최종 결과 데이터를 print()로 노출하는 방식으로 시작합니다.&#x20;

태그 내에서는 function을 추가하거나, 변수를 선언하거나, 연산, 조건문 등의 javascript처리가 가능합니다. 다만, 클라이언트 이벤트 방식에 대한 스크립트는 사용할 수 없습니다.

\[\[--ScriptStart--]] \~ \[\[--ScriptEnd--]] 태그 안에 사용된 javascript 를 실행합니다. 이 태그 안에는 액션태그와 혼용할 수 있습니다. 미리보기 또는 배포 시에는 이 태그 안에 사용된  javascript 코드는 템플릿에 노출되지 않고, Print()을 실행한 결과만 출력합니다.

## 사용 예

### Template code

```
[[--ScriptStart--]]

//javscipt code를 입력하며, 이 영역은 액션태그와 혼용할 수 있습니다 
var a = '안녕하세요';
var b = '반갑습니다';
var c = a + b ;

//최종 결과값 출력을 print()로 합니다
print(c);

[[--ScriptEnd--]]
```

### Result

> 안녕하세요 반갑습니다&#x20;
