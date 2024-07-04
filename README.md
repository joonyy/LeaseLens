# LeaseLens
가전제품 렌탈 리뷰 서비스

<div style="display:flex">
<img width="500" alt="스크린샷 2024-07-04 오전 10 14 52" src="https://github.com/joonyy/LeaseLens/assets/29936443/30309f75-9e73-4f1d-a095-e94881c7c981"> <img width="500" alt="스크린샷 2024-07-04 오전 10 25 28" src="https://github.com/joonyy/LeaseLens/assets/29936443/5114716f-d18b-4106-982c-b5622e26dd28">  
</div>

### 팀원
<img width="500" alt="스크린샷 2024-07-04 오전 10 31 27" src="https://github.com/joonyy/LeaseLens/assets/29936443/5f7536da-5f1a-4f97-aa5a-ec46f7ed596f">

### 아이디어 선정 배경
- 1인 가구가 현재 총 가구의 31.2%를 차지하면서 증가하고 있는 추세로 가전제품 구입 초기비용을 확실하게 줄이고, 케어십 서비스도 별도 비용 부담 없이 받을 수 있는 가전 구독 서비스 수요가 늘어나고 있다.
- 실제로 LG전자의 사업 보고서에 따르면 2023년 가전 구독 매출은 약 9638억 원으로 2022년보다 31.1% 증가했다. 5년 이후에는 4배 이상 성장할 것으로 전망된다.
- 가전 구독 서비스는 제품의 대여 사용 후에 구매를 결정한다는 점에서 불필요한 소비를 줄이고, 최근 일부 대형할인마트에서도 대형가전제품에 대한 렌탈서비스를 실시할 만큼 서비스 영역이 커지고 있는 상황으로 소비자들의 선호도가 증가하고 있다.
- 제품 구매 시 리뷰 검색을 대부분 진행하며, 리뷰가 구매 결정에 영향을 주는 부분이 확실히 존재한다.

<img width="500" alt="스크린샷 2024-07-04 오전 10 38 12" src="https://github.com/joonyy/LeaseLens/assets/29936443/9b552d6f-6440-4d1b-94a9-0e7e7d21b595">
<img width="500" alt="스크린샷 2024-07-04 오전 10 38 34" src="https://github.com/joonyy/LeaseLens/assets/29936443/c368445c-1895-4cdb-8c07-0de8f7517642">

### 기술스택

프론트엔드 : React, TypeScript

백엔드 : node.js, express

데이터베이스 : MySQL

배포 : AWS EC2, AWS RDS

기타 : Axios, AWS S3, sequelize

소통 및 개발환경 : slack, notion, Figma, Github, vsCode

### ERD

<img width="500" alt="개념 모델링" src="https://github.com/joonyy/LeaseLens/assets/29936443/059de493-692a-4963-8844-cf6da512cc9f">

<img width="500" alt="물리 모델링" src="https://github.com/joonyy/LeaseLens/assets/29936443/b970fde1-1852-4c7f-87c5-2478429ed5ac">


## 주요 기능

### 리뷰 인증
 <img width="344" alt="스크린샷 2024-07-04 오전 10 55 17" src="https://github.com/joonyy/LeaseLens/assets/29936443/d31b71b2-57a1-4036-afcd-e68cc490544a">

- 인증 된 리뷰 선별 을 위해 렌탈 영수증이나 인증 가능한 이미지 파일로 신뢰성 있는 리뷰 커뮤니티 구현
- 일반 사용자 계정 & 관리자 계정을 구분
 
- 일반 사용자
  - 리뷰 글 확인 가능
  - 리뷰에 댓글 달기 가능

- 관리자
  - 리뷰 댓글 대신 렌탈 인증 사진 확인
  - 인증 여부 체크 후 인증 완료
  - 일반 사용자의 커뮤니티에 인증 표시 나타남
    
### 리뷰 글 작성
<img width="500" alt="스크린샷 2024-07-04 오전 11 06 12" src="https://github.com/joonyy/LeaseLens/assets/29936443/38603821-2621-49c4-b575-da4af55d9ffa">


- 파일 업로드 처리 : 사용자가 업로드 한 이미지 파일을 서버로 전송받아 처리
- 필수 필드 검증 : 리뷰 제목(rev_title), 제품 인덱스(prod_idx), 리뷰 텍스트(rev_text), 평점(rev_rating), 인증 이미지(rev_authImg)들의 필수 입력 데이터가 모두 제공되었는지 검증
  - 필수 필드가 누락된 경우 로컬 이미지 파일 삭제 
- 사용자 인증
  - 사용자 로그인 상태 체크
  - 비로그인 상태에서 리뷰를 작성할 수 없으며, 로컬 이미지 파일 삭제
- S3 업로드
  - 모든 상태를 체크 후 이미지 파일들을 AWS S3에 업로드
  - 로컬 파일을 삭제하여 서버의 저장 공간을 효율적으로 관리
- 리뷰 데이터베이스 저장
  - 검증된 데이터 기반으로 새로운 리뷰 생성하여 데이터베이스에 저장
  - 리뷰 생성 시, 생성 일시와 사용자 인덱스 등 함께 저장

### 검색
- category를 query문으로 전달받아, 전송해주는 기능.
  - req.query.category를 통해 검색어를 전달받는다.
  - 검색 조건(conditon)을 설정해준다. 
  - 조건에 해당하는 요소들을 database에서 가져온다.
- product 페이지
  -  sequelize 문법으로 검색, 결과값을 배열의 형태로 전송
- review 페이지
  - 작성일 기준으로 내림차순 정렬을 하여, 최신 리뷰가 상단에 오도록 함.
 
### 찜하기
