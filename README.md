Java OOP Project
gitlab에서 private로진행 
프로젝트 진행 인원 총 3명

[2020-04-27]
— Slarayman vo
SalaryMan 변수 turn 및 생성자 추가
— SalaryManserviceImpl.java
Turn 체크용 IsFinished 함수 추가
False 변환용 setFalse 추가

— Test.java
turn-> turns으로 변수변경
while위에 for 추가
엔딩 추가
Menu 끝내기-> 턴끝내기로 변경

[2020-04-28] - 이규환
- v3 업데이트
- SalaryManServiceTest.java 
- 5~9번 명령 부분 업데이트
- 5번 ssn 값을 받아서 ArrayList<SalaryMan> 로 return
- 6번 hp 값 오름차순으로 정렬하여 보여주기(player에 현재 생명력을 직관적으로 확인할수있게)
- 7번 salary 값을 내림차순으로 정렬 (승리에 가장 가까운 회사원을 직관적으로 확인할수있게)
- 8번 기존에 승진을 월급협상으로 이름변경 
    ssn 값으로 인원을 선택하여 랜덤한값만큼 salary가 상승한다.
- 9번 기존 삭제 구문에서 변경점 없음(ssn값으로 확인) 

SalaryManServiceImpl.java
동작순서
 ArrayList<SalaryMan> searchHP() ->  class HpComparator ->  ArrayList<SalaryMan> searchHP()
 ArrayList<SalaryMan> searchSalary() -> class SalComparator ->  ArrayList<SalaryMan> searchSalary()
 class HpComparator, class SalComparator : 정렬 발생
 
 
 [2020-4-28 (2)]
 v4를 업로드함
 
 주요 수정사항
 - SalaryMan 필드 ssn -> empNo로 변경, 이와 관련된 메소드, 인자명 변경
 - work, nightwork, vacation 수정, 통일 후 Test 클래스 관련 사항(case 2,3,4) 수정
 - test 클래스 메뉴 순서 변경 (4번 야근-> 3번, 3번 휴가-> 4번)
 
[2020-4-28 17:05]

 주요 수정사항
 - 1억을 모으지 않아도 성공엔딩으로 끝나는 오류 수정
 - 주민번호-> 사원번호로 개념 수정
 
[2020-4-28 17:51] 

 주요 수정사항
 - 연봉협상시 턴수 true로 변경 
 
 

[2020-5-04 22:52] 

 주요 수정사항
 - 사원 추가시 턴 수가 넘어가던 것 수정
 - 
 

[2020-05-05 01:30]-이규환

 주요수정사항
 
 *인터페이스*
 
  - addSalaryMabService 인자값 변경 : (int, String, int)->(String, int)
  - updateSalaryMan 인자값 변경 : int -> SalaryMan
  - getSalaryMan, searchHP, searchSalary 속성변경 : SalaryMan -> void
 
 *서비스*
 
 - addSalaryMan : 생성을 할 때 사원번호 자동으로 입력되는 코드 추가 
     - if(sm.getEmpNo() == ssn) => if(sm.getName().equals(name))
     - sms.add(new Major(ssn, name) => sms.add(new Major(sms.size()+1, name))
     - sms.add(new Small(ssn, name)) => sms.add(new Small(sms.size()+1, name))


 - getSalaryMan : empNo-1 에 리스트 값을 받도록 변경
 
 - searchHP : 실행시겼을떄 보이는 값을 성명과 HP만 보이게 변경
              HP가 가장 낮은 사람 출력(test에 내용을 서비스로 변경)

 - searchSalary : searchHP와 똑같이 보이는 값 변경 승리에 가까운 사람 출력
 
 - updateSalaryMan : work, nightwork 처럼 개체를 받아서 임금 협상 할수있도록 변경
 
 - deleteSalaryMan : 삭제 후에 사원번호를 초기화 시키는 코드 추가
 
 - 정렬 클래스들을  SalaryManServiceImpl 클래스 밖으로 위치변경

 *테스트*
 
 - 이름변경 -> 7번 : 랭킹보기 , 8번 : 월급협상 
 - 회사원 추가하기할떄 (회사선택, 이름) 입력
 

[2020-05-05 21:08]  v9 업로드

주요 수정사항

< 서비스 >
- updateSalaryMan(월급협상 메소드) 오류 수정: 
    사원번호로 선택된 회사원의 월급여 변경 메세지만 출력되도록 if문과 break 추가, 
    월급여 변경 후 turn을 true로 변경

    <- 수정 전에는 선택되지 않은 회사원들도 for문이 돌면서 월급여 변경 메세지가 화면에 계속 출력됨 / 월급협상 후에도 턴 종료되지 않음

- deleteSalaryMan()에서 특정 회사원 삭제 이후 삭제 확인 출력문 추가


< 테스트 >

- work()와 vacation의 getInfo -> workInfo()로 수정

- 화면에 출력되는 문구들 약간씩 수정


[2020-05-05 22:43] 

 주요 수정사항
- 사원이 존재하지 않을시 추가를 제외한 선택지 진입 못하게 수정
- 월급협상시 아예 게임이 멈춰버리는 것 수정
- 10번째에서 아예 게임이 끝나던 것 수정
  
