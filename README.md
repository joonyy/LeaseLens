# LeaseLens

<div align="center">
<img width="200" alt="image" src="https://github.com/user-attachments/assets/dd456f7c-05d9-49e8-be45-391c75848c16">
</div>

> **가전제품 렌탈 리뷰 서비스** <br/> **개발 기간 : 2024.06.13 ~ 2024.07.04**

---

## 배포 주소
> **리스렌즈**

### 팀원
<div align="center">
<img width="500" alt="스크린샷 2024-07-04 오전 10 31 27" src="https://github.com/joonyy/LeaseLens/assets/29936443/5f7536da-5f1a-4f97-aa5a-ec46f7ed596f"></div>

## 프로젝트 소개

가전제품 구독 서비스가 확대되는 가운데, 우리 팀은 이에 대한 리뷰를 확인할 수 있는 사이트가 없다는 것을 느꼈습니다. 리스 렌즈는 가전제품 렌탈 서비스에 대한 리뷰 커뮤니티를 제공하는 웹 서비스입니다.

## 기술스택 

### Environment
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC?style=for-the-badge&logo=Visual%20Studio%20Code&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white)
![Github](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=GitHub&logoColor=white)             

### Config
![npm](https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white)        

### Development

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=Sequelize&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

### ERD

![ERD_End](https://github.com/user-attachments/assets/1439efaf-2dfe-4247-9d97-ad90068cb345)

## 화면 구성 📺
| 메인 페이지  |  로그인   |
| :-------------------------------------------: | :------------: |
|<img width="329" alt="image" src="https://github.com/joonyy/LeaseLens/assets/29936443/30309f75-9e73-4f1d-a095-e94881c7c981">| |
|리뷰 인증 |리뷰 글 작성 |
|   <img width="329" alt="스크린샷 2024-07-04 오전 10 55 17" src="https://github.com/joonyy/LeaseLens/assets/29936443/d31b71b2-57a1-4036-afcd-e68cc490544a"> | <img width="329" alt="스크린샷 2024-07-04 오전 11 06 12" src="https://github.com/joonyy/LeaseLens/assets/29936443/38603821-2621-49c4-b575-da4af55d9ffa"> |  
| 리뷰 검색   |  찜하기  |  
| <img width="329" alt="스크린샷 2024-07-04 오전 11 25 44" src="https://github.com/joonyy/LeaseLens/assets/29936443/e6850186-e866-4a4b-83dc-fc0ec5dd5996">|<img width="329" alt="image" src="https://github.com/joonyy/LeaseLens/assets/29936443/cef10a14-e194-4397-91cb-d0807c8bb2b4">|


## 주요 기능

### 리뷰 인증

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



- 제품 테이블의 prod_likes 속성을 프론트에 전달.
  - 좋아요 버튼 클릭 시, 찜 테이블에 값이 추가가 된다.
- sequelize 검색 기능을 통해, 유저의 마이페이지에서 찜한 제품을 찾아준다.
- 찜이 되어있는 제품이었을 경우 찜 해제 및 찜 테이블에 값 삭제, 아닐 경우 찜 추가 및 찜 테이블에 값 추가

---
## 아키텍쳐

### 디렉토리 구조
```bash
backend
├── .gitignore
├── README.md
└── backend
    ├── .env
    ├── .env.development
    ├── .env.production
    ├── Middlewares
    │   ├── error404.js
    │   ├── handleError.js
    │   ├── isAdmin.js
    │   ├── isLoggedIn.js
    │   └── isNotLoggedIn.js
    ├── app.js
    ├── config
    │   ├── adminSetup.js
    │   └── config.js
    ├── controller
    │   ├── adminReviewController.js
    │   ├── productController.js
    │   ├── renderController.js
    │   ├── reviewController.js
    │   └── userController.js
    ├── models
    │   ├── comment.js
    │   ├── favorite.js
    │   ├── index.js
    │   ├── product.js
    │   ├── review.js
    │   └── user.js
    ├── package-lock.json
    ├── package.json
    ├── passport
    │   ├── index.js
    │   └── local.js
    ├── routes
    │   ├── adminReviewRouter.js
    │   ├── index.js
    │   ├── productRouter.js
    │   ├── renderRouter.js
    │   ├── reviewRouter.js
    │   └── userRouter.js
    ├── seeders
    │   └── insertProducts.js
    └── uploads
        └── reviews
```
