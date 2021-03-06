# 템플릿 생성

이미 사이트를 구성했을 경우, 부분적으로 반영된 템플릿을 업데이트 하기 위해  하나의 카테고리를 기준으로 한개 이상의 템플릿을 등록할 수 있습니다.&#x20;

이 경우, 사이트 매니저 > 사이트 카테고리 > 템플릿 > '승인완료 템플릿' 메뉴에서 Quick Builder를 통해 하나 또는 다수의 템플릿을 한꺼번에 등록이 가능합니다. 만약, 이미 한번 퀵빌더를 통해 템플릿을 등록하였더라도, 동일한 파일명으로 등록한다면, 버전이 올라간 상태로 기존 템플릿에 업데이트니다.

아래의 절차대로 생성해보세요.



### 사이트 매니저 > 사이트 카테고리 > 템플릿&#x20;

템플릿을 등록하고자 하는 카테고리에서 승인완료 템플릿 탭으로 이동합니다. 그리고, "퀵빌더(Quick Builder)" 버튼을 클릭합니다.



### Quick Builder 팝업창&#x20;

앞서 준비한 Template 묶음로 구성된 Zip 파일을 첨부합니다. 또는 한건의 파일인 경우, Zip으로 묶지 않고 그대로 첨부합니다.&#x20;

템플릿 내에 상대경로 또는 절대경로 상에 Resource 또는 다른 템플릿이 ICS에 존재한다면, Template 내의 경로는 변환되어 등록됩니다.&#x20;



### Template 확장자 &#x20;

Template 으로 등록이 가능한 확장자는 ICS에서 이미 정의된 소스 타입 이외에 다른 확장자는 지원하지 않습니다.



### 옵션 선택&#x20;

커스텀택 추출 : 템플릿 내에 미리 정의된 태그를 읽어들여 커스텀택으로 추출할 것인지를 선택합니다.&#x20;

커스텀택 업데이트 : 이미 한번 추출된 커스텀태그가 ICS 내에 있다면, 이번 등록 파일의 내용으로 업데이트할 것인지를 선택합니다.

커스텀택 그룹 선택 : 추출한 커스텀택을 어느 그룹에 포함하여 저장할 것인지를 지정합니다.

{% hint style="info" %}
커스텀택 업데이트를 체크할 경우, 기존에 추출된 커스텀택의 버전이 올라간 상태로 업데이트 됩니다. 업데이트 여부를 반드시 체크하시길 바랍니다.&#x20;
{% endhint %}



### 실행

첨부된 파일을  읽어들이면서 템플릿을 생성합니다.



