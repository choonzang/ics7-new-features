---
coverY: 0
---

# Graal Script 개요

{% hint style="info" %}
**Good to know:** Java 및 JVM 기반의 언어를 실행하여 수행하는 결과를 여러 범용적인 언어를 통해서 활용할 수 있도록 상호 운영성을 보장하기 위해서 제공되는 런타임을 라이브러리 GraalVM이라고 합니다.&#x20;
{% endhint %}

이번 New Features에서 ICS 내에서 GraalVM을 도입하여, ICS의 개발 환경인 Java 가 javascript와 같은 범용언어를 통한 실행이 가능하도록 확장됩니다. 상호호환성이 증가되고, 데이터를 처리하는 환경이 javascript 범용 언어를 통해서 제어가 가능해집니다.

특히,  ICS내에서 사용된 액션태그는 아이온커뮤니케이션즈의 자체 스크립트 언어로 확장성 및 기능성에서 많은 제약요소를 가지고 있었습니다. 액션태그가 익숙하지 않은 파트너사는 ICS가 생성한 JSON데이터를 javascript 로  front end를 구축할 수 있도록 하였습니다.  이 의미는 액션태그 뿐 아니라, 범용 스크립트를 통한 템플릿 개발을 확장할 수 있음을 말하며,  연산, 외부 데이터에 접근 등의 활용이 가능하도록 함으로써, 앞으로 다양한 케이스의 구현이 가능해집니다.

현재는 템플릿 개발에서 적용을 시작하지만, 액션 스크립트를 사용하고 있는 컨텐츠 허브에서도 확대 적용할 계획입니다. &#x20;

Graal Script 내에서 지원이 가능한 규격은 ECMAScript (ECMA-262) 사양에 규정을 따릅니다.

ECMAScript에 의해 지정된 전역 범위 에서 다음과 같은 함수 개체를 제공합니다.\
Array, ArrayBuffer, Boolean, DataView, Date, Error, Function, JSON, Map, Math, Number, Object, Promise, Proxy, Reflect, RegExp, Set, SharedArrayBuffer, String, Symbol, TypedArray, WeakMap 및 WeakSet

참고URL : [https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/](https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/)
