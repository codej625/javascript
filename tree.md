# 크리스마스 트리를 만들어보자!

<br/>

javascript
let outPut = "";

 //2.loop 횟수설정
for (var i = 0; i < 15; i++) {
  //3. 공백 감소
  for (var j = 15; j > i; j--) {
    //console.log(`i:${i} , j:${j}`);
    outPut += " ";
  }
  //4. 별 증가
  for (var k = 0; k < i * 2 + 1; k++) {
    outPut += "*";
  }
  //5.줄 바꿈
  outPut += "\n";
}
console.log(outPut);
'''
