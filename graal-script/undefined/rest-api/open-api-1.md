# Open API로 날씨정보 가져오기 - 응용

공 API를 통해서 가져온 정보를 ICS의 콘텐츠와 매핑하여 서비스를 구현할 수 있습니다. 공공 API에서 예보된 날씨의 종류를 ICS에 미리 입력해둔 콘텐츠와 조건값이 일치하는 콘텐츠를 가져와서 서비스를 제공하는 케이스입니다.

공공 API에서 제공되는 정보 중로 하늘 상태의 값을 0\~8과 같이 숫자로 구분하고 있습니다. 다이나믹 서비스에서는 이 값에 따라 ICS에서 검색될 섬네일 이미지와 메시지를 콘텐츠등을 미 등록해두었습니다.

예보되는 하늘상태는 0=정보없음, 1=맑음, 2=구름, 3=흐림, 4=비, 5=소나기, 6=비눈, 7=눈비, 8=눈으로 정의됩니다.

ICS의 카테고리에는 af\_weather 액션필드에 0\~8에 대한 각각의 값과 콘텐츠를 등록해놓고, Dynamic Search Parameter에서 숫자값을 대입하여 검색된 결과의 콘텐츠 이미지와 메시지를 출력합니다.

배포 시점에 예보된 값을 가지고 오므로, 주기적인 배포 설정이 되어야 합니다.

## 사용 예&#x20;

### Template Code

```
[[--ScriptStart--]]
try {
  var result = $H.http('http://apis.data.go.kr/1360000/TourStnInfoService/getTourStnVilageFcst', {
  type: 'GET',
  aync:false,
  headers: {
  },
  data: {
    serviceKey: '서비스키', // 서비스 키를 발급받아주세요
    numOfRows: '1',
    pageNo: '1',
    dataType : 'JSON',
    CURRENT_DATE : [[--Date,pattern:yyyyMMdd--]]00,
    HOUR : '24',
    COURSE_ID : 66 //첨단거리 - 강남
  }
  });
} catch (error) {
    console.log('Error :' + error);
}


var list = JSON.parse(result);


function CheckSky(i){
var skynum = ['정보없음','맑음', '구름', '흐림', '비', '소나기', '비눈', '눈비', '눈'];
 return skynum[i];
}



list.response.body.items.item.forEach(function(node){

    try {
        // 다이나믹 서비스에서 af_weather 액션필드에 하늘상태 값에 따라 검색을 해옵니다 
        var result2 = $H.http("https://ICS Dynamic Server URL/dynamic/article/sck_01050000", {
          type: 'GET',
          aync:true,
          headers: {
          },
          data: {
          'search' : 'af_weather='+ node.sky+''
          }
        });

    } catch (error) {
        console.log('Error :' + error);
    }

    var list2 = JSON.parse(result2);


// ICS에 매칭된 섬네일 이미지 주소와 메시지 정보를 출력합니다.
print('[OPEN API 결과에 따라 ICS에 매칭된 섬네일 이미지와 메시지를 출력] <br/> '); 
print(list2.result.nodes[0].thumbnail+'<br/>');
print(list2.result.nodes[0].artcont+'<br/><br/><br/>')

  });


list.response.body.items.item.forEach(function(node){
// Open API의 결과를 출력합니다.
print('[OPEN API 결과 출력] <br/>'); 
print('' + node.courseAreaName +'  '+ node.courseName +' '+node.spotName+'<br/>');
print('하늘상태 : '+ CheckSky(node.sky)+'<br/> 습도 : '+ node.rhm+'% <br/>강수확률 : '+ node.pop+'% <br/>');
print('예보일자 : ' + node.tm + '');
});



[[--ScriptEnd--]]
```

### Result

\[OPEN API 결과에 따라 ICS에 매칭된 섬네일 이미지와 메시지를 출력]

&#x20;https://ICS Dynamic Server URL/dynamic/file/thumbnail/sck\_01050000/1185988/2021/11/02/tree-838666.jpg&#x20;

날이 좀 흐릴것 같네요. 기분 전환을 할수 있는 따듯한 음료를 준비하세요



\[OPEN API 결과 출력]

&#x20;서울특별시 첨단거리 - 강남 (서울)미디어폴&#x20;

하늘상태 : 흐림 습도 : 80% 강수확률 : 20%&#x20;

예보일자 : 2021-11-03 21:00



### 예제 URL

[https://isd.i-on.net/new/gst/restapi\_/exam\_01.html](https://isd.i-on.net/new/gst/restapi\_/exam\_01.html)
