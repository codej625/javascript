# 카카오 로그인을 구현해보자!

<br/>

1. JavaScript SDK 초기화 및 카카오 버튼 구현
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>kakao</title>
  <script src="https://t1.kakaocdn.net/kakao_js_sdk/2.5.0/kakao.min.js" integrity="sha384-kYPsUbBPlktXsY6/oNHSUDZoTX6+YI51f63jCPEIPFP09ttByAdxd2mEjKuhdqn4" crossorigin="anonymous"></script>
  <script src="/script/common/kakao-init.js"></script>
</head>

<body>
  <div style="border: 1px solid; width: 300px; margin: 0 auto; border-radius: 10px; background: #ededed; text-align: center;">
    <div style="margin: 20px 20px;">
      <input style="height: 50px; font-size: 20px;" id="birthday" oninput="maxLengthCheck(this);" pattern="\d*" maxlength="8" type="number" placeholder="생년월일 (19990101)">
    </div>
    <a id="kakao-login-btn" href="javascript:loginWithKakao()">
      <img src="https://k.kakaocdn.net/14/dn/btroDszwNrM/I6efHub1SN5KCJqLm1Ovx1/o.jpg" width="222" alt="카카오 로그인 버튼" />
    </a>
  </div>
  <script src="/script/common/common.js"></script>
</body>

</html>
```

<br/>

2. (로그인은 카카오 서버에서 작동 된다.) 리다이렉트 후 URI에 파라미터로 붙어있는 파라미터 code(인가 코드) 값으로 토큰 받기 요청하기
```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>Login</title>
</head>

<body>
  <div id="text"></div>
  <script src="/script/common/kakao-login.js"></script>
</body>

</html>
```

<br/>

3. (여기서 부터는 스프링을 사용해서 백엔드를 구현한다.) 전달 받은 값으로 토큰과 개인정보를 얻는다.
```java
package kr.co.mplanit.freemilkt.restcontroller;

import java.io.IOException;
import java.util.HashMap;
import java.util.Map;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

import com.fasterxml.jackson.databind.ObjectMapper;

import kr.co.mplanit.freemilkt.service.KakaoLogin;
import lombok.extern.slf4j.Slf4j;

@Slf4j
@RestController
public class RestApiController {

  @Autowired
  KakaoLogin kakaoLogin;

  @SuppressWarnings("unchecked")
  @PostMapping("/rest/kakao-login")
  public Map<String, Object> kakaoLogin(@RequestBody Map<String, Object> params) {
    log.info(">>> RestApiController kakaoLogin start >>>");

    String accessToken = ""; /* Assign token to variable */
    String secureResource = "";
    String shippingAddress = "";
    String redirect = (String) params.get("redirectUri");
    String code = (String) params.get("code");
    
    Map<String, Object> map = null;
    ObjectMapper mapper = new ObjectMapper();

    try {
      map = mapper.readValue(kakaoLogin.getKakaoToken(redirect, code), Map.class); /* Get Token */
      accessToken = (String) map.get("access_token");
      secureResource = kakaoLogin.getSecureResource(accessToken); /* Get personal information */
      shippingAddress = kakaoLogin.getShippingAddress(accessToken);
      
      map = new HashMap<String, Object>();
      map.put("secureResource", secureResource);
      map.put("shippingAddress", shippingAddress);
      /* API -> DB */
        
      /* Logic */
//			map.clear();
//			map.put("secureResource", secureResource);
    } catch (IOException e) {
      e.printStackTrace();
      log.info(" >>> account access error >>>");
    }
    return map;
  }
  
}
```

<br/>

4. service
```java
package kr.co.mplanit.freemilkt.service;

import java.nio.charset.StandardCharsets;
import java.util.Collections;

import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Service;
import org.springframework.util.LinkedMultiValueMap;
import org.springframework.util.MultiValueMap;
import org.springframework.web.client.RestTemplate;

import lombok.extern.slf4j.Slf4j;

@Slf4j
@Service
public class KakaoLogin {

  private final RestTemplate restTemplate;
  
  public KakaoLogin(RestTemplate restTemplate) {
    this.restTemplate = restTemplate;
  }
  
  public String getKakaoToken(String redirectUri, String code) {
    log.info(">>> RestApiController getKakaoToken start >>>");
  
    HttpHeaders headers = new HttpHeaders();
    headers.setContentType(MediaType.APPLICATION_FORM_URLENCODED);
    headers.setAcceptCharset(Collections.singletonList(StandardCharsets.UTF_8));
  
    MultiValueMap<String, String> map = new LinkedMultiValueMap<>();
    map.add("grant_type", "authorization_code"); /* 고정 */
    map.add("client_id", {client_id});
    map.add("redirect_uri", redirectUri);
    map.add("code", code);
    map.add("client_secret", {client_secret}); /* 카카오 계정에서 설정할 수 있는 보안 옵션 */ 
  
    HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(map, headers);
    String url = "https://kauth.kakao.com/oauth/token"; /* 토큰 받기 */
    ResponseEntity<String> response = restTemplate.postForEntity(url, request, String.class);
  
    return response.getBody();
  }
  
  public String getSecureResource(String accessToken) {
    log.info(">>> RestApiController getSecureResource start >>>");
  
    HttpHeaders headers = new HttpHeaders();
    headers.setContentType(MediaType.APPLICATION_FORM_URLENCODED);
    headers.set("Authorization", "Bearer " + accessToken); /* header값에 엑세스 토큰을 사용한다. */
  
    MultiValueMap<String, String> map = new LinkedMultiValueMap<>();
    map.add("secure_resource", "true"); /* https 옵션 true */
  
    HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(map, headers);
    String url = "https://kapi.kakao.com/v2/user/me"; /* 사용자 정보 요청 URL */
    ResponseEntity<String> response = restTemplate.postForEntity(url, request, String.class);
  
    return response.getBody();
  }

  public String getShippingAddress(String accessToken) {
    log.info(">>> RestApiController getShippingAddress start >>>");

    HttpHeaders headers = new HttpHeaders();
    headers.set("Authorization", "Bearer " + accessToken);

    HttpEntity<MultiValueMap<String, String>> request = new HttpEntity<>(headers);
    String url = "https://kapi.kakao.com/v1/user/shipping_address";
    ResponseEntity<String> response = restTemplate.exchange(url, HttpMethod.GET, request, String.class);

    return response.getBody();
  }
}
```

<br/>

5. add javascript
```javascript
function loginWithKakao() {
  const birthday = document.getElementById('birthday').value;
  
  if (isNaN(birthday)) {
    alert('숫자만 입력해주세요.');
    return false;
  }
  if (birthday.length !== 8) {
    alert('정확한 생년월일을 입력해주세요');
    return false;
  }
  if (birthday === '') {
    alert('정확한 생년월일을 입력해주세요');
    return false;
  }
  return location.href = `https://kauth.kakao.com/oauth/authorize?response_type=code&client_id=${client_key}&redirect_uri=https://ad-milkt.com/main/common/login&state=${birthday}`;
}
/* input max length */
function maxLengthCheck(object){
  if (object.value.length > object.maxLength){
    object.value = object.value.slice(0, object.maxLength);
  }
}
```

```javascript
/* Global variable */
let code = '';
const params = new URLSearchParams(window.location.search);
/* Function */
function sendData() {
  const data = {
    code,
    redirectUri: 'https://ad-milkt.com/main/common/login'
  };

  fetch('/rest/kakao-login', {
    method: 'post',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(data)
  })
  .then(response => {
    if (response.status === 500)
      return location.href = 'https://ad-milkt.com'; /* 수정 */
    
    return response.json();
  })
  .then(response => {
    let secureResource = '';
    let shippingAddress = '';
    
    if (response.secureResource !== '')
      secureResource = JSON.parse(response.secureResource);
    if (response.shippingAddress !== '')
      shippingAddress = JSON.parse(response.shippingAddress);
    
    const name = secureResource['kakao_account']['name'];
    const gender = secureResource['kakao_account']['gender'];
    console.log('address => ', shippingAddress);
//		const detailAddress = shippingAddress['shipping_addresses']['detail_address'];
//		const text = `name: ${name} gender: ${gender} address name: ${addressName} detail address: ${detailAddress}`;
    
    const view = document.getElementById('text');
    return view.innerHTML = text;
  })
  .catch(err => {
    alert('잘못된 접근입니다.');
    return location.href = 'https://ad-milkt.com'; /* 수정 */
  });
}
/* Exception */
try {
  code = params.get('code');
  if (code.length > 1)
    sendData();
  else
    throw new Error();
    
} catch (err) {
  alert('잘못된 접근입니다.');
  location.href = 'https://ad-milkt.com'; /* 수정 */
}
```

```javascript
Kakao.init(${javascript_key}); /* javascript key */
Kakao.isInitialized(); /* kakao init */
```

<br/>

```
소스를 활용해서 프론트 단에서 활용하거나 그전에 데이터베이스에 저장을 할 수도 있다.
```
