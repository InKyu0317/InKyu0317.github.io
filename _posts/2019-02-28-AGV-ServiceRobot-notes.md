---
layout: page
title: AGV & service Robot research note
---

### Research note about AGV and service robot

## 물류로봇 개요
- 일반인들이 물류로봇하면 떠올릴 아마존의 키바
- 2012년도 아마존은 키바를 인수하면서 아마존을 제외한 다른 회사들은 키바를 이용할수 없게된다. http://clomag.co.kr/article/2281
- 아마존 로보틱스: https://www.amazonrobotics.com/#/

## 키바 이후 물류로봇
- AGV 기술변화와 방향
  - 1세대: Good To Man 방식 (단순히 고정된 위치에 작업자(Picker)에게 물품전달)
  - 1.5세대: 충전방식의 변화로 생산성 향상 (이동 중 충전) 독일 쿠카로보틱스 자회사 Swisslog 의 Carry Pick
  - 2세대: 허용무게 및 최대속도의 향상 Clearpath Otto 1500
  - 향후:
    - 아마존이 피킹 첼린지를 매년 개최하는 이유는 작은 패키지들을 가급적 많이 처리하기 때문이다.
    - AI를 활용하여 물류 관련 방대한 양의 데이터를 수집·검토하고, 운용·관리방안을 제시함으로써 물류로봇 활용의 효율성을 제고할 것으로 보인다.
  - 최근에는 물류로봇의 형태가 다양해지고, 공급자 수가 늘었으며, 번뜩이는 아이디어로 무장한 스타트업의 시장 참여도
   확대되는 등 물류로봇의 공급환경이 대폭 개선

- http://m.irobotnews.com/news/articleView.html?idxno=10319

- 로커스 로보틱스 (Locus Robotics)
  - 콰이어트 로지스틱스에서 분사
  - 콰이어트 로지스틱스 납품, 작업자들의 이동거리 22.53km -> 8.04km 단축
  - 국제 배송 전문업체 DHL에 로커스봇을 납품

- 6리버시스템즈 (6RS)
  - 전 키바시스템즈 직원 4명이서 설립 
  - Chuck 높이 조정 가능, 터치스크린 (담아야할 물품 이미지, ID, 작업자 이동 방향등 표시)
  - 인간-로봇 협업형(센서 및 SW를 통해 테이터 추적, 작업자에게 피드백 제공)

- 페치 로보틱스
  - ROS개발을 주도했던 'Willow Garage' 출신, 멜로니 와이즈(Melonee Wise)가 CEO
  - 프레이트 500과 프레이트 1500 (소형~대형) 수요에 따른 제품 라인업

 ## 물류로봇 활용
- RGV(Rail Guided Vehicle): 레일이나 유도선을 따라 이동하거나 비전 유도 및 위치 추적기술 기반 으로 이동한다. 자동화된 창고 혹은 생산 공정)
- LGV(Laser Guided Vehicle): 레이저에 의해 유도, 완전 자율주행과 다수의 AGV 운용 가능
- http://www.hellot.net/new_hellot/magazine/magazine_read.html?code=204&sub=002&idx=41444
- 물류이송에서 활용되는 방식:
  - Good To Man: AGV가 고정된 자리에 있는 작업자(Picker) 앞으로 물품을 이송
  - AGV가 작업자(Picker)를 따라다니는 형태
  - Picking(매니플레이터 장착) AGV
  - Picking 로봇과 AGV가 쌍으로 구성

## AGV의 유도방식
- 유선유도
  - 자기유도: 바닥의 부착된 자석 이용, 비용저렴, 자기장에 민감
  - 전자기유도: 유도선or전기선의 전자기 이용, 외란적음, 매설비용
  - 광학유도: 컬러orSUS 테이프 인식, 테이프 손상이 쉬움 
- 무선유도
  - 레이저유도: 반사체를 레이저로 계측, 정밀도 높음, 자율주행및 다수 운반차 운영, 초기제작비용 높음
  - 천장유도: 적외선 카메라로 천장 인공표식 인식, 정밀도낮음, 작업장 높이
  - 자기/자이로유도: 자기위치측정 및 자이로센서 이용, 여러 자석 배치, 복잡한 시스템
  - 환경인지: 추가공사없음, 물체인식센서, 거리연산, 경로수정, 설치간편

## 제품개발 및 상용화 동향
- 공장물류용은 최근 자율주행 AGV 활용, 로봇팔을 이용한 중량물 적재/하역 가능해짐. 
- 물류창고용은 피킹 기능에 초점이 맞춰져있고 현재 많은 개발을 진행중이다.
- 국내의 경우 자율주행, 피커추종, 다중로봇 운영 최적화, 로봇관제시스템 연동 등의 기능을 가지는 물류로봇은 아직까지 기술개발 및 시험단계에 있다.
- 일반옥내용은 주로 대형건물에 활용되는데 병원 내 자율주행 AGV는 사업화가 이미 진행중이다. 예) 유진로봇(을지대병원), 세브란스병원
- 옥외배달용은 최근 일부 배송(택배)용 자율주행 AGV 개발 완료, 전자상거래, 유통업체, 푸드 체인 등에서 시험 운용중 예) 우아한형제들
- 물류로봇 업계 기술력 및 시장 확보를 위해 M&A 제휴/협력 활발히 진행중, 렌털 (RaaS) 방식도 적극 개발 추진중에 있다.

## 글로벌시장
- IFR (국제로봇연맹) 조사 발표 http://www.etnews.com/20180917000233
- 다양한 기관의 예상 자료 (한국로봇산업진흥원)
  <br>비제조업용(물류창고용, 병원, 제고정리 등), 제조업용(공장물류용) 이 판매량이 가장 많다.

## 국내시장
- 물류) 한화(기계부문), 칼텍, 한성웰텍, 엔스퀘어 등 다수기업이 물류센터/창고를 위한 자동화 솔루션 사업화
- 물류) CJ대한통운 종합물류연구원에서 자율주행 물류로봇(최대 500㎏, 1m/s)을 개발(전자부품연구원/KAIST/엔스퀘어 공동개발)해 물류센터에서 시험 중
- 물류) 마로로봇테크는 QR 코드 인식형 물류로봇 MR.Logi, 포테닛은 자율주행 기술기반의 제품 판매
- 물류) 포테닛: 레이저 스캐너 방식 자율주행 P-AGV, 오래된 지게차->자율주행지게차, 카카오인베스트&두산인프라 투자
- 물류) 코어벨: 팔레트에 구분 적재, 한컴MDS에서 인수 https://www.youtube.com/watch?v=SDPjuQ6r4c4
- 제조) 이노텍: 자체 특허기술을 바탕으로 H/W 및 S/W를 모두 제공하는 토털솔루션 구축, 롤러형, 리프트형, 컨베이어형, 무한궤도형, 체인형, 견인형 등 다양한 제품 출시 ,연간 매출액은 150억원 이상으로 국내 선두업체 중 하나 (브랜드명 : 나르미) (한국로봇산업진흥원), http://www.innotech20.com/bbs/board.php?bo_table=03_02
- 옥내) 파나소닉의 AMR HOSPI-R: 병원 및 호텔 24시간 가동, 자동충전, 쇼핑카트 견인 14kg 자율주행, 사람추종 기능 https://news.panasonic.com/global/topics/2015/44009.html
- 옥내) 유진로봇: 신경철 유진로봇 회장은 올 하반기부터 물류로봇 ‘고가트’를 국내외 병원, 공장, 호텔 등에 진출시켜 주력 사업으로 키우겠다고 밝혔다 유진로봇의 핵심 기술은 디슬램(D-Slam)과 티오에프 센서(ToF sensor), 로콘(ROCON), 다중로봇 제어 http://www.zdnet.co.kr/view/?no=20180517160346
- 개인적사견) 우리가 LiDAR를 달고 자율주행의 기술을 필두로 물류로봇을 기획하고자 한다면 유진로봇처럼 유연한 물류로봇을 벤치마킹할 필요가 있다고 느낀다. (자율주행에서 LIDAR 는 필수는 아니이기 때문에, 하지만 좋은 자율주행 성능-> LIDAR)
- 유진로봇 3d LIDAR (CES 2019 에서 전시): http://www.yujinrobot.com/lidar/
- 물류) 유도: 우리나라 물류센터는 아마존이나 징동 물류센터와 크기도 다르고 적재 높이도 다르다. 물류로봇은 활용공간의 최적화 되어서 설계되어야 하는것을 잘 보여준다. http://clomag.co.kr/article/3054
- 창간 5주년 기획]물류로봇 발전 방안 좌담회(1)] http://www.irobotnews.com/news/articleView.html?idxno=14112
  - 공장들이 소품종 대량생산에서 다품종 소량생산으로 가면서 AGV, 물류로봇 도입이 더욱 중요해지고있다.
  - 물류 로봇 사업을 하면서 힘들었던점:
    - 공장 바닥이 경사가 있었을때
    - 지게차가 레일을 다 망가트려버림 (국내 물류창고는 지게차와+사람 구조)
- 국내 물류창고는 90%가 중소물류창고이다. 하지만 물류로봇을 도입할떄 가장튼 걸림돌은 '비용'과 '운영' http://clomag.co.kr/article/2281, (한국로봇산업진흥원)
- 물류 로봇 제조는 80% 이상 북미에서 생산, 국내 물류로봇업체 부품 수입의존도 높음 (한국로봇산업진흥원)
- 예) 'invia robotics' 소개 RaaS 방식으로 로봇을 렌트해주면 (중소기업입장에서) 좋지 않을까? https://www.inviarobotics.com/product-overview http://clomag.co.kr/article/2183
- 사용자는 피킹 1회당 약 30센트를 지불하는 것으로 인비아로보틱스의 물류로봇 서비스를 제공받을 수 있다. 참고로 글로벌 평균 수준의 피킹 원가는 회당 약 80센트 수준이다.


## 국내 물류로봇 기술동향 및 전망

- 국내는 공장물류용 AGV 기술개발에 집중, 설계 및 조립은 국산화가 된 반면 핵심부품 및 기술은 여전히 해외에 의존
- 물류창고용 로봇은 피킹 시스템을 지속적으로 개발하여야 한다.
    - 입출고 무인화 기술, 로봇 시스템의 기술, DAS(Digital assorting system) 등에 대한 기술은 진전
    - 자동 Dock Leveler 개발 미비
    - 자율주행 수준 높여야된다.
- 옥내용 (병원 및 대형건물) 물류로봇은 자율주행 뿐만 아닌 엘레베이터와의 연동같은 부분을 더욱 개발,  24시간 가동 능력을 갖추어야한다

## 서비스로봇 동향
- 서비스로봇: 병원, 호텔, 식당 등 서비스업계에서 다양한 직종을 담당하는 로봇들
- 최근 시장동향:
  - 서비스 로봇 시장 2025년 천억 달러 예상 http://www.kidd.co.kr/news/202821
    - 의료 로봇 시장 규모는 17년도 17억 달러에서 2025년 134억 달러로 7.8배 성장할 걸로 예측
    - 접객/안내 로봇 시장 규모는 17년도 14억 달러(7만5천대)에서 2025년 118억 달러(91만대)로 8.4배 성장할 걸로 기대
  - http://www.businesskorea.co.kr/news/articleView.html?idxno=23660
    - 올해 시장을 선도할 분야는 제조용 로봇시스템, 의료로봇, 로봇용 구조부품 및 부분품, 로봇과학 및 기술서비스, 로봇판매서비스, 기타 전문서비스용 로봇, 로봇임대서비스 등 7개 분야로 꼽혔다
  - 서비스로봇 사업 확장하는 알리바바: http://techm.kr/bbs/board.php?bo_table=article&wr_id=5276
  - 징동 X사업부: https://platum.kr/archives/110682
  - 중국로봇시장: http://www.shanghaibang.com/shanghai/news.php?code=ne03&mode=view&num=56843
  - CES 2019 service robot: 
    - “service robots for personal and domestic use” will grow from $2.2 billion in 2015 to $22 billion by 2019. https://www.roboticsbusinessreview.com/consumer/6-service-robot-questions-ces-2019/
  - 로봇관련산업분야 다양성: https://blog.serenacapital.com/ces-2019-floor-we-are-the-robots-dbf62a8d6d6b
  - CES 2019 혁신수상: https://www.prnewswire.com/news-releases/coral-robots-inc-named-as-ces-2019-innovation-awards-honoree-300747270.html

## 재고관리 로봇
- Simbe Robotics ‘Tally’: https://www.simberobotics.com/
    - Stock Management: https://www.simberobotics.com/solutions/out-of-stock-management/
- Fellow Robotics, Navii(scan), Inventory stock Management(관리시스템), Fellowinsight(데이터 분석), Sotreview(map virtual view) : https://www.fellowrobots.com/
- Megazino, 신발상자 picking: https://www.magazino.eu/products/toru/?lang=en
- Bossa Nova Robotics: http://bossanova.com/
- 월마트:https://www.tampabay.com/business/walmart-deploying-robots-to-scan-florida-store-shelves-20190211/
- Fujitsu: http://www.irobotnews.com/news/articleView.html?idxno=10070

## 일반 옥내용
- 중국) 스마트 식당 서비스로봇: https://platum.kr/archives/111510
- 국내) 퓨처로봇(대표 송세경) : 국내 서비스로봇 전문 업체, 디지털옵틱과 깊은 관계??
 기능 및 스펙: http://www.futurerobot.com/new2/page/product02.php
 철도경찰로봇: http://www.startuptoday.co.kr/news/articleView.html?idxno=20853
 성균관대 중앙학술정보관 안내로봇: http://www.kyosu.net/news/articleView.html?idxno=43447
 미래형 이마트 의왕시 계획: https://www.msn.com/ko-kr/news/national/%EC%9D%B4%EB%A7%88%ED%8A%B8-30%EA%B0%9C%EC%9B%94%EB%A7%8C%EC%97%90-%EC%83%88-%EB%A7%A4%EC%9E%A5%E2%80%A6%EC%A2%85%EC%9D%B4-%EC%82%AC%EB%9D%BC%EC%A7%80%EA%B3%A0-ai%EB%A1%9C%EB%B4%87%EC%9D%B4-%EC%95%88%EB%82%B4/ar-BBQMfwo
- 미국) Aethon / TUG: https://aethon.com/
- 미국) SwissLog / KUKA: https://www.swisslog.com/en-us
- 미국) Savioke / Relay: http://www.savioke.com/healthcare
- 국내) 유진로봇: http://newstomato.com/ReadNews.aspx?no=805695
- 자체 라이다 센서 개발: http://www.yujinrobot.com/lidar/
- 국내) NT로봇: Sbot2-MD 병원물류운반 http://ntrobot.net/ 디지털 랜드마크 방식(천정), 무궤도 방식, 레이저 스캐너 1개, 초음파 센서 4개, 위치 인식 센서
- 일본) 알데바란 로보틱스(인수됨), 소프트뱅크 로봇도우미 '페퍼' https://ko.wikipedia.org/wiki/%ED%8E%98%ED%8D%BC_(%EB%A1%9C%EB%B4%87)
- 마이크 x 4, RGB 카메라 x 2,3D 센서 x 1, 터치 센서 x 3
- 대한민국에 들어오는 페퍼에는 LG유플러스가 자체 개발한 AI 플랫폼 탑제
- 국내) 이마트 LG전자 일라이(http://www.etnews.com/20180417000247) 후속탄 https://www.ajunews.com/view/20181105102445680
- 일본) Promobot: https://promo-bot.ai/
- 일본) moogle 'evo': https://www.daiwahouse.co.jp/robot/moogle/ 건물 내부, 지하실 이런곳 탐사로봇???

## 배달로봇
- 자율주행 기능이 더욱 특화, Lidar 의 장점이 더 두각.
- 자율주행 로봇의 눈과 귀, ‘센서’ 파헤치기: http://clomag.co.kr/article/3105
- 미국) 라이다장착한 자율주행 로봇 robby.io
- 중국) 쑤닝: https://www.thestar.com.my/news/regional/2018/07/19/in-china-yellow-delivery-robots-may-change-future-of-logistics/
- 중국) 알리바바, 라이다 네비게이션 장착: http://www.irobotnews.com/news/articleView.html?idxno=14868
- 중국) 어러머: https://pandaily.com/ele-me-delivery-robot-completed-takeout-delivery-for-the-first-time/
- 중국) 징동, 대학교 캠퍼스내 배달서비스: https://www.gizmochina.com/2017/06/19/jd-com-tests-motorized-robot-deliveries-universities/
- 국내) 우아한형제들, 베어로보틱스 인수, 푸드코트 배달로봇 '딜리': https://1boon.daum.net/bloter/308829
- 일본) ZMP: ADAS?? https://www.zmp.co.jp/en/products/carriro-creation

## 간호/돌봄/생활지원/정서지원 로봇
- 일본) 파나소닉 HOSPI: https://news.panasonic.com/global/topics/2015/44009.html
- 일본) ROBEAR: 이승 보조 및 이동지원 기술: http://www.riken.jp/en/pr/press/2015/20150223_2/
- 미국) 조지아공대 Cody: 헬스케어용 로봇, 목욕지원기술 http://pwp.gatech.edu/hrl/robotic-nurse-assistant/
- 국내) GIST 헬스케어로봇센터 연구소: http://www.etnews.com/20180608000156
- 마인렛 샤와야가 NWic: 배설보조 로봇: http://www.minelet.com/seihin-joho.html
- 실벗: 치매케어 로봇: http://robocare.co.kr/en/index.php/silbot/
- 국내) 아이로비(iRobi) 유진로봇 노인건강상태 모니터링 및 기록 로봇 http://www.yujinrobot.com/portfolio-items/irobi-q/
- 일본) 파로Paro, intelligent system: 우울증이나 고립감 시달리는 노인의 말동무 http://www.parorobots.com/
- 아이보 Aibo, Sony: 강아지 https://us.aibo.com/
- Luvozo SAM 'robotic concierge': 자율주행 기능과 자율주행을 이용한 텔레프레전스 http://luvozo.com/sam/
- 국내) 한국로봇융합연구원 KIRO-M5: 병원용품 운반, 실내공기 살균 및 탈취, 환자 기저귀 교환 시점 통보 http://www.kiro.re.kr/dev/fintro.asp?idx=16&bgbn=R
- 일본) Tapia(커뮤니케이션 로봇): https://mjirobotics.co.jp/en/
- 일본) parlo from Fujisoft: https://palro.jp/