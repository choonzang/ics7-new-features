---
description: Content Hub 만 가능
---

# $H.execUpdate()

외부DB에 접근하여 쿼리한 데이터를  삭제, 또는 추가, 업데이트를  위해서 아이온커뮤니케이션즈에서 지원하는 객체 $H.execUpdate()입니다.&#x20;

접속정보를 직접 입력하는 방식이 아니라, "ICS > Operation Manager > Content Hub > 연동DB정보"에 DB의 계정 정보를 입력하게 되면, connection ID(connId)를 생성할 수 있으며, 그 ID 를 이용하여 Query하는 방식입니다.

데이터 업데이트 또는 삭제와 같은 처리를 하나의 트랜잭션에서 여러 건의 데이터를 처리하거나, 여러 건의 트랜잭션을 순차적으로 처리할 경우에 사용할 수 있습니다.&#x20;

데이터의 변경이 발생하는 부분이므로, 실행 시 충분한 검증이 필요합니다.&#x20;

## 사용 예&#x20;

### code

```xml
<c:script targetKey="xx1"><![CDATA[
$H.execUpdate({
        connId : 'scott',
        query : [{
            sql : 'Delete from EMP where empno in ( 797, 796, 798, 799  )',
        },{
            sql : 'Insert into EMP (empno, ename, job, mgr, hiredate, sal, comm, deptNo) values (:empno, :ename, :job, :mgr, sysdate, :sal, :comm, :deptNo)',
            param : [{ 
                empno: 798, 
                ename: 'NOVI2', 
                job: {type:'string', value:'NONO'}, 
                mgr: {type:'int', value:'7839'}, 
                sal: {type:'int', value:'600'}, 
                comm: {type:'int', value:'500'}, 
                deptNo: {type:'int', value:'20'} 
            },
            { 
                empno: 799, 
                ename: 'NOVI3', 
                job: {type:'string', value:'NONO'}, 
                mgr: {type:'int', value:'7839'}, 
                sal: {type:'int', value:'600'}, 
                comm: {type:'int', value:'500'}, 
                deptNo: {type:'int', value:'20'} 
            }]
        }]
    });


var result= $H.db({
        connId : 'scott',
        query : 'Select empno, ename, job, mgr, hiredate, sal, comm, deptNo from EMP Where deptNo = 20'
    });

var list = JSON.parse(result); 

return list.rows;
]]></c:script>

<c:out sourceKey="xx1"/>
```
