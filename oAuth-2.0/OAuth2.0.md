# OAuth 2.0

인증을 위한 표준 프로토콜  
간편 로그인(구글, 카카오, 네이버 등)도 해당 방식을 사용  

---

## grant_type
클라이언트 환경에 따른 인증 및 권한 위임 방법  
access token을 발급받기 위해서 필수로 필요  

- **refresh_token**  
- **implicit**  
- **password**  
- **client_credentials**  
- **refresh_token**
  - access token 만료 후 재발급을 위해 사용하는 토큰 

### Authorization Code Grant
자체 생성한 Authorization Code를 전달하여 사용  
클라이언트가 사용자를 대신하여 특정 자원에 접근(간편 로그인)  


---

## acceess token
인증에 성공하면 결과로 받을 수 있음  
만료 기간이 존재

헤더에 다음과 같은 형식으로 access token을 추가 

```
Authorization : Bearer {ACCESS_TOKEN}
```



---
https://blog.naver.com/mds_datasecurity/222182943542
https://www.oauth.com/oauth2-servers/access-tokens/client-credentials/