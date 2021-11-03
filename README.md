---
coverY: 0
---

# Graal Script 개요

액션태그 내 제한적이었던 기능을 Graal Script를 통해서 액션태그가 익숙하지 않은 파트너사는 ICS가 생성한 JSON데이터를 javascript 로  front end를 구축할수 있으므로 범용 스크립트를 통한 템플릿 개발을 확장할 수 있습니다. 또한 연산, 외부 데이터에 접근 등의 활용이 가능하도록 확장하는 방식을 지원하여, 다양한 케이스의 구현을 지원합니다.

Graal Script 내에서 지원이 가능한 규격은 ECMAScript (ECMA-262) 사양에 규정을 따릅니다.

ECMAScript에 의해 지정된 전역 범위 에서 다음과 같은 함수 개체를 제공합니다.\
Array, ArrayBuffer, Boolean, DataView, Date, Error, Function, JSON, Map, Math, Number, Object, Promise, Proxy, Reflect, RegExp, Set, SharedArrayBuffer, String, Symbol, TypedArray, WeakMap 및 WeakSet

참고URL : [https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/](https://docs.oracle.com/en/graalvm/enterprise/20/docs/reference-manual/js/JavaScriptCompatibility/)
