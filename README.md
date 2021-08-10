# :pushpin: OnedayTwoday
>원데이 클래스 및 상품을 제공하는 웹사이트    
>기획안 링크 : [Click](https://www.notion.so/Onedaytwoday-cadf7591883243848126075e990368ba "notion link")   

### 프로젝트 전체 기능     

<details>
<summary><b>전체 기능 설명 펼치기</b></summary>
<div markdown="1"> </br>  
   1. 로그인/회원가입 – sns로그인, 개인정보 암호화, 회원가입, 문자인증 기능   </br></br>    
   2. 관리자 - 회원, 상품, 클래스, 이벤트 관리 기능   </br></br>    
   3. 결제 - 클래스, 상품 결제, 장바구니 기능   </br></br>    
   4. 게시판 - 리뷰, 이벤트, 상품, 클래스, 공지사항 게시판   </br></br>    
   7. 채팅 - 관리자와의 채팅, 회원/ 강사 1대1 채팅, 텍스트 음성번역, 타 언어로 번역, 채팅 저장   </br></br>    
   8. 지도 - 클래스 위치 제공 기능   </br></br>    
   9. 알림 - 할인정보, 로그인내역(IP)등 정보 알림 기능   </br></br>    
   10. 검색 - 자동완성, 실시간 검색어 순위 기능   </br></br>    

</div>
</details>
</br>

## 1. 제작 기간 & 참여 인원
- 21.06.28 ~ 21.08.01 
- TEAM : 5명(남민혁, 곽수정, 심희주, 안재온, 김정규)  

</br>

## 2. 사용 기술
#### `Back-end`
  - <img src="https://img.shields.io/badge/11-Java-red"/> 
  - <img src="https://img.shields.io/badge/Mybatis-grey"/>
  - <img src="https://img.shields.io/badge/11-Oracle-yellow"/>
  - <img src="https://img.shields.io/badge/5.8.1-Spring-green"/>
 
#### `Front-end`
  - <img src="https://img.shields.io/badge/Javacript-red"/>
  - <img src="https://img.shields.io/badge/html/css-orange"/>

</br>
## 4. 사용 api   
Kakao login api   
Naver login api   
Naver sens api   
Google chart api   
Channeltalk api   
SpeechSynthesis 
Naver papago api   
Elastic search api   
Kakao map api   
카카오 알림톡 api   
Kakao pay api


## 3. ERD 설계   
![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8b4cf2f7-ee1b-4145-99b2-efddf1de533a%2Ffinal.png?id=64d8e210-4e19-43f1-b85c-9673b1d94ac0&table=block&spaceId=02035cac-9dbb-4a33-9431-b4b67098f6ba&width=2840&userId=7b670629-fe67-41bb-a78d-7cbf6af5b506&cache=v2)   
</br></br>

## 4. 담당 기능   

-	**병원, 여행일정 게시판**   
1)	병원 : 데이터베이스에 등록된 병원에 화상상담을 예약할 수 있도록 구현.   
2)	여행일정 : 지도기능을 활용하여 여행일정을 작성하고 마이페이지에서 조회하도록 구현.   
-	**지도**   
   키워드 검색을 통한 원하는 장소의 상세페이지 조회 / 장소들 간의 거리, 이동시간 조회 / 데이터베이스에 등록된 장소를 마커로 표시하여 위치조회, 상세정보 조회   
-	**나와 닮은 동물 찾기**   
    머신러닝 기능을 활용하여 닮은 동물상을 출력해주는 기능.   
    
</br></br>
## 5. 트러블 슈팅
### 5.1. 지도 api와 데이터베이스 연결
- 지도에서 특정 버튼을 클릭할 시, 데이터베이스에 등록된 업체(병원 및 가게)들을 지도 상에 마커로 표시하여 사용자가 한 눈에 확인할 수 있도록 구현하고자 하였습니다. 해당 기능을 구현하기 위해 세 가지 질문에 관한 해결 방안을 생각해보았습니다.   
   
  - **'도로명 주소, 업체명이 담긴 리스트에서 어떻게 하나씩 가져와 뿌려줄 수 있을까'**   
   ->  각 업체의 정보 리스트를 가져와 반복문을 사용하여 JSON 객체에 도로명주소, 업체명을 하나씩 담아주고, 이를 JSON배열에 담아서 보내주는 방식으로 해결하였습니다.  
  - **'사용한 api에선 주소의 위도 및 경도 정보가 필요한데 도로명 주소를 어떤 방법으로 변환해야 할까'**   
   -> 도로명주소를 위도, 경도 좌표로 변환해주는 라이브러리(daum.maps.services)를 사용하여 변환해주었습니다.   
  - **'ajax 사용여부'**   
   -> 페이지를 새로 로딩하여 지도를 다시 띄우는 방법보단, 이미 띄워진 지도에 사용자가 원할 경우 업체 리스트가 마커로 표시되도록 구현하고자 하였습니다. 이는 ajax를 사용하여 업체 리스트 데이터만 받아와 지도에 표시하는 것으로 해결하였습니다.

