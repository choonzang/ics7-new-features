# 정렬하기

외부 요건에 따라 데이터의 정렬을 해야 하는 경우에 Script Tag를 활용할 수 있습니다.

아티클의 조회수를 구현하는 경우, 대부분 ICS가 아닌 다른 시스템에서 보관이 이루어 집니다. 다만, 아티클의 데이터는 ICS에 있기 때문에 조회수를 기준으로 한 정렬을 원하는 경우, 조회수 데이터를 정렬하여, 아티클 아이디를 가져와야 합니다.

이때, Script tag 에서는 외부 시스템의 조회수를 정렬하여 아이클 아이디 리스트를 가져오고, 아티클 데이터 (아이디, 제목, 내용 등)과 일치하는 정보를 출력하여 조회수에 따른 리스트를 출합니다.

## 사용 예

### Template Code

```javascript
[[--ScriptStart--]]
try{
  var result = $H.http('https://(Service Id).restdb.io/rest/hit-count', {
  type: 'GET',
  "async": true,
  "crossDomain": true,
  headers: {
    "content-type": "application/json",
	"x-apikey": "(Service API Key)",
    "cache-control": "no-cache"
},
  data: {
	"sort": "hit_cnt",
	"dir":"-1"
},
});
var list = JSON.parse(result);

const articles = [
[[--ActionStart,sck_03030000,row:*--]]
[[--ARTJSON,pretty:false,COMMA:true,EXCEPT:keyword;modday;catid;content--]]
[[--ActionEnd--]]
];

print(JSON.stringify(list));
print('<br/><br/><br/>');
print(JSON.stringify(articles));
print('<br/><br/><br/>');

list.forEach(function(node){
	print(node.mapId +'; 조회수('+node.hit_cnt+');');
	var result = articles.filter(x => x.artid === node.mapId).map(x => x.subject);
	print(result + '<br/><br/><br/>');
});

} catch(error) {
	print(error)
}
[[--ScriptEnd--]]
```

### Result

\[{"\_id":"61944687d4fd1466000244b0","mapId":1185982,"hit\_cnt":200,"s\_catId":"sck\_03030000"},{"\_id":"619446cad4fd1466000244bb","mapId":1185999,"hit\_cnt":102,"s\_catId":"sck\_03030000"},{"\_id":"619446dad4fd1466000244bd","mapId":1186000,"hit\_cnt":89,"s\_catId":"sck\_03030000"},{"\_id":"61944666d4fd1466000244a5","mapId":1185976,"hit\_cnt":46,"s\_catId":"sck\_03030000"},{"\_id":"619446a5d4fd1466000244b4","mapId":1185983,"hit\_cnt":42,"s\_catId":"sck\_03030000"},{"\_id":"61944677d4fd1466000244aa","mapId":1185978,"hit\_cnt":39,"s\_catId":"sck\_03030000"},{"\_id":"619446b5d4fd1466000244b9","mapId":1185998,"hit\_cnt":21,"s\_catId":"sck\_03030000"},{"\_id":"619445f4d4fd14660002448f","mapId":1185974,"hit\_cnt":21,"s\_catId":"sck\_03030000"},{"\_id":"61944638d4fd146600024497","mapId":1185975,"hit\_cnt":12,"s\_catId":"sck\_03030000"},{"\_id":"6194464ad4fd14660002449e","mapId":1185976,"hit\_cnt":5,"s\_catId":"sck\_03030000"},{"\_id":"619446e9d4fd1466000244c0","mapId":1186001,"hit\_cnt":1,"s\_catId":"sck\_03030000"}]

\[{"artid":1186001,"subject":"fdsfffdsfdsfsfsf","creday":"20211112-144126","thumbnail":""},{"artid":1186000,"subject":"\[News] I-ON Communications selected for 2021 Global Jump 300 and Export Voucher Program for expanding overseas business.","creday":"20211111-171639","thumbnail":""},{"artid":1185999,"subject":" Key Factors to a Productive IT Work Culture","creday":"20211111-171542","thumbnail":""},{"artid":1185998,"subject":" The Next Normal: Evolvement of Artificial Intelligence","creday":"20211111-171455","thumbnail":""},{"artid":1185983,"subject":"The Big Deal in Digital Innovation","creday":"20211101-102337","thumbnail":""},{"artid":1185982,"subject":"I-ON Communications to Attend Mobile World Congress 2021","creday":"20211101-102251","thumbnail":""},{"artid":1185978,"subject":"I-ON participates in 1:1 online business meetings with overseas buyers and investors","creday":"20211027-113555","thumbnail":"/choonzang/publish/res.do?type=thumb\&res=/2021/10/27/GettyImages-1244481806.jpeg"},{"artid":1185977,"subject":" \[Column] E-commerce is growing. So should your business!","creday":"20211027-113508","thumbnail":""},{"artid":1185976,"subject":"I-ON Communications to release Contact Share","creday":"20211027-113431","thumbnail":"/choonzang/publish/res.do?type=thumb\&res=/2021/10/27/CS\_news.jpeg"},{"artid":1185975,"subject":"I-ON Communications resumes to stretch its global business after pause due to Coronavirus Pandemic","creday":"20211027-113320","thumbnail":"/choonzang/publish/res.do?type=thumb\&res=/2021/10/27/GettyImages-1179837602\_1.jpeg"},{"artid":1185974,"subject":"I-ON Communications to participate at GMV 2020","creday":"20211022-115155","thumbnail":"/choonzang/publish/res.do?type=thumb\&res=/2021/10/22/gmv\_20200512\_135322.png"}]

1185982; 조회수(200); I-ON Communications to Attend Mobile World Congress 2021

1185999; 조회수(102); Key Factors to a Productive IT Work Culture

1186000; 조회수(89); \[News] I-ON Communications selected for 2021 Global Jump 300 and Export Voucher Program for expanding overseas business.

1185976; 조회수(46); I-ON Communications to release Contact Share

1185983; 조회수(42); The Big Deal in Digital Innovation

1185978; 조회수(39); I-ON participates in 1:1 online business meetings with overseas buyers and investors

1185998; 조회수(21); The Next Normal: Evolvement of Artificial Intelligence

1185974; 조회수(21); I-ON Communications to participate at GMV 2020

1185975; 조회수(12); I-ON Communications resumes to stretch its global business after pause due to Coronavirus Pandemic

1185976; 조회수(5); I-ON Communications to release Contact Share

1186001; 조회수(1); fdsfffdsfdsfsfsf

## 샘플 URL

[https://isd.i-on.net/new/gst/sort/exam\_01.html](https://isd.i-on.net/new/gst/sort/exam\_01.html)
