# Open API로 기사정보 가져오기

Open API를 활용하여, 서비스에 필요한 콘텐츠를 획득할 수 있습니다.&#x20;

네이버 Developer의 검색 > 뉴스에 대한 안내 입니다. 아래의 URL을 참고하셔서, Header와 Data를 통해 조회된 값을 이용할 수 있습니다.&#x20;

참고 URL : [https://developers.naver.com/docs/serviceapi/search/news/news.md#%EB%89%B4%EC%8A%A4](https://developers.naver.com/docs/serviceapi/search/news/news.md#%EB%89%B4%EC%8A%A4)&#x20;

## 사용 예

### Template Code

```
[[--ScriptStart--]]

  var result = $H.http('https://openapi.naver.com/v1/search/news.json', {
  type: 'GET',
  headers: {
      'X-Naver-Client-Id' : 'Clinet ID', // Client ID를 발급받아서 입력합니다 
      'X-Naver-Client-Secret' : 'Client Secret Key' //Secret Key를 발급받아서 입력합니다 
},
  data: {
      query : '아이온커뮤니케이션즈', //검색어를 지정 합니다
      display : '10', // 출력건
      sort : sim //정렬기준으로 sim(유사도순), date(날짜순)  
},
});
var list = JSON.parse(result);

list.items.forEach(function(node){
  print(node.title + node. pubDate+'<br/><br/>')
});

[[--ScriptEnd--]]
```

### Result

**아이온**컴즈, 미주 최대 IT 전시회 'MWC 로스엔젤레스 2021' 참가Thu, 28 Oct 2021 10:16:00 +0900\
\
**아이온커뮤니케이션즈**, 미주 최대 IT 전시회 'MWC Los Angeles 2021' 참가Wed, 27 Oct 2021 18:14:00 +0900\
\
**아이온**컴즈, 미주 최대 IT 전시회 참가Wed, 27 Oct 2021 18:00:00 +0900\
\
**아이온커뮤니케이션즈**, 'MWC 로스엔젤레스' 참가Wed, 27 Oct 2021 17:30:00 +0900\
\
**아이온커뮤니케이션즈**, 미주 최대 IT 전시회 MWC LA 2021에 참가Wed, 27 Oct 2021 17:20:00 +0900\
\
**아이온커뮤니케이션즈**, 미국에 스포츠 영상 분석 시스템 선봬Mon, 25 Oct 2021 08:28:00 +0900\
\
**아이온커뮤니케이션즈**, 미국 허브풋볼캠프에 스포츠영상 분석 시스템 제공Fri, 22 Oct 2021 13:14:00 +0900\
\
**아이온커뮤니케이션즈**, 美 허브 풋볼 캠프에 영상 분석 시스템 제공Thu, 21 Oct 2021 20:07:00 +0900\
\
**아이온**컴즈, 美 허브 풋볼 캠프서 스포츠 영상 분석 시스템 선봬Thu, 21 Oct 2021 19:46:00 +0900\
\
'한-베 ICT 비즈니스 파트너십', 하노이서 개최...25\~11월5일, 온오프라인으로Thu, 21 Oct 2021 15:56:00 +0900



### 참고 URL

[https://isd.i-on.net/new/gst/restapi/exam\_03.html](https://isd.i-on.net/new/gst/restapi/exam\_03.html)
