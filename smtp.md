# smtp를 사용해서 메일 받기 기능을 구현해보자!

```html
<div class="form-wrap">
  <form id="" action="" method="">
      <fieldset>
        <legend class="hide">Recruit</legend>
        <div class="write-wrap">
          <dl>
            <dt>회사명</dt>
            <dd>
              <input type="text" name="companyName" class="">
            </dd>
          </dl>
          <dl>
            <dt>담당자</dt>
            <dd>
              <input type="text" name="userName" class="">
            </dd>
          </dl>
          <dl>
            <dt>연락처</dt>
            <dd>
              <input type="text" name="contact" class="form-control" maxlength="11" placeholder="ex) 01012345678">
            </dd>
          </dl>
          <dl>
            <dt>이메일</dt>
            <dd>
              <input type="text" name="email" class="form-control">
            </dd>
          </dl>
          <dl>
            <dt>프로젝트</dt>
            <dd>
              <input type="text" name="project" class="form-control">
            </dd>
          </dl>
          <dl>
            <dt>예산 (월 기준)</dt>
            <dd>
              <input type="text" name="budget" class="form-control">
            </dd>
          </dl>
          <dl>
            <dt>집행기간</dt>
            <dd>
              <input type="text" name="term" class="form-control">
            </dd>
          </dl>
      </div>
      <div class="checkbox-wrap">
        <div class="checkbox-group">
          <input type="checkbox" name="" id="agree_y" checked>
          <label for="agree_y">[필수] 개인정보 수집 및 이용에 동의합니다.</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" name="event" id="agree_y2">
          <label for="agree_y2">[선택] 광고성 정보 수신에 동의합니다.</label>
        </div>
      </div>
      <div class="btn-wrap">
        <button type="button" id="consult" class="">프로젝트 문의</button>
      </div>
    </fieldset>
  </form>
</div>
```

```javascript
// 폼 요소의 값을 직렬화하기 위한 함수
function serializeForm(formId) {
  const form = document.getElementById(formId);
  const formData = new FormData(form);
  const serializedData = new URLSearchParams(formData).toString();

  return serializedData;
}

const consultButton = document.getElementById('consult');
consultButton.addEventListener('click', (e) => {
  e.preventDefault();
  
  let checked = document.getElementById('agree_y');
  checked = checked.checked;

  if (checked == false) {
    alert('개인정보 수집 및 이용에 동의 부탁드립니다.');
    return false;
  }

  const inputFields = ['companyName', 'userName', 'contact', 'email', 'project', 'budget', 'term'];
  
  for (let vali of inputFields) {
    const inputValue = document.querySelector(`#${vali}`).value;

    switch (inputValue) {
      case 'companyName':
        if (inputValue === '') {
          alert('회사명을 입력해주세요');
          return false;
        }
        break;
      case 'userName':
        if (inputValue === '') {
          alert('담당자명을 입력해주세요');
          return false;
        }
        break;
      case 'contact':
        if (inputValue === '') {
          alert('연락처를 입력해주세요');
          return false;
        }
        break;
      case 'email':
        if (inputValue === '') {
          alert('메일을 입력해주세요');
          return false;
        }
        break;
      case 'project':
        if (inputValue === '') {
          alert('프로젝트 내용을 입력해주세요');
          return false;
        }
        break;
      case 'budget':
        if (inputValue === '') {
          alert('예산을 입력해주세요');
          return false;
        }
        break;
      case 'executionPeriod':
        if (inputValue === '') {
          alert('집행기간을 입력해주세요');
          return false;
        }
        break;
    }
  }
  
  // 폼 요소의 ID를 전달하여 직렬화 수행
  const result = serializeForm('frm');
  
  axios.get('{url}', {
    params: result
  })
  .then((response) => {
    const res = response.data;
    if (res === 1) {
      alert('컨설팅 요청이 완료되었습니다.');
      window.location.reload();
    } else {
      alert('잘못된 요청입니다.');
      window.location.reload();
    }
  })
  .catch((error) => {
    console.error('에러 발생: ', error);
  });
});
```

```java
@CrossOrigin
@ResponseBody
@GetMapping(value = "/")
public int getMail(@RequestParam HashMap<String, Object> params) throws Exception {
  log.info(">>> controller start >>>");
  
  final String DATE_TIME_HUMAN_READABLE_PATTERN = "yyyy년 M월 d일 H시 m분";   // date format set
  final SimpleDateFormat DATE_TIME_HUMAN_READABLE_FORMAT = new SimpleDateFormat(DATE_TIME_HUMAN_READABLE_PATTERN);

  final String user = "test@naver.com", // 발신자 이메일
               password = "12345678"; // 발신자 패스워드
  
  String companyName = (String) result.get("companyName"), 
         userName = (String) result.get("userName"),
         contact = (String) result.get("contact"), 
         email = (String) result.get("email"),
         project = (String) result.get("project"),
         budget = (String) result.get("budget"),
         term = (String) result.get("term"),
         event = (String) result.get("event");
  event = (event == null) ? "동의 안 함" : "동의";
  
  String[] params = { companyName, userName, contact, email };
  
  if (Arrays.asList(params).contains(null)) return 0; // parameter check
    
  StringBuilder builder = new StringBuilder();
  builder.append("신청자 입력 정보" + "\n");
  builder.append("- 회사명 : " + companyName + "\n");
  builder.append("- 이름 : " + userName + "\n");
  builder.append("- 연락처 : " + contact + "\n");
  builder.append("- 이메일 : " + email + "\n");
  builder.append("- 프로젝트 : " + project + "\n");
  builder.append("- 예산 : " + budget + "\n");
  builder.append("- 집행기간 : " + term + "\n\n");
  builder.append("추가 정보" + "\n");
  builder.append("- 신청 일시 : " + DATE_TIME_HUMAN_READABLE_FORMAT.format(new Date()) + "\n");
  builder.append("- 모바일 / PC 구분 : " + (device.isMobile() ? "모바일" : "PC") + "\n");
  builder.append("- 접속 IP : " + SystemUtil.getClientIpAddr(request) + "\n");
  builder.append("- Agent : " + SystemUtil.getClientAgent(request) + "\n");
  builder.append("- 광고성 정보 수신에 동의 : " + event + "\n");

  Properties prop = new Properties();
  prop.put("mail.smtp.host", "smtp.naver.com"); // naver smtp server
  prop.put("mail.smtp.port", 587);
  prop.put("mail.smtp.auth", "true");
  prop.put("mail.smtp.ssl.enable", "false");
  prop.put("mail.smtp.ssl.trust", "smtp.naver.com");

  Session session = Session.getInstance(prop, new javax.mail.Authenticator() {
    protected PasswordAuthentication getPasswordAuthentication() {
      return new PasswordAuthentication(user, password);
    }
  });

  try {
    MimeMessage message = new MimeMessage(session);
    message.setFrom(new InternetAddress(user));
    message.addRecipient(Message.RecipientType.TO, new InternetAddress("test@naver.com")); // 수신자 이메일
    message.setSubject("[컨설팅 요청]" + " \"" + companyName + "\""); // 메일 제목
    message.setText(builder.toString()); // 메일 내용
    Transport.send(message);
  } 
  catch (AddressException e) {
    log.info("");
    e.printStackTrace();
    
    return 0;
  } 
  catch (MessagingException e) {
    log.info("");
    e.printStackTrace();
    
    return 0;
  }
  return 1;
}
```
