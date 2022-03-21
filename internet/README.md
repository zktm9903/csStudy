# 인터넷
## 인터넷은 어떻게 동작하는가?
1. 인터넷이란?  
   - *인터넷은 웹의 핵심적인 기술*
   - *컴퓨터들이 서로 통신 가능한 거대한 네트워크*
   - *수십억 대의 컴퓨터를 모두 연결하는 기술 인프라*
   ---
2. 인터넷의 변천과정  
   - 두 개의 컴퓨터가 통신이 필요할 때, 다른 컴퓨터와 물리적으로 또는 무선으로 연결되어야 함 
     
   ---
   **단순한 네트워크**
   ![internet-schema](/internet/images/internet-schema-1.png)
   - 1대1로 연결
   
   ![internet-schema](/internet/images/internet-schema-2.png)
   - 10대의 컴퓨터를 연결하려는 경우 컴퓨터 당 9개의 플러그가 달린 45개의 케이블 필요  
  
   ![internet-schema](/internet/images/internet-schema-3.png)
   - 이 문제를 해결하기 위해 네트워크의 각 컴퓨터는 라우터라고 하는 특수한 소형 컴퓨터에 연결   
   - 10대의 컴퓨터에는 10개의 케이블이 필요
   ---
   **네트워크 속의 네트워크**
   ![internet-schema](/internet/images/internet-schema-5.png)
   - 라우터끼리 연결  
  
   ![internet-schema](/internet/images/internet-schema-6.png)
   - 모뎀이라는 특수 장비를 이용하여 전화시설에 연결

   ![internet-schema](/internet/images/internet-schema-7.png)
   - 네트워크를 인터넷 서비스 제공 업체 (Internet Service Provider, ISP)에 연결
   - ISP는 모두 함께 연결되는 몇몇 특수한 라우터를 관리하고 다른 ISP의 라우터에도 액세스 할 수 있는 회사
   ---

3. IP/도메인이란?  
   - 네트워크에 연결된 모든 컴퓨터에는 IP 주소라는 고유한 주소가 있음 
   예:`192.168.2.10`
   - IP 주소를 일일히 기억하기 어려움 따라서 '도메인 이름' 이라고하는 사람이 읽을 수 있는 IP 주소의 이름을 지정
   ![internet-schema](/internet/images/dns-ip.png)

4. 인터넷과 웹
   - 인터넷과 웹이 같은 것을 의미하지는 않음
   - 인터넷은 수십억 대의 컴퓨터를 연결하는 기술 인프라
   - 컴퓨터들 중 일부는 '웹 서버'로서 웹 브라우저가 이해할 수 있는 서비스를 제공
   - 인터넷은 **인프라**, 웹은 **그 위에 구축된 서비스**