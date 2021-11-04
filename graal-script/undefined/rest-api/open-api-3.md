# Open API로 기사정보 가져오기 - 응용

앞서 기사검색을 위해 데이터를 요청할 떄, 아티클 중에 포함된 키워드 정보를 quiery로 요청하여, 관련된 기사를 불러오는 예제입니다.

Query에 필요한 키워드를 ICS의 주제어 입력 란에 입력된 정보를  받아서 Open API로 요청하여 결과를 받습니다.

&#x20;기업에서 보도자료를 내면, 검색엔진에 기사가 노출되는 경우가 많은데, 마케터는 이러한 설정을 하게 되면, 자사 웹사이트에서 보도자료에 언급된 기사 링크를 자동으로 걸 수 있으므로, 유용하게 사용될 수 있습니다.&#x20;

## 사용 예&#x20;

### Template Code

```
 [[--ScriptStart--]]
  var result = $H.http('https://openapi.naver.com/v1/search/news.json', {
  type: 'GET',
  headers: {
 'X-Naver-Client-Id' : 'Client ID',
 'X-Naver-Client-Secret' : 'Client Secret Key'
},
  data: {

      query : '[[--ArtKeyword--]]' //액션태그로 현재 게시글에 키워드 값을 쿼리로 넘깁니다


},
});
var list = JSON.parse(result);

print('<h6 class="padding-30px-top ">관련 기사</h6>')

//반복문으로 JSON의 데이터를 출력합니다 
list.items.forEach(function(node){

var date = new Date(node.pubDate); // 날짜 형식 변환
const formatDate = date.getFullYear() +"-"+ (date.getMonth() + 1)  + "-" + date.getDate() ;

 print('<div><a href="'+node.link+'">['+ formatDate +'] '+node.title +'</a></div>');
});
[[--ScriptEnd--]]
```

### Result

관련 기사

&#x20;\[2021-10-28] 아이온컴즈, 미주 최대 IT 전시회 'MWC 로스엔젤레스 2021' 참가&#x20;

\[2021-10-27] 아이온커뮤니케이션즈, 미주 최대 IT 전시회 'MWC Los Angeles 2021' 참가&#x20;

\[2021-10-27] 아이온컴즈, 미주 최대 IT 전시회 참가&#x20;

\[2021-10-27] 아이온커뮤니케이션즈, 'MWC 로스엔젤레스' 참가&#x20;

\[2021-10-27] 아이온커뮤니케이션즈, 미주 최대 IT 전시회 MWC LA 2021에 참가&#x20;

\[2021-6-30] 아이온커뮤니케이션즈, 'MWC 2021' 오프라인 전시 참가&#x20;

\[2021-6-30] 아이온커뮤니케이션즈, 'MWC 2021' 참가&#x20;

\[2021-6-30] 아이온커뮤니케이션즈, MWC 2021 바르셀로나에 참가&#x20;

\[2021-6-29] 아이온컴즈, 세계 최대 IT 전시회 참가&#x20;

\[2021-6-29] 아이온커뮤니케이션즈, '모바일월드콩그레스 바르셀로나' 참가



### 예 URL

[https://isd.i-on.net/new/gst/restapi\_\_/exam\_01.html](https://isd.i-on.net/new/gst/restapi\_\_/exam\_01.html)
