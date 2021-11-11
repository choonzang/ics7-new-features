---
coverY: 0
---

# Graal Script 개요

{% hint style="info" %}
**Good to know:** Java 및 JVM 기반의 언어를 실행하여 수행하는 결과를 여러 범용적인 언어를 통해서 활용할 수 있도록 상호 운영성을 보장하기 위해서 제공되는 런타임을 라이브러리 GraalVM이라고 합니다.&#x20;
{% endhint %}

이번 New Features에서 ICS 내에서 GraalVM을 도입하였습니다. 이를 통해, ICS의 주된 개발언어 인 Java의 객체를  javascript와 같은 범용언어를 통한 활용이 가능하도록 확장 되었습니다. 프론트엔드의 대표적인 언어인 javascript와 같은 언어와 상호 호환성이 증가되고, 데이터를 처리하는 영역이 넓어졌습니다.

특히,  기존 액션태그는 아이온커뮤니케이션즈의 자체 스크립트 언어로 확장성 및 기능성에서 많은 제약요소를 가지고 있었습니다. 이에 액션태그가 익숙하지 않은 파트너사는 javascript만을 이용하여  front-end를 구축할 수 있도록 하였습니다.  이 의미는 범용 스크립트를 통한 템플릿 개발을 확장할 수 있음을 말하며,  연산, 외부 데이터에 접근 등의 활용이 가능하도록 함으로써, 앞으로 다양한 케이스의 구현이 가능하다는 것을 말합니다.

현재는 템플릿 개발에서 적용을 시작하지만,향 액션 스크립트를 사용하고 있는 컨텐츠 허브에서도 확대 적용할 계획입니다. &#x20;

Graal Script 내에서 지원이 가능한 규격은 ECMAScript (ECMA-262) 사양에 규정을 따릅니다.

ECMAScript에 의해 지정된 전역 범위 에서 다음과 같은 함수 개체를 제공합니다.\
Array, ArrayBuffer, Boolean, DataView, Date, Error, Function, JSON, Map, Math, Number, Object, Promise, Proxy, Reflect, RegExp, Set, SharedArrayBuffer, String, Symbol, TypedArray, WeakMap 및 WeakSet

참고URL : [https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/](https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/)
