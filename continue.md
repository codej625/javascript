# Continue

<br />
<br />

* 잘 사용하지 않는 continue

--- 

```
여러 파일을 순차적으로 처리해야 하는 상황에서
continue를 사용하면 굉장히 편리한데,
평소 잘 사용하지 않는 continue 사용 예시를 알아보자.
```

<br />
<br />
<br />
<br />

1. continue? return?

```
파일들을 체크하고 검증하는 로직이다.

여기서 파일이 조건문에 걸릴때마다
return을 쓰면 어떻게 될까?
```

<br />

`return 사용 시`

```ts
for (const file of files) {  // 파일 3개: A, B, C
  if (!extractedIp) {
    invalidFiles.push(`${file.name}`);
    return; // 함수 전체 종료
  }
  // 나머지 검증 로직...
  validFiles.push(file);
}

// A파일에서 문제 발견 → 함수 완전 종료, B와 C파일 처리 안 됨
```

<br />

`continue 사용 시`

```ts
for (const file of files) {  // 파일 3개: A, B, C
  if (!extractedIp) {
    invalidFiles.push(`${file.name}`);
    continue; // 현재 파일만 건너뛰고 다음 파일로
  }
  // 나머지 검증 로직...
  validFiles.push(file);
}

// A파일에서 문제 발견 → A파일만 건너뛰고 B, C파일 계속 처리
```
