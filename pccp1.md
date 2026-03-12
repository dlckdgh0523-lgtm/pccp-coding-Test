정수 내림차순으로 정리하기 

함수 solution은 정수 n을 매개변수로 입력받는다 

n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴하라

예를들어 n이 118372 면 873211 을 리턴하면된다 

​

내림차순 은 sort b -a 사용하면 될것같고 

수를 문자열로 바꾸고 string

 하나씩 나열했다가 붙혀야하니깐 .. split ,join

parsInt 붙혀서 리턴 

function solution(n) {
 
    const result = String(n)
           .split("")
           .sort((a , b) => b - a)
           .join("");
    return parseInt(result);
}
3점 

​

2. 하샤드 수 

양의정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야한다

예를들어 18의 자릿수합은 1+8 = 9 이고 19 은 9로 나누어 떨어지므로 18은 하샤드 수다

자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수 솔루션을 완성하라

​

음 ..

x안에 들어갈  수를 문자열로 쪼개서 더하고 수로 변경 후 % 나누기  

 split   sum reduce 일까 ? nerArray ,  더하고  x랑 나눈다 

그 값이 x %  ===  0 이 나오는 수 

sum 오류나오네 이건 아니니 reduce로 

function solution(x) {
    
    const newArray = String(x).split('');
    const newH = newArray.reduce((acc,curr) => acc + Number(curr) ,0);
    const answer = (x% newH === 0);
    return answer;
}
​

​

​

3. 정수 제곱근 판별 

임의의 양의 정수 n 에대해 , n이 어떤 양의 정수 x 의 제곱인지 아닌지 판단하려한다

n이 양의정수 x의 제곱이라면 x+1의 제곱을 리턴하고 n이 양의정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하라

입출력 예를 보아하니 아니면 그냥 -1 떄리고 

if 문 n === x * x 트루면 x + 1 * x + 1 

그짓이면 리턴 -1 

이게 맞을까 갑자기 쉬워지는데 

넣어보려하니 이건 아닌거같다 x가 주어지는건 아닌거같은데 이게 n이 무언 수의 제곱인지 를 알아야 할거같은데 

검색 해보니 [javascript] Math.sqrt() 제곱근 반환


[javascript] Math.sqrt() 제곱근 반환
Math.sqrt() 함수는 숫자의 제곱근을 반환한다.x : 숫자반환 값주어진 숫자에 루트를 씌운다. 만약 숫자가 음수이면 NaN를 반환한다.sqrt()는 Math의 정적 메서드 이므로 만든 Math 객체의 메서드가 아니라 항상 Math.sqrt()함수를 사용해야한다.

velog.io

이걸 써야할거같다  이걸 써서 x를 선언해주고 해보자 

걍 해보니 오류 

정수가 아닌 3..... 뭐 이딴게 끼니깐 계산을 몬하나 

if 에서 이게 정수인지 판별하고 정수면 +1 해서 곱해주고 

정수 판별 number.is integer

function solution(n) {
   const x = Math.sqrt(n)
   if (Number.isInteger(x) ){ 
   return (x+1) * (x+1) ; 
   }else {
       return -1
   }
    
}
8점이네 ? b 

​

​

4. 자연수 뒤집어 배열로 만들기

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴 

예를들어 n 이 12345 이면 [5,4,3,2,1]을 리턴한다 

이거 그냥 문자열로 바꿔주고  쪼개서  배열 안에 넣어준뒤에  배열 뒤집고 숫자로 바꿔주면 그만인게 아닌가 

String.split ('') 

reverse(newArray)

function solution(n) {
  return String(n).split('').reverse().map(Number)
}
ez 하네

​

5. 자릿수 더하기 

자연수 N이 주어지면 N의 각 자릿수의 합을 구해서 return 하는 솔루션함수를 만들어라 

n이 123 이면 6 

​

이것도 문자 배열로 쪼개주고 더하고 다시 합쳐주고 

String(n).split('').reduce((acc,curr) => acc + Number(curr), 0)

function solution(n)
{ 
    return String(n).split('').reduce((acc,curr) => acc + Number(curr), 0)
}
​

​

​

6. 두 정수 사이의 합

두 정수 a,b 가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, 솔루션을 완성하라

a= 3 b=5 일 경우 3+4+5 =12 12를 리턴 같은경우는 a b 둘중 아무거나 리턴

if 문 쓰고 a b 사이의 임의 x 선언 a보다 크고 b보단 작은  아 근데 a b 대소관계는 정해진게 없으니 작을수도 있는데 

if를 두번 들어가야하나 ?  등차수열 합 ? 사이가 얼마나 클지도 모르지 예시처럼 차이가 짧은게 아니라 크다면 ?

 그럼 등차수열 합으로 a b 더하고 a b 사이 개수 구하고 /2  return a + b Math.abs b-a +1 /2 

이거로 해보자 

function solution(a, b) {
 
    return (a+b) * (Math.abs(b - a) + 1 )/2  ;
}
​

​

​

​

​

7. 문자열 내 p 와 y 의 개수

대문자와 소문자가 섞여있는 문자열 s가 주어진다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 true. 다르면 false 를 리턴하는 솔루션을 완성하라 p와 y 모두 하나도 없는 경우는 항상 트루 리턴 단 개수를 비교할때 대문자와 소문자는 구별하지 않는다 .....

와.. 음 .. 우선 s 를 쪼개 p  y 개수 찾고 비교  쪼개주고 하나씩 들러서 이게 있나 없나 for을 두개 p 찾는애 y찾는애 

for .length 일까 그렇게 찾아서 개수 비교할때 if 같으면 true 틀리면 false 그것도 아닌게 둘다 없을때니 else true???? 

근데 대소문자 구별 안한댓는데 이건 검색 

for 에 if 가 들어가도 되겠네 

else if  두개 각 증가 시켜주고 마지막에 p y 비교 

toLowerCase 이게 대소문자 무시시켜주는것 

function solution(s){
  const str = s.toLowerCase();
  let p = 0;
  let y = 0;
  for (let i = 0;i < str.length;i++){
      if (str[i] === 'p'){
          p++;
      }else if (
          str[i] === 'y'
      ) { y++;
        }  }
    return p === y;
}
​

8.음양 더하기 

어떤 정수들이 있다 . 이정수들의 절댓값을 차례대로 담은 정수 배열 absolution 와 이 정수들의 부호를 차례대로 담은 불리언 배열 signs 가 매개변수로 주어진다 실제 정수들의 합을 구하여 리턴하라 

제한 absolution 은 1 이상 1000 이하 

signs 의 길이는 ab 의 길이와 같다 

signs[i]가 참이면 abs..[i] 의 실제 정수가 양수임을 그렇지 않으면 음수임을 의미한다 

​

ab 에는 - 든 그냥 배제하고 숫자 오게하고 

signs 는 true false .. result 는  - 든 + 든 걍 더한 정수 

ab에는 그냥 정수로 만들어서 배열 넣어주고 

signs 는 if 넣어서 .. 이게 + 인지 -인지 

리턴은 그냥 이것들 합 reduce 해서 넣어준다 

아 입출력을보니 잘못이해했네 

abs.. 하고 signs 은 주어진다 

signs가 true면 더하기 

false면 빼기 

for i abs.length i ++ if signs[i]{answer += abs [i]

이런식으로 해보자

 

​

function solution(absolutes, signs) {
    var answer = 0;
    for (let i = 0; i < absolutes.length;i++){
        if (signs[i] ){
            answer+=absolutes[i];
        }else {answer -= absolutes[i]}
    }
    return answer;
}
ezzzzzzzz

​

​

9. 없는 숫자 더하기 

0부터 9까지의 숫자중 일부가 들어있는 정수배열 numbers 가 매개변수로 주어진다 .numbers 에서 찾을수 없는 0부터 9까지의 숫자를 모두 찾아 더한 수 를 리턴  

​

아까 했던 등차수열 합으로 들어 가 되 가 아닌가 ? 

아니다 1 부터 9까지 없는걸 찾아 더해라 .reduce

없는걸 찾는건 비교 해야하나  

우선 등차수열로 진행 

0 +9 * 10 / 2 = 45 

45 에서  numbers 합 계산해서 뺴뻐리면 그만 인것같다 

function solution(numbers) {
    
    return 45 - numbers.reduce((acc,curr) => acc + Number(curr),0);
}
 한번 진행 해본 식이다보니 매우매우 ezzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

​

​

10. 나누어 떨어지는 숫자 배열 

array의 각 element중 divisor 로 나누어 떨어지는 값을  오름차순으로 정렬한 배열을 반환하는 함수 솔루션을 완성하라 

divisor로 나누어 떨어지는 element가 하나도 없다면 그냥 -1 리턴 

arr 은 자연수

정수 i , j에 대해 i 랑 j가 같지 않다면 arr [i] 랑 arr[j]는 같지 않다 

divisor는 자연수 

array는 길이 1 이상인 배열 

array하고 divisor이 주어진다 

arr는 막 섞여 나올수 있으니 정렬 해줘야하고 

arr 하나하나 읽어서 for array.length i++ 

if arr[i] % divisor === 0 {

answer.push arr[i]} else -1 

이렇게도 갈거같고 음.. filter도 될거같은데 

filter가 깔끔할거같으니 

function solution(arr, divisor) {
    const answer = arr.filter(num => num % divisor === 0 );
            if (answer.length === 0 ){
                return [-1];
            }
    return answer.sort((a,b) => a-b);
}
​

11. 서울에서 김서방 찾기 

String 형 배열 seoul 의 element 중 "kim"의 위치 x 를 찾아, "김서방은 x 에 있다"는 String을 반환하는 함수 . 솔루션을 완성해라 . 서울에 김은 오직 한번 나타나며 잘돗된 값이 입력되는 경우는 없다 

서울은 길이 1 이상 1000 이하

원소는 길이 1 이상 20 이하 문자열 

김은 반드시 서울에 있다 

주어지는건 서울 

배열.. 에서 값을 찾아라 인거 같은데 

컴퓨터는 0부터 세기 때문에 이게 문제가 되려나 싶기도 하고 길이가 제한이 있으니 상관 없을듯  string 인덱스 

인덱스이니 인덱스안에서 찾는건 ..  인덱스오브 

리턴해서 `김서방은 ${x}에 있다` 

function solution(seoul) {
    const x = seoul.indexOf("Kim");
    return `김서방은 ${x}에 있다`;
}
ㅋ

​

12. 콜라츠 추측 

1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될 떄까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다 

1-1. 입력된 수가 짝수라면 2로 나눕니다. 

1-2 입력된 수가 홀수라면 3을 곱하고 1을 더한다 

2. 결과로 나온수에 같은작업을 1이 될 떄까지 반복한다 

예를들어 주어진수가 6이라면 6 - 3 - 10 - 5 - 16 - 8 - 4 - 2 - 1 이 되어 총 8번만에 1이 된다 위 작업을 몇번을 

반복해야하는지 반환하는 함수 솔루션을 완성하라 단 주어진수가 1인경우에는 0을 작업을 500 번 이상 반복할떄까지 1이 안된다면 -1을 반환 

​

​

...이거 뭐 인스타같은데서  마술이랍시고 뭐 본적 있는거 같은데 .. 

if문 n %  2 === 0 은 짝수란거니깐  n/2 해주고 

n % === 1 은 홀수 n * 3 +1 

for 안에 if 문들어가야겠고 아니다 이건 while 문이겠네 

계속 반복하는게 아니니깐 1 이 나오면 그만두라 

if문 계속 돌아가게 마지막 else  리턴 -1 

​

 

function solution(num) {
    var answer = 0;
    
    while (num !== 1){
        if (answer >= 500 )return -1
        if (num % 2 === 0){
            num = num/2;
        }else {
            num = num*3+1;
        }
        answer ++;
    }
    return answer;
}
13. 핸드폰 번호 가리기 

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼때 고객들의 전화번호의 일부를 가립니다.,

전화번호가 문자열 phone_number로 주어졌을때 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 * 으로 가린 문자열을 리턴하는 함수 솔루션을 완성하라

​

숫자 문자열로 전환 뒤 4자리 제외하면 앞 7자리 니깐 이걸 * 로 바꾸라는 로직 

조건 걸어서 앞 7자리 .. 문자열이면 String(phone_number).split(').push(*) .. 조건 거는 방법이 .,.

아니다 생각해보니깐 앞에가 7자리가 아닐 수 도 있네  그냥 뒤 4자리를 뺏다가 더하는게 맞겠네

for phone_number.length i ++ 

if  i < length -4   += *

아니라면 그냥 숫자 그대로 노출 

 

function solution(phone_number) {
    var answer = '';
    for (let i = 0; i < phone_number.length ; i ++){
        if(i < phone_number.length -4){
            answer += "*"
        } else {
            answer += phone_number[i]
        }
    }
    return answer;
}
​

14. 가운데 글자 가져오기 

단어 s 의 가운데 글자를 반환하는 함수 솔루션을 만들어라 

단어의 길이가 짝수라면 가운데 두글자를 반환한다 

음... 가운데 글자 변수 선언하고 소수점 안나오게 math.floor 글자수 에 /2  해서 가운데 잡고

if 들어가서 s.length % 2 === 0  변수 -1 + 변수 

​

function solution(s) {
   
    const mid = Math.floor(s.length/2)
    if (s.length % 2 === 0){
        answer = s[mid -1] + s[mid]
    }else {
        answer = s[mid]
    }
    return answer;
}
15. 제일 작은 수 제거하기

정수를 저장한 배열 , arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수 솔루션을 완성하라 

단 리턴하려는 배열이 빈 배열일 경우 배열에서 -1을 채워 리턴해라

이건..  arr.filter 하고 math.min 사용하면 쉬울거같은데 우선 빈배열일경우 ..if arr.length <=1 return [-1]

하고 Math.min arr 해서 최소값 구해주고 

필터로 걸러준다 

function solution(arr) {
    if (arr.length <= 1){return [-1]}
    const min = Math.min(...arr)
    answer = arr.filter(num => num !== min )
    
    return answer;
}
​

16. 내적

길이가 같은 두 1차원 정수 배열 a, b 가 매개변수로 주어집니다. a와 b의 내적을 return 하도록 솔루션함수를 완성해라 

이때 a와 b의 내적은 a[0] * b[0] + a[1] *b[1]  ...??????

내적.. 이 뭔지 모르겠는데 설명을 봤더니 

Dot product - Wikipedia 

뭐라 씨부리싸는건지 모르겠다 

채찍피티한테 물어보자 얜 무슨 벡터 뭐 이러는데 

뭐라는겨 

다시 코데로 와서 보니 입출력 예시를 보고 알아냈다 

a 하고 b [] [] 안에 있는걸 

인덱스 숫자가 맞는것끼리 곱하라 그 곱한걸 더해라 

​

a 를 쪼개주고 따로 선언 [ㅁ , ㄴ , ㅇ , ㄹ ]

b를 쪼개준다음 따로 선언 [ㅂ, ㅈ, ㄷ ,ㄱ ]

a선언.length        

b선언.length 끼리 곱한다 ?.. for 문 필요할거같고

이거 또 그냥 reduce로는 안될까 ? 

a. reduce acc curr i => acc + (curr * b[i] ,0) ?

될거같은데 

function solution(a, b) {
   
 return a.reduce((acc, cur, i) => acc + (cur * b[i]), 0);
}
설명만 어려운거였군 

​

17. 수박수박수밧ㄱ수밧가ㅑㅜㅈㅂ

길이가 n이고 , "수박수박수박수..."와 같은 패턴을 유지하는 문자열을 리턴하는 함수 솔루션을 완성하라 

예를들어 n이 4면 수박수박을 리턴하고 3이면 수박수를 리턴한다 

for n.length i ++ 

   {answer = n[i] }

오류뜨네 이게 아닌가본데 n은 10000 이하 자연수 ... 짝 홀 수 박 인가 

for 그대로 가고 

if i % 2 === 0 {answer += "수" }else if i % 2 === 1 { answer += "박 "  }

function solution(n) {
    var answer = "";
    for (let i = 0; i < n;i++){
       if (i % 2 === 0 ){
           answer += "수";
       }else if (i % 2 === 1 ) {
           answer += "박";
       }
    }
    return answer;
18. 약수의 개수와 덧셈 

두 정수 left와 right 가 매개변수로 주어진다. left 부터 right 까지 모든 수들 중에서 약수의 개수가 짝수인 수는 더하고 약수의 개수가 홀수인 수는 뺀수를 리턴하라 

 음.. 우선 약수의 개수가 짝인지 홀인지 알아야 하는데 등차수열인가 ? 아닌데 ..  이거 제곱수 찾으믄 될것도 같은데 

제곱수 = 1 4 9 16 25 36 48  홀수 그게 아닌건 짝수 124 139 124816 1525 123469121636 이게 맞나보군 

이게 딱 떨어진다.. 는 아까 쓴 isInteger Math.sqrt  이걸 for문 안에서 돌려준다 ... 

function solution(left, right) {
    var answer = 0;
    for (let i= left ; i <= right ; i ++ ){
        if (Number.isInteger(Math.sqrt(i))){
            answer -= i;
            }else { answer += i;}
    }
    return answer;
}
i left i <= rigth i ++ 레프트부터 라이트까지 돌리고 

여기서 나온 i 가  정수인 제곱근이냐 ? 맞으면 - i 틀리면 + i

19.   문자열 내림차순으로 배치하기

문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수 솔루션을 만들라 

s는 영문 대소문자로만 구성되어있고 대문자는 소문자보다 작은것으로 간주한다 

str은 길이 1 이상이다 S Zbcdefg // gfedcbZ 

????????????

문자열을 큰것부터 작은순으로 정렬해라 ? 무슨기준으로 문자가 수도 아니고 ?? 

abcdefg 역순인건 맞는거같은데   컴퓨터가 인식하는 그런 숨겨진 그런게 있나 ? 검색해보니 그렇다고 하네요

그럼 split으로 쪼개서 sort (a ,b b-a ) 해주고  join""다시 합치면 끝일라나 

     return s.split('').sort((a,b) => b -a ).join(''); 해줬더니 Z 가 맨 앞으로오네 .. Z를 뒤로 빼는거는 그냥 reverse 써서 뒤집어 줘야하나 ..? 

​

function solution(s) {
   
    return s.split('').sort().reverse().join('');
}
증답 

​

20. 부족한 금액 계산하기 

새로생긴 놀이기구는 인기가 매우 많아 줄이 끊이질 않는다  . 이 놀이기구의 원래 이용료는 price원인데 , 놀이기구를 N번 쨰 이용한다면 원래 이용료의 N배를 받기로 했습니다 즉, 처음 이용료가 100원 이었다면 2번째에는 200, 3번째에는 300 으로 요금이 인상된다 

놀이기구를 count 번 타게 되면 현재 자신이 가지고있는 금액에서 얼마가 모자라는지를 리턴하라 

금액이 부족하지 않으면 0을 리턴 

price money, count 가 제공되고 

for 로 반복로직 이 아니라 이건 while 문 

끝나는건 ㅑ <= count 까지  i ++ 을 

가격  * 해주고 

이게 끝났을때에 머니랑 뺀다 

빼고나서 요게 0원인지 0원 초과인지 

function solution(price, money, count) {
   let total = 0;
   let i = 0;
while (i <= count){
    total +=price*i
    i++
}
    const moneyZero = total - money

    return moneyZero > 0 ? moneyZero :0 ;
}
​

20문제 우선 끝 ! 

솔직히 pccp 준비 책을 읽지 않았으면 문제 읽고나서 내가 생각하는걸 적어서 정리해놓고 이걸 코딩으로 바꿔서 넣을줄은 몰랐을건데 책 좀 봤다고 문제가 그리 막막하지가 않다 먼저 내가 생각하는걸 정리하면 어떻게 풀어나가야할지 어 이거 아까 푼거랑 비슷한데 ? 라고 우선 이게 필요하구나 생각하고 

문제를 많이 접하고 지금 이 기록하는 습관을 유지해야겠다 

​

​

내일 피그마 공부하고 시간되면 5문제 정도 더 풀어봐야지 

​

​

​