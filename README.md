---
coverY: 0
---

# Graal Script 개요

그 동안  ICS내에서 사용된 액션태그는 스크립트 언어로 확장성 및 기능성에서 많은 제약요소를 가지고 있었습니다.&#x20;

이번 New Features에서 Graal Script를 통해서 액션태그가 익숙하지 않은 파트너사는 ICS가 생성한 JSON데이터를 javascript 로  front end를 구축할 수 있도록 하였습니다. 이 의미는 액션태그 뿐 아니라, 범용 스크립트를 통한 템플릿 개발을 확장할 수 있음을 말하며,  연산, 외부 데이터에 접근 등의 활용이 가능하도록 함으로써, 앞으로 다양한 케이스의 구현이 가능해집니다.&#x20;

Graal Script 내에서 지원이 가능한 규격은 ECMAScript (ECMA-262) 사양에 규정을 따릅니다.

ECMAScript에 의해 지정된 전역 범위 에서 다음과 같은 함수 개체를 제공합니다.\
Array, ArrayBuffer, Boolean, DataView, Date, Error, Function, JSON, Map, Math, Number, Object, Promise, Proxy, Reflect, RegExp, Set, SharedArrayBuffer, String, Symbol, TypedArray, WeakMap 및 WeakSet

참고URL : [https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/](https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/)
