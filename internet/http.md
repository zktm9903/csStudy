## http란?
   - http는 **Hyper Text Transfer Protocol**의 두문자어
   - *인터넷에서 데이터를 주고받을 수 있는 프로토콜(규칙)*
   - 클라이언트가 요청을 한 다음 받을 때까지 대기하는 **클라이언트-서버 모델**을 따름
   - 요청, 응답 두 요청 간에 어떠한 상태나 데이터를 유지하지 않는 **무상태 프로토콜**
   ---
     
1. 동작  
   ![http](/internet/images/http1.png)  
   클라이언트 : 서버에게 요청을 보내는 리소스 사용자  `ex) 웹 브라우저, 모바일 어플리케이션, IoT 등`  
   서버 : 클라이언트에게 요청에 대한 응답을 제공하는 리소스 관리자

   - 클라이언트가 필요한 리소스를 URL을 통해 **서버에 요청**하면 서버에서는 해당 **요청에 대한 결과를 응답**하는 형태로 동작
   - ---

   1.1 요청  
   
   요청메세지 예시  

   GET https://www.2sang.com HTTP/1.1  

   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)  
   Upgrade-Insecure-Requests: 1

   data

   - 첫 줄 
     - GET(요청 메서드) 
     - https://www.2sang.com (주소) 
     - HTTP/1.1(HTTP 버전)
   - 두 번째 줄 (header)
     - 요청에 대한 정보
   - 데이터 (마지막 부분)
     - 요청을 할 때 함께 보넬 데이터
   ---

   1.2 응답

   응답 메세지 예시

   HTTP/1.1 200 OK  
   Connection: keep-alive  
   Content-Encoding: gzip  
   Content-Length: 35653  
   Content-Type: text/html;  

   `<!DOCTYPE html><html lang="ko" data-reactroot=""><head><title...`

   - 데이터 (마지막 부분)
     - 응답으로 html을 담아 보내줌(예시)
   
   ---
   ### 알아두면 좋은 헤더들

   - **General Header(공통 헤더)**  
      *요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더*
      - Date : 현재시간
      - Pragma : 캐시제어 , HTTP/1.0에서 쓰던 것으로 HTTP/1.1에서는 Cache-Control이 쓰인다.
      - Cache-Control : 캐시를 제어할 때 사용
      - Upgrade : 프로토콜 변경시 사용
      - Via : 중계(프록시)서버의 이름, 버전, 호스트명
      - Connection : 네트워크 접속을 유지할지 말지 제어. HTTP/1.1은 kepp-alive 로 연결 유지하는게 default 값
      - Transfer-Encoding : 사용자에게 entity를 안전하게 전송하기 위해 사용하는 인코딩 형식을 지정
   - **Entity Header(엔티티 헤더)**   
      *컨텐츠 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더*
      - Content-type : 리소스의 media type 명시 
        - ex) application/json, text/html
      - Content-Length : 바이트 단위를 가지는 개체 본문의 크기
      - Content-language : 본문을 이해하는데 가장 적절한 언어
      - Content-location : 반환된 데이터 개체의 실제 위치 
        - ex) /index.html
      - Content-disposition : 응답 메세지를 브라우저가 어떻게 처리할지. 주로 다운로드에 사용
      - Content-Security-Policy : 다른 외부 파일을 불러오는 경우 차단할 리소스와 불러올 리소스 명시
         - ex) default-src https -> https로만 파일을 가져옴
         - ex) default-src 'self' -> 자기 도메인에서만 가져옴
         - ex) default-src 'none' -> 외부파일은 가져올 수 없음
      - Content-Encoding : 본문의 리소스 압축 방식. 주로 Content-Type과 같이 사용되며 참조되는 미디어 타입을 얻도록 디코드하는 방법을 클라이언트가 알게 해줍니다.
      - Location : 301, 302 상태코드일 때만 볼 수 있는 헤더로 서버의 응답이 다른 곳에 있다고 알려주면서 해당 위치(URI)를 지정
      - ast-Modified : 리소스의 마지막 수정 날짜
      - Allow : 지원되는 HTTP 요청 메소드 ex) GET, HEAD, POST
      - Expires : 자원의 만료 일자
      - ETag : 리소스의 버전을 식별하는 고유한 문자열 검사기(주로 캐시 확인용으로 사용)

   - **Request Header(요청 헤더)**  
      *HTTP 요청에서 사용되지만 메시지의 컨텐츠와 관련이 없는 패치될 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더*
      - Host : 요청하려는 서버 호스트 이름과 포트번호
      - User-agent : 클라이언트 프로그램 정보 
        - ex) Mozilla/4.0, Windows NT5.1
      - Referer : 현재 페이지로 연결되는 링크가 있던 이전 웹 페이지의 주소
      - Accept : 클라이언트가 처리 가능한 MIME Type 종류 나열
      - Accept-charset : 클라이언트가 지원가능한 문자열 인코딩 방식
      - Accept-language : 클라이언트가 지원가능한 언어 나열
      - Accept-encoding : 클라이언트가 해석가능한 압축 방식 지정
      - If-Modified-Since : 여기에 쓰여진 시간 이후로 변경된 리소스 취득. 캐시가 만료되었을 때에만 데이터를 전송하는데 사용
      - Authorization : 인증 토큰을 서버로 보낼 때 쓰이는 헤더
      - Origin : 서버로 Post 요청을 보낼 때 요청이 어느 주소에서 시작되었는지 나타내는 값. 경로 정보는 포함하지 않고 서버 이름만 포함
        - 이 값으로 요청을 보낸 주소와 받는 주소가 다르면 CORS 에러가 난다.
      - Cookie : 쿠기 값 key-value로 표현된다. Set-Cookie 헤더와 함께 서버로부터 이전에 전송됐던 저장된 HTTP 쿠키를 포함

   - **Response Header(응답 헤더)**  
      *위치 또는 서버 자체에 대한 정보(이름, 버전)과 같이 응답에 대한 부가적인 정보를 갖는 헤더*
      - Server : 웹서버의 종류
      - Age : max-age 시간내에서 얼마나 흘렀는지 초 단위로 알려주는 값
      - Referrer-policy : 서버 referrer 정책을 알려주는 값 
        - ex) origin, no-referrer, unsafe-url
      - WWW-Authenticate : 사용자 인증이 필요한 자원을 요구할 시, 서버가 제공하는 인증 방식
      - Proxy-Authenticate : 요청한 서버가 프록시 서버인 경우 유저 인증을 위한 값
      - Set-Cookie : 서버측에서 클라이언트에게 세션 쿠키 정보를 설정 (RFC 2965에서 규정)


2. 참고
   - https://surprisecomputer.tistory.com/54
   - https://www.zerocho.com/category/HTTP/post/5b344f3af94472001b17f2da
   - https://velog.io/@cham/HTTP-Header%EC%97%90%EB%8A%94-%EC%96%B4%EB%96%A4-%EC%A0%95%EB%B3%B4%EB%93%A4%EC%9D%B4-%EB%8B%B4%EA%B2%A8%EC%9E%88%EC%9D%84%EA%B9%8C