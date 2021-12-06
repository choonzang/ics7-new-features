# 이번 달 달력 만들기

기존의 액션태그로는 달력을 만들기가 매우 어려웠습니다.  변수 , 반복구문, 날짜 연산 등의 처리를 javascript를 이용하여 이번달에 해당하는 달력을 만들고, 액션태그를 통해 가져온 컨텐츠의 게시된 날짜와 매핑하여 해 아티클의 정보를 제공하는 예제입니다. &#x20;

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]
//액션태그로 현재 년도와 월을 구해서 이번 달의 아티클 리스트를 dataset 변수에 저장합니다.
[[--RecordStart,thismonth--]][[--Date,pattern:yyyyMM--]][[--RecordEnd--]]
var dataset = [
[[--ActionStart,row:*,sck_03040000,search:startdate==[%thismonth%],sort:id=desc--]][[--RecordStart,checkindex--]][[--ArtIndex--]][[--RecordEnd--]]
[[--IFStart,is:[%checkindex%]=1--]][[--thenstart--]][[--thenend--]][[--elsestart--]],[[--elseend--]][[--IFEnd--]]{"DAYON":"[[--ArtStartDate,pattern:d--]]","article":"[[[--ArtID--]]] [[--ArtTitle,length:10--]]","link":"[[--ArtAddress--]]"}
[[--ActionEnd--]]
];

	//javascript를 통해 현재년도와 월, 오늘날짜를 구해서 변수로 저장합니다.
	var cal=new Date();  // 데이트 객체 생성
	var year=cal.getFullYear(); // 현재 년도
	var month=cal.getMonth()+1; // 현재 월
	var date=cal.getDate();   // 오늘 날짜
	var firstDay=new Date(year,month-1,1).getDay(); // 현재 월의 첫째 요일 값 0~6  1
	var lastDay=new Date(year,month,0).getDate(); // 마지막 날짜
	var cnt=0; // 줄바꿈하기 위한 카운트 변수

	var	calendar="<table style='text-align:center;width:100%;height:100%' border='1'>";
	calendar+="<caption>"+year+"년 "+month+"월</caption>";
	
	calendar+="<tr>";
	calendar+="<td width='14%' style=color:red><b>일</td>";
	calendar+="<td width='14%'><b>월</td>";
	calendar+="<td width='14%'><b>화</td>";
	calendar+="<td width='14%'><b>수</td>";
	calendar+="<td width='14%'><b>목</td>";
	calendar+="<td width='14%'><b>금</td>";
	calendar+="<td width='14%' style=color:blue><b>토</td>";
	calendar+="</tr>";

	//캘린더를 구현합니다.
	calendar+="<tr>";
	for(var i=0;i<firstDay;i++){ // 공백 넣기
		calendar+="<td>&nbsp;</td>";
		cnt++;
	}	
	for(var i=1;i<=lastDay;i++){ // 숫자 출력
		if(cnt==0){ // 일요일이면 빨간색
			calendar+="<td style=color:red>";
			calendar+=i;
			//이번달의 ICS의 아티클의 오늘날짜와 일치하는 지를 비교하고, 일치할 경우, 해당 아티클 정보 및 링크를 걸어줍니다.
				dataset.forEach(function(item,idx){
					var tt = i;
					tt += "";
					if(dataset[idx].DAYON === tt) {
						calendar+= '<br/><a href="'+dataset[idx].link+'">'+dataset[idx].article+'</a>';
					}
				})
			calendar+="</td>";
			cnt++;
		}else if(cnt==6){ // 토요일이면 파란색
			calendar+="<td style=color:blue>";
			calendar+=i;
			//이번달의 ICS의 아티클의 오늘날짜와 일치하는 지를 비교하고, 일치할 경우, 해당 아티클 정보 및 링크를 걸어줍니다.
				dataset.forEach(function(item,idx){
					var tt = i;
					tt += "";
					if(dataset[idx].DAYON === tt) {
						calendar+= '<br/><a href="'+dataset[idx].link+'">'+dataset[idx].article+'</a>';
					}
				})		
			calendar+="</td>";
			cnt++;
		}else{
			calendar+="<td>";
			calendar+=i;
			//이번달의 ICS의 아티클의 오늘날짜와 일치하는 지를 비교하고, 일치할 경우, 해당 아티클 정보 및 링크를 걸어줍니다.

				dataset.forEach(function(item,idx){
					var tt = i;
					tt += "";
					if(dataset[idx].DAYON === tt) {
						calendar+= '<br/><a href="'+dataset[idx].link+'">'+dataset[idx].article+'</a>';
					}
				})
				
			calendar+="</td>";
			cnt++;	
		}		
		
		if(cnt%7==0){
			calendar+="</tr><tr>"; //줄 바꿈
			cnt=0;;
		}
	}
	for(var i=0;i<7-cnt;i++)
		calendar+="<td>&nbsp;</td>"; // 마지막 날짜 이후의 남은 공백 넣기
		
	calendar+="</tr>";
	print(calendar);
	[[--ScriptEnd--]]
```

### Result

> 예제는 2021년 11월1일에 3개의 아티클이 있습니다.

**2021년 11**

| **일** | **월**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **화** | **수** | **목** | **금** | **토** |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- | ----- | ----- | ----- | ----- |
|       | <p>1<br><a href="https://isd.i-on.net/choonzang/publish/preview.do?pageNumber=1&#x26;pageString=1&#x26;catId=sck_03040000&#x26;tplId=1406&#x26;artId=1185984&#x26;publishingDate=20211101-153331">[1185984] Key Factor...</a><br><a href="https://isd.i-on.net/choonzang/publish/preview.do?pageNumber=1&#x26;pageString=1&#x26;catId=sck_03040000&#x26;tplId=1406&#x26;artId=1185983&#x26;publishingDate=20211101-153331">[1185983] The Big De...</a><br><a href="https://isd.i-on.net/choonzang/publish/preview.do?pageNumber=1&#x26;pageString=1&#x26;catId=sck_03040000&#x26;tplId=1406&#x26;artId=1185982&#x26;publishingDate=20211101-153331">[1185982] I-ON Commu...</a></p> | 2     | 3     | 4     | 5     | 6     |
| 7     | 8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 9     | 10    | 11    | 12    | 13    |
| 14    | 15                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 16    | 17    | 18    | 19    | 20    |
| 21    | 22                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 23    | 24    | 25    | 26    | 27    |
| 28    | 29                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 30    |       |       |       |       |



## 샘플 URL

[https://isd.i-on.net/new/gst/cal/exam\_04.html](https://isd.i-on.net/new/gst/cal/exam\_04.html)
