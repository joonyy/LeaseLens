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
<img width="500" alt="스크린샷 2024-07-04 오전 10 31 27" src="https://github.com/joonyy/LeaseLens/assets/29936443/5f7536da-5f1a-4f97-aa5a-ec46f7ed596f">
</div>

## 프로젝트 소개

가전제품 구독 서비스가 확대되는 가운데, 우리 팀은 이에 대한 리뷰를 확인할 수 있는 사이트가 없다는 것을 느꼈습니다. 리스 렌즈는 가전제품 렌탈 서비스에 대한 리뷰 커뮤니티를 제공하는 웹 서비스입니다. 리스 렌즈에서는 특정 가전제품별로 찜하기, 리뷰 작성하기 등의 기능을 제공하며, 리뷰 인증 기능을 통해 제품을 정말로 사용해본 사용자가 작성한 리뷰인지 확인할 수 있습니다.
[leaselens.pdf](https://github.com/user-attachments/files/16215797/leaselens.pdf)

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


## 화면 구성
| 메인 페이지  |  로그인   |
| :-------------------------------------------: | :------------: |
|<img width="329" alt="image" src="https://github.com/joonyy/LeaseLens/assets/29936443/30309f75-9e73-4f1d-a095-e94881c7c981">|<img width="329" alt="image" src="https://github.com/user-attachments/assets/9b773926-1a9f-4e32-994d-87f4efecee6a"> |
|리뷰 인증 |리뷰 글 작성 |
|   <img width="329" alt="스크린샷 2024-07-04 오전 10 55 17" src="https://github.com/joonyy/LeaseLens/assets/29936443/d31b71b2-57a1-4036-afcd-e68cc490544a"> | <img width="329" alt="스크린샷 2024-07-04 오전 11 06 12" src="https://github.com/joonyy/LeaseLens/assets/29936443/38603821-2621-49c4-b575-da4af55d9ffa"> |  
| 리뷰 검색   |  찜하기  |  
| <img width="329" alt="스크린샷 2024-07-04 오전 11 25 44" src="https://github.com/joonyy/LeaseLens/assets/29936443/e6850186-e866-4a4b-83dc-fc0ec5dd5996">|<img width="329" alt="image" src="https://github.com/joonyy/LeaseLens/assets/29936443/cef10a14-e194-4397-91cb-d0807c8bb2b4">|


## 주요 기능

### 리뷰 인증

> 인증 된 리뷰 선별 을 위해 렌탈 영수증이나 인증 가능한 이미지 파일로 신뢰성 있는 리뷰 커뮤니티 구현

> 계정은 "사용자"와 "관리자" 로 구분하는 속성 'role'을 통해 관리.

- 사용자가 제품에 해당하는 리뷰를 작성합니다.
- 작성된 리뷰에는 반드시 구매 영수증이 첨부되어야만 업로드가 가능합니다.
- 업로드된 이미지는 "관리자" 계정으로 동일 페이지에 접속했을 때 확인할 수 있습니다. 이 때, 관리자가 승인을 해준다면 사용자들에게 "인증된 리뷰글"임을 나타내는 체크박스가 나타납니다.

- 관리자 계정은 최초 서버 실행 시에 자동으로 생성하며, middleware를 통해 로직을 구현했습니다. 여기엔 중복 생성 방지 기능도 포함되어 있습니다.
  
### 리뷰 글 작성

> 사용자는 본인이 사용한 제품에 대해 리뷰 글을 작성함.


1. 필수 필드 검증 : 리뷰 제목, 제품 선택 여부, 리뷰 본문, 제품 평점, 인증 이미지 등 필수 입력 데이터가 모두 제공되었는지 검증
   - 업로드한 게시물 사진은 글작성창(react-quill) 내부에 보여야 하므로, 프론트 서버에 업로드하는 방식으로 구현.
   - 필수 필드가 누락된 경우 이미지 파일 삭제
     
2. S3 업로드
   - 모든 상태를 체크 후 이미지 파일들을 AWS S3에 업로드
   - 로컬 파일을 삭제하여 서버의 저장 공간을 효율적으로 관리함.
  
5. 리뷰 데이터베이스 저장
   - 검증된 데이터 기반으로 새로운 리뷰 생성하여 데이터베이스에 저장
   - 리뷰 생성 시, 생성 일시와 사용자 인덱스 등 함께 저장

### 검색
> 내가 원하는 제품이 있는지, 혹은 내가 보고싶은 리뷰 글의 키워드가 있다면 검색할 수 있습니다.

- category를 query문으로 전달받아, 전송해주는 기능.
  - req.query.category를 통해 검색어를 전달받는다.
  - 검색 조건(conditon)을 설정해준다. 
  - 조건에 해당하는 요소들을 database에서 가져온다.
- product 검색
  -  sequelize 문법으로 검색, 결과값을 배열의 형태로 전송
- review 글 검색
  - 작성일 기준으로 내림차순 정렬을 하여, 최신 리뷰가 상단에 오도록 함.
 

### 찜하기
> 원하는 제품을 찜해두고, "마이 페이지"에서 모아볼 수 있습니다.

- 제품 테이블의 prod_likes 속성을 프론트에 전달.
  - 좋아요 버튼 클릭 시, 찜 테이블에 값이 추가가 된다.
- sequelize 검색 기능을 통해, 유저의 마이페이지에서 찜한 제품을 찾아준다.
- 찜이 되어있는 제품이었을 경우 찜 해제 및 찜 테이블에 값 삭제, 아닐 경우 찜 추가 및 찜 테이블에 값 추가

---
## 아키텍쳐

### 디렉토리 구조
```bash
LeaseLens
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
