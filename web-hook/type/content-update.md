# Content Update Web Hook

ICS 내에서 지정된 특정 카테고리 콘텐츠 등록 및 수정이 발생되었을 때, 이벤트를 발생하는 Web Hook 입니다.

![](<../../.gitbook/assets/스크린샷 2021-12-02 오전 9.56.02 (1).png>)

업데이트 콘텐츠에 관련하여 Web Hook으로 제공할수 있는 정보는 다음과 같습니다.

catID, artID ,modSerno, artSubject,artCont ,Operday,expireDay, thumbnail, regUserId, creDate,modDate,keyword 입니다.

ICS를 통해서 제공하는 배포된 콘텐츠 서비스에서는 별도의 검색엔진 솔루션이 필요합니다. 검색엔진은 ICS 내에서 제공하고 있는 콘텐츠에 대해서 검색 인덱싱 작업이 필요합니다. 이때 기존에는 프로시저를 호출할 수 있도록 열어주거나, 인덱싱을 위한 별도의 파일을 제공하였으나, web Hook을 통해서 이벤트가 발생할 경우, 검색엔진 측에 색인을 요청하는 용도 등으로 활용할 수 있습니다.

### 응용 사례

Slack과 같은 외부 메신져 서비스에 API를 통해 web hook 정보를 보내어 이벤트 정보를 메신저로 수신하도록 하는 것도 가능합니다.

![](<../../.gitbook/assets/스크린샷 2021-11-11 오후 3.54.19.png>)
