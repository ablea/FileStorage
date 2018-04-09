---

copyright:
  years: 2014, 2017
lastupdated: "2017-12-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 확장 가능한 파일 공유 용량

이 새 기능을 통해 현재 {{site.data.keyword.filestorage_full}} 사용자는 상황에 따라 복제를 작성하거나 수동으로 데이터를 더 큰 볼륨으로 마이그레이션하지 않고도 최대 12TB까지 기존 {{site.data.keyword.filestorage_short}}의 크기를 GB 증분 단위로 확장할 수 있습니다. 크기를 조정하는 동안 스토리지에 대한 액세스가 제한되거나 중단되지 않습니다.  

볼륨에 대한 청구는 현재 청구 주기에는 비례 배분된 새 가격의 차이만큼 추가하도록 자동으로 업데이트된 후 다음 청구 주기에 완전히 새 금액으로 청구됩니다. 

이 기능은 [엄선된 데이터 센터](new-ibm-block-and-file-storage-location-and-features.html)에서만 사용할 수 있습니다.  

## 확장 가능한 파일 공유의 이점이 생기는 이유는 무엇입니까?

- **비용 관리** – 데이터의 확장 가능성이 있지만, 시작할 때는 작은 크기의 스토리지여야 한다는 점을 알고 있습니다. 확장 능력을 갖추면 고객은 시작할 때 스토리지 비용을 절감하고 이후에 필요한 크기를 수용하도록 성장할 수 있습니다.   

- **스토리지 확장 요구** - 빠른 확장을 경험한 고객은 이러한 확장을 관리하기 위해 스토리지 크기를 쉽고 빠르게 늘리는 방법이 필요합니다. 

## 스토리지 크기 조정은 복제에 어떤 영향을 줍니까?

기본 스토리지에서 확장 조치를 수행하면 복제본의 크기도 자동으로 조정됩니다. 

## 제한사항이 있습니까?

이 기능은 향상된 기능으로 [데이터 센터](new-ibm-block-and-file-storage-location-and-features.html)에서 프로비저닝된 스토리지에서만 사용 가능합니다. 이 데이터 센터에서 프로비저닝된 암호화된 스토리지는 최대 12TB까지 늘어날 수 있습니다.  

Endurance로 프로비저닝된 {{site.data.keyword.filestorage_short}}의 기존 크기 제한사항이 계속 적용됩니다(10 IOPS 티어의 경우 최대 4TB, 기타 모든 티어의 경우 최대 12TB). 

## 내 프로비저닝된 스토리지가 확장 가능한지 어떻게 알 수 있습니까?

향상된 성능으로 프로비저닝된 스토리지는 항상 휴면 중 암호화가 적용됩니다. 포털 UI에서 옆에 "잠금" 아이콘이 있으면 스토리지가 해당 자격이 있음을 쉽게 알 수 있습니다.  

## 내 스토리지는 어떻게 크기를 조정할 수 있습니까?

1. {{site.data.keyword.slportal}}에서 **스토리지** > **{{site.data.keyword.filestorage_short}}** 또는 {{site.data.keyword.BluSoftlayer_full}} 카탈로그에서 **인프라** > **스토리지** > **{{site.data.keyword.filestorage_short}}**를 클릭하십시오. 
2. 목록에서 볼륨을 선택하고 **조치** > **볼륨 수정**을 클릭하십시오. 
3. 새 스토리지 크기(GB)를 입력하십시오. 
4. 선택사항 및 새 가격 책정을 검토하십시오. 
5. **마스터 서비스 계약을 읽었습니다...** 선택란을 클릭하고 **주문하기**를 클릭하십시오. 
6. 새 스토리지 할당은 몇 분 안에 사용 가능해야 합니다. 
