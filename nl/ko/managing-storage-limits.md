---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 스토리지 한계 관리

기본적으로, 글로벌하게 250개 {{site.data.keyword.blockstorageshort}} 볼륨의 통합 총계를 프로비저닝할 수 있습니다. 

[{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window}에서 티켓을 제출하여 한계 늘리기를 요청할 수 있습니다. 요청이 승인되면 특정 데이터 센터에 대해 설정된 볼륨 한계를 받습니다.   

한계 늘리기를 요청하려면 티켓을 열고 이를 영업 담당자에게 보내십시오. 

티켓에서 다음 정보를 제공하십시오.

- **티켓 제목**: 데이터 센터 볼륨 개수 스토리지 한계 늘리기 요청

- **추가 볼륨 요청에 대한 유스 케이스는 무엇입니까?** <br />
*이에 대한 답변은 새 VMware 데이터 저장소, 새 개발 및 테스트 환경, SQL 데이터베이스 또는 로깅 등일 수 있습니다. *

- **유형, 크기, IOPS 및 위치별로 필요한 추가 블록 볼륨의 수는 얼마입니까?** <br />
*예를 들어, 답변은 "DAL09의 25x Endurance 2TB @ 4IOPS" 또는 "WDC04의 25x Performance 4TB @ 2IOPS"와 유사한 것일 수 있습니다.*

- **유형, 크기, IOPS 및 위치별로 필요한 추가 파일 볼륨의 수는 얼마입니까?** <br />
*예를 들어, 답변은 "DAL09의 25x Performance 20GB @ 10IOPS" 또는 "SJC03의 50x Endurance 2TB @ 0.25IOPS"와 유사한 것일 수 있습니다.*
 
- **요청된 모든 볼륨 늘리기의 프로비저닝에 대한 예상/계획 시점을 제공하십시오.** <br />
 "*예를 들어, 답변은 "90일"과 유사한 것일 수 있습니다.*

- **이러한 볼륨의 예상된 평균 용량 사용량의 90일 예측치를 제공하십시오.** <br />
*이에 대한 답변은 "30일에 25퍼센트 이용, 60일에 50퍼센트 이용 및 90일에 75퍼센트 이용이 예상됨" 등일 수 있습니다. *

위의 모든 질문에 반드시 응답해야 합니다. 사용자는 티켓 프로세스를 통해 한계에 대한 업데이트의 알림을 받습니다. 
