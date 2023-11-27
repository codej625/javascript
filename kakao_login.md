# 카카오 로그인을 구현해보자!

<br/>

```javascript
<!DOCTYPE html>
<html>
  <head>
  <meta charset="UTF-8">
    <title>kakao login</title>

    <script src="https://t1.kakaocdn.net/kakao_js_sdk/2.5.0/kakao.min.js" integrity="sha384-kYPsUbBPlktXsY6/oNHSUDZoTX6+YI51f63jCPEIPFP09ttByAdxd2mEjKuhdqn4" crossorigin="anonymous"></script>
    <script>
      Kakao.init('{javascript_key}');
      Kakao.isInitialized();
    </script>
  </head>
  <body>
    <a id="kakao-login-btn" href="javascript:loginWithKakao()">
      <img src="https://k.kakaocdn.net/14/dn/btroDszwNrM/I6efHub1SN5KCJqLm1Ovx1/o.jpg" width="222" alt="kakao login btn" />
    </a>
    <p id="token-result"></p>

    <script>
      function loginWithKakao() {
        Kakao.Auth.authorize({
          redirectUri: '{redirect}',
        });
      }
      displayToken();
      
      function displayToken() {
        const token = getCookie('authorize-access-token');
  
        if (token) {
          Kakao.Auth.setAccessToken(token);
          Kakao.Auth.getStatusInfo()
            .then(function (res) {
              if (res.status === 'connected') {
                document.getElementById('token-result').innerText = 'login success, token: ' + Kakao.Auth.getAccessToken();
              }
            })
            .catch(function (err) {
              Kakao.Auth.setAccessToken(null);
            });
        }
      }
  
      function getCookie(name) {
        const parts = document.cookie.split(name + '=');
        if (parts.length === 2) {
          return parts[1].split(';')[0];
        }
      }
    </script>
  </body>
</html>
```
