# Main Visual by location

## 개요&#x20;

![](../../.gitbook/assets/fireshot\_01.png)

&#x20;Web Browser에 접속한 사용자의 GPS 정보를 기준으로 Main Visual 영역을 동적으로 보여주는 구성입니다.  위치정보별로 Main Visual의 변화를 알아볼수 있도록 하기 위해, 지도 API를 활용하여, 위치를 선택하도록 하였습니다.  실제 사용에서는 지도 노출 부분을 제거하시고 사용하시길 바랍니다.&#x20;

GPS정보를 수신하더라도 , 수신된 GPS의 지역정보를 가져오기 위해서 외부 서비스를 이용해야 합니다. 본 예제의 구현을 위해 사용된 외부 서비스 API 의 정보는 아래와 같습니다. 관련 URL을 참고해주시길 바랍니다 .

GPS 좌표로 행정구역 정보 받아오기 : [https://developers.kakao.com/docs/latest/ko/local/dev-guide#coord-to-district](https://developers.kakao.com/docs/latest/ko/local/dev-guide#coord-to-district)&#x20;

더불어, 해당 서비스 이용에 필요한  API Service Key도 발행하여 사용하여야 합니다.

ICS내에서는 행정구역 정보와 매칭되는 콘텐츠를 동적으로 제공하기 위해 Dynamic Service를 이용하였습니다.  제공된 예제는 콘텐츠 등록시, "af\_region(string type)" 필드에 국내 시도 행정명칭 및 콘텐츠(이미지, 타이틀, 설명)를 등록하고, 접속자의 행정구역에 따라 다이나믹하게 보여지도록 만든 예제입니다.&#x20;

## 참고 URL

[https://isd.i-on.net/new/ac/sample02/exam\_01.html](https://isd.i-on.net/new/ac/sample02/exam\_01.html)



## Component 구성

### 기본정보&#x20;

Basic Action Component

popup width : 600, popup height : 500&#x20;

Option , width : 100%



### 필드설정&#x20;

필드는 다음 총 5가지로 추가되어 있습니다.&#x20;

1.  카테고리(ics\_category)

    다이나믹으로 호출할 사이트 카테고리를 선택하는 필드입니다. 조건에 매칭되었을 때 가져올 아티클이 있는 사이트 카테고리를 선택하도록 합니다.
2.  listnum

    조건에 매칭된 콘텐츠의 갯수를 가져오는 필드입니다. 현재는 1건을 매칭되어야 하기 때문에 "1"로 등록되어있습니다.
3.  search&#x20;

    데이터를 가져올떄, 검색에 따른 조건으로 선별되어야 할때 필드의 값을 입력합니다. 현재는 설정값 없이 공란으로 두었습니다.
4.  sort

    데이터를 가져올때, 정렬 조건을 설정할 수 있습니다. 현재는 설정값 없이 공란으로 두었습니다.
5.  template (숨김상자)&#x20;

    다이나믹에서 결과를 가져왔을 때, 보여질 다이나믹 서비스의 결과 템플릿을 아래의 소스와 같이 숨김파일로 등록되었습니다.  마케터가 템플릿을 수정할수 있다면, "숨김상자"를 하지 않고, "긴 입력상자"를 선택하여 팝업창에서 소스 코드를 수정하도록 하면 되지만, 마케터가 수정이 불가능하다면, 파트너사가 필드를 숨김상자로 만들어 해당 템플릿 소스를 등록할 수 있습니다.

```html
<section v-for="(node, index) in nodes" class="p-0 parallax mobile-height" data-parallax-background-ratio="0.5" :style="'background-image: url(' + node.thumbnail + ');background-position: 50% -150px;'">
  <div class="container position-relative">
    <div class="row">
      <div class="col-12 col-lg-5 col-md-6 col-sm-8 full-screen md-h-650px sm-h-450px d-flex flex-column justify-content-center wow animate__fadeIn">
        <span class="text-extra-medium alt-font font-weight-500 text-uppercase text-olivine-green d-block margin-35px-bottom xs-margin-15px-bottom">여행추천</span>
        <h1 class="alt-font font-weight-700 text-dark-charcoal text-uppercase margin-2-half-rem-bottom letter-spacing-minus-2px sm-margin-20px-bottom xs-margin-15px-bottom" style="color:#FFFFFF;text-shadow: 0 0 50px rgba(0, 0, 0, 0.9);">
          {{node.artsubject}}</h1>
        <p class="text-extra-medium line-height-30px w-75 margin-3-rem-bottom lg-w-90 md-w-100 xs-margin-15px-bottom" style="color:#FFFFFF;text-shadow: 0 0 50px rgba(0, 0, 0, 0.9);">{{node.artcont}}</p>
        <a :href="node.af_link" class="btn btn-fancy btn-large btn-olivine-green section-link align-self-start">More</a>
      </div>
    </div>
    <div class="down-section text-center z-index-1 xs-bottom-30px d-none d-sm-inline-block"><a href="#about" class="section-link"><i class="fas fa-arrow-down text-dark-charcoal bg-white box-shadow-extra-large w-45px h-45px line-height-46px border-radius-100"></i></a></div>
  </div>
</section>
```



### vue.js

#### Sample Data

```json
{
    "ics_category": {
        "catId": "sck_03020000",
        "catNm": "Sample2",
        "catPath": "ICS7 New Features>Action Component>Sample2"
    },
    "listnum": "1",
    "search": "",
    "sort": "",
    "template": "<section v-for=\"(node, index) in nodes\" class=\"p-0 parallax mobile-height\" data-parallax-background-ratio=\"0.5\" :style=\"'background-image: url(' + node.thumbnail + ');background-position: 50% -150px;'\">\n  <div class=\"container position-relative\">\n    <div class=\"row\">\n      <div class=\"col-12 col-lg-5 col-md-6 col-sm-8 full-screen md-h-650px sm-h-450px d-flex flex-column justify-content-center wow animate__fadeIn\">\n        <span class=\"text-extra-medium alt-font font-weight-500 text-uppercase text-olivine-green d-block margin-35px-bottom xs-margin-15px-bottom\">여행추천</span>\n        <h1 class=\"alt-font font-weight-700 text-dark-charcoal text-uppercase margin-2-half-rem-bottom letter-spacing-minus-2px sm-margin-20px-bottom xs-margin-15px-bottom\" style=\"color:#FFFFFF;text-shadow: 0 0 50px rgba(0, 0, 0, 0.9);\">\n          {{node.artsubject}}</h1>\n        <p class=\"text-extra-medium line-height-30px w-75 margin-3-rem-bottom lg-w-90 md-w-100 xs-margin-15px-bottom\" style=\"color:#FFFFFF;text-shadow: 0 0 50px rgba(0, 0, 0, 0.9);\">{{node.artcont}}</p>\n        <a :href=\"node.af_link\" class=\"btn btn-fancy btn-large btn-olivine-green section-link align-self-start\">More</a>\n      </div>\n    </div>\n    <div class=\"down-section text-center z-index-1 xs-bottom-30px d-none d-sm-inline-block\"><a href=\"#about\" class=\"section-link\"><i class=\"fas fa-arrow-down text-dark-charcoal bg-white box-shadow-extra-large w-45px h-45px line-height-46px border-radius-100\"></i></a></div>\n  </div>\n</section>",
    "accId": "sample",
    "accNm": "Sample Action Component",
    "accWidth": "100",
    "accWUnit": "%",
    "accHeight": ""
}
```

#### Template

```typescript
<div class="container-fluid">
  <div class="row justify-content-center">
    <div class="col-md-12 text-center margin-five-bottom">
        <span class="alt-font font-weight-500 text-fast-blue d-block margin-5px-bottom text-uppercase">Basic Component</span>
      <h6 class="alt-font text-extra-dark-gray font-weight-500">{{accNm}}</h6>
    </div>
  </div>
</div>

<!-- Dynamic Service를 호출할수 있는 Div tag를 설정하고, vue에서 필요한 데이터를 넘겨서 처리된 결과를 출력합니다. --> 
<div id="dynamicData" v-html="template" :catid="ics_category.catId" :search="search" :sort="sort" :listnum="listnum" below="true" catids="" fields=""/>
```



### JS

#### Add External javascript (CDN Links)

//dapi.kakao.com/v2/maps/sdk.js?appkey=(API service Key)\&libraries=services



#### Javscript

```javascript
var check = ACmptUtil.vueArticle('dynamicData');
var mapContainer = document.getElementById('map'), // 지도를 표시할 div
mapOption = {
center: new kakao.maps.LatLng(37.566826, 126.9786567), // 지도의 중심좌표
level: 1 // 지도의 확대 레벨
};

// 지도를 생성합니다
var map = new kakao.maps.Map(mapContainer, mapOption);

// HTML5의 geolocation으로 사용할 수 있는지 확인합니다
if (navigator.geolocation) {

// GeoLocation을 이용해서 접속 위치를 얻어옵니다
navigator.geolocation.getCurrentPosition(function(position) {

lat = position.coords.latitude;    // 위도
lon = position.coords.longitude; // 경도

var locPosition = new daum.maps.LatLng(lat, lon), // 마커가 표시될 위치를 geolocation으로 얻어온 좌표로 생성합니다
message = '<div style="padding:5px;width:220px;">'+ lat + ' / ' + lon +'</div>'; // 인포윈도우에 표시될 내용입니다

  searchDetailAddrFromCoords(locPosition, function(result, status) {

    if (status === kakao.maps.services.Status.OK) {
      selectRegion.innerHTML = result[0].address.region_1depth_name;
      var message = !!result[0].road_address ? '<div>도로명주소 : ' + result[0].road_address.address_name + '</div>' : '';
      message += '<div>지번 주소 : ' + result[0].address.address_name + '</div>';

      var content = '<div class="bAddr">' +
              '<span class="title">법정동 주소정보</span>' +
              message +
              '</div>';

     /**  // 마커를 클릭한 위치에 표시합니다
      marker.setPosition(locPosition); 
      marker.setMap(map);

      // 인포윈도우에 클릭한 위치에 대한 법정동 상세 주소정보를 표시합니다
      infowindow.setContent(content);
      infowindow.open(map, marker);
      **/

      //클릭 이후에 검색값을 반영하여 다이나믹을 한번 더 호출합니다.
      var _key =  $('.selectRegion').html();
      //alert(_key);
      check.search('af_region='+_key);
    }
  });

// 마커와 인포윈도우를 표시합니다
displayMarker(locPosition, message);

var idGap = document.getElementById("digit");
//idGap.innerHTML = "위도 : "+ lat +" , 경도 : " + lon;
});

} else { // HTML5의 GeoLocation을 사용할 수 없을때 마커 표시 위치와 인포윈도우 내용을 설정합니다

var locPosition = new daum.maps.LatLng(33.450701, 126.570667),
message = 'geolocation을 사용할수 없어요..'

displayMarker(locPosition, message);
}

// 지도에 마커와 인포윈도우를 표시하는 함수입니다
function displayMarker(locPosition, message) {

  // 마커를 생성합니다
  var marker = new daum.maps.Marker({
  map: map,
  position: locPosition
  });

  var iwContent = message, // 인포윈도우에 표시할 내용
  iwRemoveable = true;

  // 인포윈도우를 생성합니다
  var infowindow = new daum.maps.InfoWindow({
  content : iwContent,
  removable : iwRemoveable
  });

  // 인포윈도우를 마커위에 표시합니다
  infowindow.open(map, marker);

  // 지도 중심좌표를 접속위치로 변경합니다
  map.setCenter(locPosition);
}

// 주소-좌표 변환 객체를 생성합니다
var geocoder = new kakao.maps.services.Geocoder();

var marker = new kakao.maps.Marker(), // 클릭한 위치를 표시할 마커입니다
infowindow = new kakao.maps.InfoWindow({zindex:1}); // 클릭한 위치에 대한 주소를 표시할 인포윈도우입니다

// 현재 지도 중심좌표로 주소를 검색해서 지도 좌측 상단에 표시합니다
searchAddrFromCoords(map.getCenter(), displayCenterInfo);


// 지도를 클릭했을 때 클릭 위치 좌표에 대한 주소정보를 표시하도록 이벤트를 등록합니다
kakao.maps.event.addListener(map, 'click', function(mouseEvent) {
searchDetailAddrFromCoords(mouseEvent.latLng, function(result, status) {

if (status === kakao.maps.services.Status.OK) {
selectRegion.innerHTML = result[0].address.region_1depth_name;
var detailAddr = !!result[0].road_address ? '<div>도로명주소 : ' + result[0].road_address.address_name + '</div>' : '';
detailAddr += '<div>지번 주소 : ' + result[0].address.address_name + '</div>';

var content = '<div class="bAddr">' +
  '<span class="title">법정동 주소정보</span>' +
  detailAddr +
  '</div>';

    // 마커를 클릭한 위치에 표시합니다
    marker.setPosition(mouseEvent.latLng);
    marker.setMap(map);

    // 인포윈도우에 클릭한 위치에 대한 법정동 상세 주소정보를 표시합니다
    infowindow.setContent(content);
    infowindow.open(map, marker);

    //클릭 이후에 검색값을 반영하여 다이나믹을 한번 더 호출합니다.
    var _key =  $('.selectRegion').html();
    //alert(_key);
    check.search('af_region='+_key);
}
});
});

// 중심 좌표나 확대 수준이 변경됐을 때 지도 중심 좌표에 대한 주소 정보를 표시하도록 이벤트를 등록합니다
kakao.maps.event.addListener(map, 'idle', function() {
searchAddrFromCoords(map.getCenter(), displayCenterInfo);
});

function searchAddrFromCoords(coords, callback) {
  // 좌표로 행정동 주소 정보를 요청합니다
  geocoder.coord2RegionCode(coords.getLng(), coords.getLat(), callback);
}

function searchDetailAddrFromCoords(coords, callback) {
  // 좌표로 법정동 상세 주소 정보를 요청합니다
  geocoder.coord2Address(coords.getLng(), coords.getLat(), callback);
}


// 지도 좌측상단에 지도 중심좌표에 대한 주소정보를 표출하는 함수입니다
function displayCenterInfo(result, status) {
  if (status === kakao.maps.services.Status.OK) {
  var infoDiv = document.getElementById('centerAddr');

    for(var i = 0; i < result.length; i++) {
    // 행정동의 region_type 값은 'H' 이므로
      if (result[i].region_type === 'H') {
      infoDiv.innerHTML = result[i].address_name;
      break;
      }
    }

  }
}

```

