# INPUT 의 길이(용량) 계산하기

<br />
<br />

* 길이 제한 VS 용량 제한

---

```
Input의 길이 제한을 할 때,
일반적으로 length를 기준으로 하는 경우가 많다.

하지만 이는 대부분의 경우에서 문제를 일으킨다.

DB 컬럼의 용량을 기준으로 제한하지 않으면,
숫자, 알파벳, 한글 무엇을 입력해도 길이로 제한이 돼버리기 때문에

DB 인코딩(EUC-KR, UTF-8)에 맞춰 용량 제한을 걸자.
```

<br />
<br />
<br />
<br />

1. 간단한 용량 제한 예시

```
여기서는 함수를 하나 만들어
용량을 계산하고 그에 따른 조건을 거는 방법을 사용한다.

(그 외에도 얼마든지 응용 방법이 많으니 참고만 하시길)
```

```tsx
// common-func.ts

export function getEucKrByteLength(str: string): number {
  let byteLength = 0;
  for (let i = 0; i < str.length; i++) {
    const charCode = str.charCodeAt(i);

    // 한글 유니코드 범위 (가-힣: 0xAC00-0xD7AF)
    if (charCode >= 0xac00 && charCode <= 0xd7af) {
      byteLength += 2; // 한글은 EUC-KR에서 2바이트
    }
    // 한글 자모 (ㄱ-ㅎ, ㅏ-ㅣ)
    else if (
      (charCode >= 0x3131 && charCode <= 0x318e) ||
      (charCode >= 0x3200 && charCode <= 0x321e) ||
      (charCode >= 0x3260 && charCode <= 0x327e)
    ) {
      byteLength += 2; // 한글 자모도 2바이트
    }
    // ASCII 범위 (0-127)
    else if (charCode <= 127) {
      byteLength += 1; // ASCII는 1바이트
    }
    // 기타 특수문자들 (대부분 2바이트)
    else {
      byteLength += 2; // 안전하게 2바이트로 계산
    }
  }
  return byteLength;
}
```

```tsx
// 사용 예시

const [value, setValue] = useState<string>("");

<input
  name="value"
  value={value}
  placeholder={"(최대 25자)"}
  onChange={(e: React.ChangeEvent<HTMLInputElement>) => {
    const inputValue: string = e.target.value;
    const byteLength: number = getEucKrByteLength(inputValue);
    
    if (byteLength > 50) {
      // 50바이트를 초과하는 경우, 문자를 하나씩 제거하면서 50바이트 이하가 될 때까지 자르기
      let trimmedValue: string = inputValue;
      while (getEucKrByteLength(trimmedValue) > 50 && trimmedValue.length > 0) {
        trimmedValue = trimmedValue.slice(0, -1);
      }
      setValue(trimmedValue);
    } else {
      setValue(inputValue);
    }
  }}
/>
```

<br />
<br />
<br />
