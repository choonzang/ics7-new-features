# 날짜 연산

날짜 연산을 통해서 입력된 날짜의 가감으로 연산된 날짜를 구해올 수 있습니다. 배포되는 시점에 연산된 결과를 출력하여 Template에 포함된 상태로 전송되므로, 날짜가 유동적으로 변경되는 경우, 배포를 주기적으로 이루어지도록 해야 합니다.

## 사용 예

### Template Code

```
[[--ScriptStart--]]

[[--ActionStart,row:1--]]
//아티클 게시일을 변수로 담기
let date = new Date([[--ArtStartDate,pattern:yyyy--]],[[--ArtStartDate,pattern:M--]] -1 ,[[--ArtStartDate,pattern:d--]]);
//아티클 게시일에 1달을 추가하여 변수에 담기 
let cal_date = new Date([[--ArtStartDate,pattern:yyyy--]],[[--ArtStartDate,pattern:M--]] -1 +1 ,[[--ArtStartDate,pattern:d--]]);
[[--ActionEnd--]]

print('아티클 게시일 출력: '+ date + '<br/>');
print('아티클 게시일 1달 더하기: '+ cal_date + '<br/>');

[[--ScriptEnd--]]
```

### Result

{% hint style="info" %}
예제의 아티클 게시일은 2021.10.17 입니다.
{% endhint %}

> 아티클 게시일 출력: Sun Oct 17 2021 00:00:00 GMT+0900 (KST)
>
> 아티클 게시일 1달 더하기: Wed Nov 17 2021 00:00:00 GMT+0900 (KST)

## 샘플 URL

[https://isd.i-on.net/new/gst/cal/exam\_03.html](https://isd.i-on.net/new/gst/cal/exam\_03.html)
