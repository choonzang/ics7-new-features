# Open API로 날씨정보 가져오기

공공 API를 활용하여, ICS의 템플릿 내에서도 활용이 가능합니다. Graal Script를 이용하여, API 호출 및 변환, 출력을 javascript를 이용하여 처리합니다. &#x20;

아래의 케이스는 공공 API를 이용하여 특정 지역의 날씨정보를 가져오는 API를 구현한 케이스입니다. $H.http() 객체를 사용하여, 외부 API를 호출하였으며, header와 data로 넘기는 key 와 value는 서비스에서 요구되는 기준에 맞게 전달되어야 합니다.&#x20;

참고한 API는 공공 API 서비스입니다. 요청주소와 서비스 키는 아래 서비스에서 신청하실 수 있습니다.

기상청\_관광코스별 관광지 상세 날씨 조회서비스 : [https://www.data.go.kr/data/15056912/openapi.do](https://www.data.go.kr/data/15056912/openapi.do)

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]
try {
  var result = $H.http('http://apis.data.go.kr/1360000/TourStnInfoService/getTourStnVilageFcst', {
  type: 'GET',
  headers: {
  },
  data: {
    serviceKey: '서비스키', // 서비스 키를 발급받아주세요
    numOfRows: '1',
    pageNo: '1',
    dataType : 'JSON',
    CURRENT_DATE : [[--Date,pattern:yyyyMMdd--]]00, // 오늘날짜를 전달합니다
    HOUR : '24',
    COURSE_ID : 66 //첨단거리 - 강남을 지정하여 예보를 받습니다 
  },
});
} catch (error) {
  //에러가 발생할 경우, 기본값이 될 정보를 결과로 정의할 수 있습니다
  var result = '{"response":{"header":{"resultCode":"00","resultMsg":"NORMAL_SERVICE"},"body":{"dataType":"JSON","items":{"item":[{"tm":"2021-10-20 21:00","thema":"쇼핑/놀이","courseId":"66","courseAreaId":"1100000000","courseAreaName":"서울특별시","courseName":"비첨단거리-강남","spotAreaId":6602,"spotAreaName":"서울","spotName":"(서울)미디어스틱","th3":9,"wd":329,"ws":1,"sky":1,"rhm":70,"pop":0}]},"pageNo":1,"numOfRows":1,"totalCount":1}}}';
}

var list = JSON.parse(result);

// API가 반환하는 값을 원하는 형식으로 변환합니다
function CheckSky(i){
var skynum = ['정보없음','맑음', '구름', '흐', '비', '소나기', '비눈', '눈비', '눈'];
 return skynum[i];
}

list.response.body.items.item.forEach(function(node){
  print('예보시각: ' + node.tm + '<br/> 지역 : ' + node.courseAreaName +'  '+ node.courseName +' '+node.spotName+'<br/> 하늘상태 : '+ CheckSky(node.sky)+'<br/> 습도 : '+ node.rhm+'%<br/> 강수확률 : '+ node.pop+'% <br/><br/>')
});

[[--ScriptEnd--]]
```

### Result

예보시각: 2021-11-03 21:00&#x20;

지역 : 서울특별시 첨단거리 - 강남 (서울)미디어폴&#x20;

하늘상태 : 흐림&#x20;

습도 : 80%&#x20;

강수확률 : 20%



### 예제 URL

[https://isd.i-on.net/new/gst/restapi/exam\_04.html](https://isd.i-on.net/new/gst/restapi/exam\_04.html)
