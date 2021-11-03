# 주의사항

### 배포지연 주의

Graal Script 를 통해서 외부 시스템 접근 후, 데이터를 받아오는 과정에서 지연이 발생될 경우, ICS에서의 배포 과정의 지연으로 연결됩니다. 이로인해 배포가 느려질 수 있습니다.  외부 시스템 접근하여 데이터를 가져오는 스크립트에서는 이 부분을 참고해주시길 바랍니다.



### 클라이언트 기반 이벤트 미지원&#x20;

Graal Script에서는 최종 처리된 결과를 출력하는 태그 형태이므로, 클라이언트의 이벤트에 대한 동작에 따라 결과를 반영하는 구조에서는 적합하지 않습니다.
