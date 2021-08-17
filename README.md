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

## 3. 사용 api   
- Kakao login api   
- Naver login api   
- Naver sens api   
- Google chart api   
- Channeltalk api   
- SpeechSynthesis    
- Naver papago api   
- Elastic search api   
- Kakao map api   
- 카카오 알림톡 api   
- Kakao pay api


## 4. ERD 설계   
![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8b4cf2f7-ee1b-4145-99b2-efddf1de533a%2Ffinal.png?id=64d8e210-4e19-43f1-b85c-9673b1d94ac0&table=block&spaceId=02035cac-9dbb-4a33-9431-b4b67098f6ba&width=2840&userId=7b670629-fe67-41bb-a78d-7cbf6af5b506&cache=v2)   
</br></br>

## 5. 담당 기능   

-	**채팅**   
1)	채널톡 API를 사용하여 관리자(상담사)와의 채팅 기능 구현   
2)	Websocket을 활용하여 회원 간 1대1채팅 기능을 구현   
3)	speechSynthesis api를 사용하여 텍스트 음성번역 
-	**SNS 로그인**   
1) 카카오, 네이버 아이디로 로그인(kakao login api, naver login api)   
2) sns로그인 정보를 회원가입 폼으로 전달   
-	**게시판**   
1) 리뷰 게시판 crud   
2) 클래스, 상품 메인 페이지(페이징, 검색)   
    
</br></br>
## 6. 트러블 슈팅
### 6.1. 
- 클래스/상품/리뷰 리스트의 페이징 기능을 구현하는 과정에서 특정 데이터들이 누락되는 문제가 발생하여 이를 각 게시판의 용도에 맞게 해결하고자 하였습니다.   
- 기존의 방식 :  리스트 페이지에서 클래스/상품/리뷰 테이블과 파일 테이블을 조인하여 썸네일로 각 게시글에 맞는 사진 파일을 띄워주고자 하였습니다. 해당 부분 쿼리문은 inner join을 사용하여 작성하였는데 사진 파일 없이 텍스트로만 등록된 데이터들이 리스트에서 누락되는 문제가 발생하였고 이를 해결하기 위해 두 가지 단계를 고려하였습니다.
   
  - **'1. 페이지의 용도'**   
   ->  클래스/상품 페이지의 경우, 해당 클래스와 상품의 판매 용도로 만들어진 페이지이기 때문에 사용자 편의를 위해 사진 파일이 필수적으로 포함되어야 한다고 판단하였습니다.   
   ->  리뷰 페이지의 경우 사용자가 특정 클래스, 상품을 사용한 후기(텍스트)에 중점을 둔 페이지이기 때문에 사진 파일은 부가적인 부분이라 판단하였습니다.   
  - **'2. 용도에 맞는 해결 방안'**   
   ->  클래스/상품 페이지는 기존 쿼리문은 수정하지 않고, 클래스/상품 등록 시에 파일을 업로드 하지 않으면 등록이 불가능하도록 설정하였습니다.   
   ->  리뷰 페이지는 텍스트로만 작성이 된 데이터가 리스트에서 누락되지 않고 출력되도록 쿼리문을 수정하였습니다. 리뷰 번호를 기준으로 inner join을 사용하였던 부분을 left outer join 방식으로 변경하여, 파일테이블에 등록된 사진이 없더라도 모든 리뷰 데이터가 출력되도록 구현하였습니다.


