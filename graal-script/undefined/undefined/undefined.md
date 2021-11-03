# 할인율 적용

ICS의 콘텐츠에 가격에 대한 정보를 가지고 있다면, 그 가격에 연산처리를 통한 할인이 적용된 금액을 표현할 수 있습니다. 그 외에 다양한 연산식 (+,-,\*, / 등)을 사용하여 연산된 값을 적용할 수 있습니다.



## 사용 예 #1

### Template Code

```
[[--ScriptStart--]]

//action tag을 이용하여 af_price field에 10000원 값이 변수로 저장됩니다. 
var price = [[--ActionStart,row:1--]][[--ArtFieldValue,field:af_price--]][[--ActionEnd--]]
//discount 는 20% 할인율을 적용하여 변수로 저장됩니다.
var discount = price * 0.8;

//원가와 할인가를 출력합니다.
print('원가: <span style="text-decoration:line-through;">'+ price +'</span> , 할인가 :'+ discount+'<br/>');

[[--ScriptEnd--]]
```

### Result

원가: ~~10000~~ , 할인가 :8000

## 사용 예 #2

아티클에 ₩20000, ₩5000, ₩1000의 정보를 af\_price필드에 가지고 있는 3개의 콘텐츠가 있습니다. 여기에 ₩5000이상인 금액에서만 할인율 20%를 적용한 금액을 노출하도록 만들어 봅니다.

### Template Code

```
<strong>* 원가가 5,000원 이상인 경우, 할인율 20%를 해줌</strong> <br/><br/>

[[--ActionStart,row:*--]]
[[--ScriptStart--]]
// 가격정보(af_price, 20000/5000/1000)를 가지고 있는 콘텐츠 3건을 각각 불러와서 금액이 5000원 이상이면 할인율80%를 적용합니다.
var price = [[--ArtFieldValue,field:af_price--]]

//가격 비교 및 분기 처리 합니다. 
if (price >= 5000){
	var discount = price * 0.8;
} else {
	var discount = price;
}

print('원가: <span style="text-decoration:line-through;">'+ price +'</span> , 할인가 :'+ discount+'<br/>');

[[--ScriptEnd--]]
[[--ActionEnd--]]
```

### Result

**\* 원가가 5,000원 이상인 경우, 할인율 20%를 해줌**

원가: ~~20000~~ , 할인가 :16000&#x20;

원가: ~~5000~~ , 할인가 :4000&#x20;

원가: ~~1000~~ , 할인가 :1000
