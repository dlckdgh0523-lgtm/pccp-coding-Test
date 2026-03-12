문자열 다루기 기본 

문자열 s 의 길이가 4 혹은 6이고 , 숫자로만 구성돼있는지 확인해주는 함수, 솔루션을 완성하라

예를들아 s 가 "a234"이면 false를 리턴하고 "1234"라면 true 를 리턴하면 된다

​

문자열 길이가 4 또는 6자.. 인지를 확인하고 여기에 숫자인지 아닌지 를 알아야한다 

4 또는 6자가 아닐때에도 false 일테고 숫자로만 이루어져있냐 를 확인하면 될것같은데 

전부 다 훑어가면서 이게 숫자인지 확인을 해봐야하니 쪼개서 하나하나 검증 

for 문으로 i < 10 으로 잡아서 0 ~ 9 까지 만 돌게 .. 먼저 if 먼저 들어가야겠네 

if 안에 for문인가 for문안에 if 인가 

​

function solution(s) {
    if (s.length !== 4 && s.length !== 6){
        return false;
    }
    for (let i = 0; i < s.length; i++){
        if (s[i] < '0' || s[i] > '9'){
            return false;
        }
      
    }
    return true;
}
if 문으로 length 4 또는 6 이 아니면 false 나오게 해주고 for 

if s i 는 0 보다 작거나 9 보다 크면 false 

이 조건들을 통과시 true 보내주면 되네 

​

​

2.  행렬의 덧셈

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 

더한 결과가 된다 2개의 행렬 arr1 과 arr2 를 입력받아 행렬 덧셈의 결과를 반환하는 함수 솔루션을 완성하라 

​

말이 복잡하긴 하지만 입출력 예를 보니 결국 같은 자리에 있는것들끼리의 덧셈 

제한조건에 행과 열의 길이는 500을 넘지않는다 이건 for 문 쓰라는것 같은데 

for 이 필요한가 ? 이거 그냥 map으로  들어가면 끝날거같은데 

function solution(arr1, arr2) {
    
    return arr1.map((row, i) => row.map((val, j) => val + arr2[i][j] )
    ) ;
};
리턴 arr .map 을 해서 규칙을 정해줌과 동시에 행을 꺼내준다 row  i 는 인덱스 

row.map 으로 값을  val 로 꺼내주고 인덱스 j 를 꺼낸다 

여기 나온 값 val + arr 2 의 인덱스열 i j  같은것들의 좌표를 찍어준다

​

3. 직사각형 별찍기 

이문제에는 표준 입력으로 두개의 정수 n과 m 이 주어진다 

별 (*)문자를 이용해 가로의 길이가 n 세로의 길이가 m인 직사각형 형태를 출력해라 

아.. *로 그림그리는거 했던거 같은데 

for 문으로 return 값에  i ++ 대로 *이 찍히게 하면 되던 이중 for 문 세로 가로 

세로는 줄바꿈만  가로만 * 찍어주게 

process.stdin.setEncoding('utf8');
process.stdin.on('data', data => {
    const n = data.split(" ");
    const a = Number(n[0]), b = Number(n[1]);
    
    for (let i = 0; i < b; i ++){
        let str = "";
    
    for (let j = 0; j < a; j++){
       str = str + "*";
    }
    console.log(str)}
   
});
​

​

4. 같은 숫자는 싫어 

배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져있다 . 이때 배열 arr에서

연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려한다. 단 제거된 후 남은수들을 반환할때는

배열 arr 의 원소들이 순서를 유지해야한다 예를들면 

arr [1,1,3,3,0,1,1] 이면 [1,3,0,1] 을 리던해야한다 

같은수끼리 배열이 나오면 이것들을 .. filter 로 없애버리면 될것도 같은데 

​

function solution(arr)
{
 
    
    return arr.filter((val, index)=> {return val !== arr[index + 1] });
};
arr filter 로 val index 잡아주고 내 뒤에 있는 숫자랑 다르면 남게 

val ! == arr ~~ 이건 

같지 않으면 ! true 주고 틀릴때 false 

그러니 같은값은 사라지고 다른값은 남는다 

​

5.최대공약수와 최소 공배수 

두수를 입력받아 두 수의 최대 공약수와 최소 공배수를 반환하는 함수 솔루션을 완성해라 

배열의 맨 앞에 최대 공약수 , 그다음 최소공약수를 반환하면 된다 

예를들어 두 수 3 , 12 의 최대 공약수는 3 최소 공배수는 12 이므로 솔루션 3, 12 는 3,12 를 반환 

최대공약수 = 두 수의 약수중 가장 큰것

최소공배수 = 두 수위 배수중 가장 작은것 

return 할때에 [최대 , 최소 ]        let으로 선언들어가주고 

약수를 구하는건 

function solution (n) {
 let answer = 0;
 for (let i = 0; i <= n; i++){
     if (n % i === 0){
     answer += i;
     }
 }
 return answer;
}
이 문제에서 했었는데 이걸 좀 변형을 시켜서 

n % i === 0 

m % i === 0 해서 같은거 ? 

똑같이 for문 들어가고 

Math.min 으로 최솟값 

answer 는 1도 해당되는 1 로 들어가고 

최소공배수는 두수를 곱하고 / 구한 최대공약수를 하면 될것같은데 

function solution(n, m) {
    var answer = 1;
    for (let i = 0;i <= Math.min(n,m);i++ ){
        if (n % i === 0 && m % i === 0){
            min = i;
        }
    }

    let max = (n * m) / min;
    
    return [min,max];
};
위에서 풀어봤던 문제랑 다르게 이건 n 과 m 의 약수를 구하되 최소값을 구하는거니 

Math.min (n,m)  

if n m 이 둘다 같이 0으로 떨어지는수를 min 이랑 같다 라고 선언

max는 n *M 하고 min으로 나누면 끝 

​

​

6.크기가 작은 부분문자열 

숫자로 이루어진 문자열 t 와 p가 주어질때, t에서 p와 길이가 같은 부분문자열 중에서, 이 부분문자열이 

나타내는 수가 p가 나타내는 수보다 작거나 같은것이 나오는 횟수를 리턴하는 솔루션을 완성하라 

예를들어 t = "3141592" 이고 p= "271"인 경우 t의 길이가 3인 부분문자열은 314 141 415 159 592 이다 이 문자열이 나타내는 수중 271 보다 작거나 같은수는 141 159 두개이다 

​

t 와 p 아니 p의 인덱스 개수를 먼저 구해서 t에다가 조건을 걸어준다 

그러고 비교를 하는데 작거나 같은것을 구한다 

먼저 p.length 선언 

for 문 들어가주고 

slice 쓸수 있을것같은데 

if 문 들어가서 비교까지 해준다 

function solution(t, p) {
   let count = 0;
   let pl = p.length;
    for (let i = 0; i <= t.length - pl; i ++){
        let tStr = t.slice(i,i + pl );
        if (Number(tStr) <= Number(p) ){
            count ++
        }
    }
    return count;
}
카운트 = 횟수 카운트 

pl 은 p.length 

for i < = t.length - pl 은 t.length 에서 pl 만큼 빼면 남은 인덱스를 알수 있으니 다음 p.length 만큼 t를 쪼갤수 있다 

tStr t.slice 는 이제 시작점에서 pl 만큼 더한곳 직전까지 자른다 

이걸 if문에 넣어서 비교를 해주고 참이면 count  1 씩 증가 

리턴 카운트 

​

7.삼총사

한국중학교에 다니는 학생들은 각자 정수번호를 갖고있다 . 이 학교 학생 3명의 정수번호를 더했을때 0이 되면 

3명의 학생들은 삼총사라 불린다 

예를들어 5명의 학생이 있고 각각의 정수ㅡ번호가 순서대로 -2 3 0 2 -5 일때 첫번째 새번째 네번쨰 학생의 정수번호를 더하면 0이 되므로 세 학생은 삼총사이다 

또한 2 4 5 학생들을 더할경우에도 0이니 이 학생들도 삼총사다 

따라서 이 경우 한국중학교에서는 두가지 방법으로 삼총사를 만들 수 있다 

한국중학교의 학생 번호를 나타내는 정수 넘버가 주어질때 

​

배열로 쪼개서  하나씩 더해본다 ... 여기서 0이 되는것을 찾는다 

다만 값은  반드시 3개가 필요하다 .. for문이면 될거같은데 

​

function solution(number) {
    var count = 0;
    for (let i = 0 ; i < number.length; i ++){
        for (let j = i + 1; j < number.length; j++){
            for(let k = j + 1; k < number.length;k++){
                if(number[i]+number[j]+number[k] === 0){
                    count ++
                }
            }
        }
    }
    return count;
}
처음에 for문 뒤 i j k 값을 다 0으로 넣었더니 값은 나오는데 오답이 나와서 

생각을 해봤는데 서로 자리수가 다른거로 비벼봐야 하니 전의 것에 + 1 을 기준으로 잡아준다 

이렇게 하니 풀렸네 

​

8. 예산 

s사에서는 각 부서에 필요한 물품을 지원해 주기 위해 부서별로 물품을 구매하는데 필요한 금액을 조사했다

그러나 전체 예산이 정해져 있기 떄문에 모든 부서의 물품을 구매해 줄 수는 없다

그래서 최대한 많은 부서의 물품을 구매해 줄 수 있도록 하려고 한다

물품을 구매해 줄 때는 각 부서가 신청한 금액만큼을 모두 지원해줘야한다

예를들어 1000원을 신청한 부서에는 정확히 1000 원을 지원하며 1000원보다 부족한 금액을 지원해줄수는 없다 

부서별로 신청한 금액이 들어있는 배열 b 와 예산 budget이 주어질때 최대 몇개의 부서에 물품을 지원 가능한지 리턴하라 

​

이거 7번문제랑 비슷한 흐름인것같은데 이 문제는 .. 삼총사처럼 몇개인지 정해져 있는게 없다 

그러니 for을 3중으로 만들 필요 없이 

for 하나로  b를 쪼개서 각각 더한값이 budget보다 같거나 작다

sort 를 넣어줘서 작은값부터 치루게 .. 조건을 보면 최대한 많이 지원해준다한다 

최대한 많은부서에 지원해주려면 적은값부터 계산을 해야한다 

​

 

function solution(d, budget) {
    var answer = 0;
    d.sort((a, b) => a - b );
    for (let i = 0; i < d.length; i ++){
        if (budget >= d[i]){
            budget -= d[i];
            answer++
        } else {
            break; 
        }
    }
    return answer;
}
9.3진법 뒤집기

자연수 n이 매개변수로 주어진다 n을 3진법 상에서 앞뒤로 뒤집은 후 이를 다시 10진법으로 표한한 수를 리턴하라 

우선 n은 10진법인걸 3진법으로 바꾸고 이걸 배열뒤집어서 10진법으로 나타내라 

sort 써서 뒤집어주고 b-a 

3진법으로 교체를 어떻게하지 .. 이건 검색 toString()을 쓰면 된다한다

이건 괄호안에 숫자 뭘 넣든 그 진법으로 교체해준다나 .. 

다시 10진법으로 돌릴때는 parseInt 

    return n.toString(3).sort((a,b) => b - a).parseInt(n,3); 

오답 .. 뭔가 잘못된거같은데 .. 모르겠으니 힌트 찾아보자 

​

function solution(n) {
    let answer = n.toString(3).split('').reverse().join('');
    
    return parseInt(answer,3);
}
​

여기선 sort 를 하지 않는다 이건 배열을 오름 내림차순으로 하는거고 이 문제에선 그냥 뒤집는것 이니깐 

.split('').reverse().join('');  이건 배열 뒤집기에 쓰이니 꼭 기억 

​

parseInt는 .parsInt 로 사용하지 못하니 따로 빼줘야한다고 한다 

​

​

10. 이상한 문자 만들기 

문자열 s 는 한 개 이상의 단어로 구성되어있다 . 각 단어는 하나 이상의 공백 문자로 구분되어있다 

각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수 솔루션을 완성하라 

기본 사용법

소문자 → 대문자: str.toUpperCase()를 호출하면 모든 문자가 대문자로 변환된 새 문자열이 반환됩니다. 1 3

대문자 → 소문자: str.toLowerCase()를 호출하면 모든 문자가 소문자로 변환된 새 문자열이 반환됩니다. 1 3

​

라고 한다  이걸 사용하면 될것같다 

단어를 기준으로 짝 홀수를 정한다 .. 

단어별로 각각 띠어서 여기서 홀수 짝수를 구하고 이걸 어퍼 로우 갈겨준다 

단어................. 트라이 헬로 월드 라 할때 기준을 공백 공백을 잡고 split 해서 쪼개준다 

위에것처럼 뒤집을건 없으니 reverse 뺴고 join 들어가주고 

map으로 각 단어 나눠서 짝 홀수 %2 === 0 으로 가려주고 

if네 

function solution(s) {
    
    return s.split(' ').map(pizza => {
        return pizza.split('').map((min, index) => {
            return index % 2 === 0 ? min.toUpperCase() : min.toLowerCase();
        }).join('');
    }).join (' ');
}
s.split ('') 를 할때에 공백을 기준으로 쪼개기로 했으니 띄워쓰기 한번 들어가주고 거기에 map 하나하나 해야하니 

 다음 

pizza.split 에서는 하나하나 나눠야 하기에 띄워쓰기는 제하고 map min 하고 index 구해주고 

index % 2 === 0 이면 짝수  ? 는 if 문과 같은 효과 : else 랑 같은 뜻 

join 도 '' 띄워쓰기 없는것부터 붙혀주고 밖에서 join ' ' 해주면 끝 .. 

이건 방향은 알겠는데 자꾸 오답이 나오고 모르겠어서 힌트 보면서 진행했습니다 

​

 11. 최소 직사각형

명함지갑을 만드는 회사에서 지갑의 크기를 정하려 한다 .

다양한 모양과 다양한 크기의 명함들을 모두 수납할 수 있으면서 

작아서 들고 다니기 편한 지갑을 만들기 위해 디자인팀은 모든 명함의 가로 길이와 세로 길이를 조사했다

아래 표는 4가지 명함의 가로길이와 세로 길이를 나타낸다 

명함번호 1 가로 60 세로 50

        2 가로 30 세로 70

        3 가로 60 세로 30

        4 가로 80 세로 40 

가장 긴 가로와 세로 길이가 각각 80 70 이기 때문에 가로 80 * 세로 70 크기의 지갑을 만들면 

모든 명함을 수납할수있다 하지만 2번 명함 을 나로로 눕혀 수납한다면 가로 80 * 세로 50 크기의 지갑으로 모든 명함을 수납할 수 있다.

이때 지갑 크기는 4000 (= 80 * 50)이다

모든 명함의 가로길이와 세로길이를 나타내는 2차원 배열 sizes 가 매개변수로 주어진다 모든 명함을 수납할 수 있는 가장 작은 지갑을 만들 떄, 지갑의 크기를 리턴하도록 솔루션 함수를 만들라 
​

음 .. 사이즈는 하나로 가로 세로가 주어지고  한번에 주어진다 

가로 중 가장 긴거 찾고 세로중 길면서 짧은걸 찾아라 

​

for 들어가고 sizes.length 

[] 배열 선언들어가주고 

max , min 값 구해서  선언해주고

가로 세로 값 선언해둔거에 입혀주고 

리턴 곱하기 

​

function solution(sizes) {
    let maxWidth = 0 ;
    let maxHeight = 0 ;
    
    for (let i = 0; i < sizes.length; i++){
        const [w , h ] = sizes[i];
        const longSide = Math.max(w , h);
        const shortSide = Math.min(w , h );
        maxWidth = Math.max(maxWidth , longSide);
        maxHeight = Math.max(maxHeight , shortSide);
    }
    return maxWidth * maxHeight;
}
 12 가장 가까운 같은 글자 

문자열 s 가 주어졌을때, s의 각 위치마다 자신보다 앞에 나왔으면서 , 자신과 가장 가까운 곳에 있는 같은 글자가 어디 있는지 알고싶다 

예를들어 s = banana 라고 할때 , 각 글자들을 왼쪽부터 오른쪽으로 읽어 나가면서 다음과 같이 진행할 수 있다 

음 처음나오는 문자열은 -1 처리 그리고 뒤에 나온 문자열중에 이미 처리가 된 문자열이 있다면 그 문자열과의 index 계산 

for 들어가서 s.length 해주고 

안에 if 로 -1 이거나 자릿값 i - index 

i 로 갱신해주고 리턴 

​

function solution(s) {
    var answer = [];
    let lastindex = {};
    
    for (let i = 0;i < s.length ; i++){
        let index = s[i];
        if (lastindex[index] === undefined){
            answer.push(-1);
        }else {
            answer.push(i - lastindex[index]);
        }
        lastindex[index] = i;
        
        
        
    }
    return answer;
}
13 . 시저 암호 

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라 한다 예를들어 "AB"는 1만큼 밀면 "BC"가 되고 , 3만큼 밀면 "DE"가 된다 . "z"는 1만큼 밀면 "a"가 된다 

문자열 s와 거리 n 을입력받아 s 를 n 만큼 민 암호문을 만드는 함수 솔루션을 만들라 

소 대문자 구별할 필요 없이 그냥 들어오는대로 바꿔준다 . 소 = 소 대 = 대 

length 로 쪼개주고 하나씩 push 해준다 ? 

이거 비슷한 문제에서 문자열 대할때 toUpperCase 랑 toLowCase 썻던게 생각나는데 

아......일단 컴퓨터는 알파벳 모르잖아 

컴퓨터한테 알려주고 .. if  대소문자 적용해주고 

순환하는거 알파벳 총 26자 

​

function solution(s, n) {
    const alphabet = "abcdefghijklmnopqrstuvwxyz"
    let result = "";
    
    for (let i = 0 ; i < s.length; i ++){
        let index = s[i];
        if ( index === " "){
            result += " ";
            continue;
        }
        let isUpper = (index === index.toUpperCase());
        let isLower =index.toLowerCase();
        let findindex = alphabet.indexOf(isLower);
        let newIndex = (findindex + n) % 26;
        let shiftedindex = alphabet[newIndex];
        if (isUpper){
            result += shiftedindex.toUpperCase();
        }else {
            result += shiftedindex;
        }
    }
    return result;
}
공백 잡아주고 어퍼 로월 선언 찾고 넣어주고 순환 

대문자면 대문자로 변환  소문자면 그냥 내보낸다 

아 이거 진짜 너무 복잡한거같아서 질문하기 좀 뒤져보고 풀었습니다 

생각은 얼추 맞는거같았는데 스키드 ? 스키디 ? 어후 이런게 있다고 하는데 

일단은 패스 

​

14. 푸드 파이트 대회

수웅이는 매달 주어진 음식을 빨리 먹는 푸드 파이트 대회를 개최합니다.

이 대회에서 선수들은 1대 1로 대결하며, 매  대결마다 음식의 종류와 양이 바뀝니다.

*대결은 준비된 음식을 일렬로 배치한 뒤 *,* 한 선수는 제일 왼쪽에 잇는 음식부터 오른쪽으로 *

*다른 선수는 제일 오른쪽에 있는 음식부터 왼쪽으로 순서대로 먹는 방식으로 * 진행 됩니다 

*중앙에는 물을 배치하고 , 물을 먼저 먹는 선수가 승리 * 

이때 대회의 공정성을 위해  *두 선수가 먹는 음식의 종류와 양이 같아야 하며 , 음식을 먹는 순서도 같아야 합니다 * 또한, 이번 대회부터는 *칼로리가 낮은 음식을 먼저 먹을 수 있게 배치하여 * 선수들이 음식을 더 잘 먹을 수 있게 하려고 합니다. 이번 대회를 위해 수웅이는 음식을 주문했는데, 대회의 조건을 고려하지 않고 음식을 주문하여 몇 개의 음식은 대회에 사용하지 못하게 되었습니다 .

예를들어 , 3가지 음식이 준비되어 있으며 , 칼로리가 적은 순서대로 1번음식을 3개 2번음식을 4개 3번음식을 6개 준비했으며 , 물을 편의상 0번 음식이라 칭한다면 두ㅡ 선수는 1번음식 1개 , 2번음식 2개 3번음식 3개씩을 먹게됨으로 음식의 배치는 1223330333221 이 된다 

따라서 1번음식 1개는 대회에 사용하지 못한다 

이게 뭔 소린지 모르겠는데 .. 가운데에 0을 넣어주되 .. 이건 뭐 food length  해주고 왼쪽 오른쪽 분리 시켜서 .. for 문 ..  Math.floor 로 2로 나누고 소수점 제외 

오른쪽은 배열을 뒤에서부터 와야하니 반대로 들어가주고 .. length -1  i -- 

   

function solution(food) {
    var left = '';
    for ( let i = 1; i < food.length ; i ++){
        let count = Math.floor(food[i]/2);
        for (let j = 0; j < count; j++){
            left += i;
        }
    }
        
    let right = "";
        for (let i = left.length -1 ; i >= 0; i -- ){
            right += left[i];
        }
    return left + "0" + right;
    }
    
15 . 두 개 뽑아서 더하기 .

정수 배열 numbers가 주어진다 

numbers 에서 서로 다른 인덱스에 있는 수 끼리 더해서 나올 수 있는 모든 수를 배열에 오름차순으로 넣어라 

​

응 그냥 하나하나 뽑아서 다 더하고 중복 된건 그냥 하나로 표시해주고 

오름차순 

​

function solution(numbers) {
    var answer = [];
    for (let i = 0; i < numbers.length ; i ++){
        for (let j = i + 1 ; j < numbers.length; j ++){
            answer.push(numbers[i]+numbers[j]);
        }
        
    }
    const result = [... new Set(answer)].sort((a , b) => a - b);
    return result;
}

 

16. 프로그래머스 사이트를 운영하는 그렙에서는 재택근무와 함께 출근 희망시각을 자유롭게 정하는 유연금누제를 시행하고 있습니다. 제도 정착을 위해 오늘부터 일주일 동안 각자 설정한 출근 희망 시각에 

늦지 않고 출근한 직웑들에게 상품을 주는 이벤트를 진행하려 합니다 

직원들은 일주일동안 자신이 설정한 출근희망시각 + 10 분 까지 어플로 출근해야합니다 

예를들어 출근 희망시각이 9시 58분인 직원은 10시 8분까지 출근해야합니다. 

단 토요일 일요일의 출근 시각은 이벤트에 영향을 끼치지 않습니다 . 

직원들은 매일 한 번씩만 어플로 출근하고, 모든 시각은 시에 100을 곱하고 분을 더한 정수로 

표현됩니다. 예를들어 10시 13분은 1013이 되고 9시 58분은 958이 됩니다 

당신은 직원들이 설정한 출근희망 시각과 실제로 출근한 기록을 바탕으로 상품을 받을

직원이 몇명인지 알고 싶습니다.  직원 n명이 설정한 출근 희망 시각을 담은 

1차원 정수 배열 schedules, 직원들이 일주일동안 출근한 시각을 담은 2차원 정수 배열

timelogs, 이벤트를 시작한 요일을 의미하는 정수 startday, 가 매개변수로 주어집니다.

이 떄 상품을 받을 직원의 수를 리턴하도록 만들라 

​

schedules 가 희망시각 이니 이거랑 timelogs 랑 비교를해서 받은 n에서 맞지 않는다면

flase , 시작한 요일 .. 요일이 언제든지 주말은 계산에 넣지 않는다 

1이 월요일 , 6 7 은 카운트 하지 않고 스케줄 사람들 쪼개주고 

7일 반복문 만들어주고 

if 문 들어가주고 , 

function solution(schedules, timelogs, startday) {
    var answer = 0;

  
    for (let i = 0; i < schedules.length; i++) {
        
        let isSuccess = true; 
        for (let j = 0; j < 7; j++) {
            
           
            let currentDay = (startday + j) % 7;
            if (currentDay === 0) currentDay = 7;

            
            if (currentDay === 6 || currentDay === 7) {
                continue;
            }

           
            let schdhour = Math.floor(schedules[i] / 100);
            let schedmin = schedules[i] % 100;
            let deadline = (schdhour * 60) + schedmin + 10;

            
            let timehour = Math.floor(timelogs[i][j] / 100);
            let timemin = timelogs[i][j] % 100;
            let arrival = (timehour * 60) + timemin; 
            if (arrival > deadline) {
                isSuccess = false; 
                break;
            }
        }
        if (isSuccess) {
            answer++;
        }
    }
    return answer;
}
          
17 . 

당신은 동영상 재생기를 만들고 있습니다. 당신의 동영상 재생기는 10초 전으로 이동, 10초 후로 이동, 오프닝 건너뛰기 3가지 기능을 지원합니다. 각 기능이 수행하는 작업은 다음과 같습니다.

10초 전으로 이동: 사용자가 "prev" 명령을 입력할 경우 동영상의 재생 위치를 현재 위치에서 10초 전으로 이동합니다. 현재 위치가 10초 미만인 경우 영상의 처음 위치로 이동합니다. 영상의 처음 위치는 0분 0초입니다.

10초 후로 이동: 사용자가 "next" 명령을 입력할 경우 동영상의 재생 위치를 현재 위치에서 10초 후로 이동합니다. 동영상의 남은 시간이 10초 미만일 경우 영상의 마지막 위치로 이동합니다. 영상의 마지막 위치는 동영상의 길이와 같습니다.​

오프닝 건너뛰기: 현재 재생 위치가 오프닝 구간(op_start ≤ 현재 재생 위치 ≤ op_end)인 경우 자동으로 오프닝이 끝나는 위치로 이동합니다.

동영상의 길이를 나타내는 문자열 video_len, 기능이 수행되기 직전의 재생위치를 나타내는 문자열 pos, 오프닝 시작 시각을 나타내는 문자열 op_start, 오프닝이 끝나는 시각을 나타내는 문자열 op_end, 사용자의 입력을 나타내는 1차원 문자열 배열 commands가 매개변수로 주어집니다. 이때 사용자의 입력이 모두 끝난 후 동영상의 위치를 "​mm:ss" 형식으로 return 하도록 solution 함수를 완성해 주세요.

prev = 10 초 전 "동영상의 남은 길이가 10초 미만일경우 처음으로 "

 next = 10초 후 "동영상의 남은시간이 10초 미만일경우 영상의 마지막으로  = 영상의 마지막 위치는 동영상 길이와 같음 "

op_start <= 현재 재생 위치 < op_end 

사용자의 입력이 랜덤으로 들어올떄 현재 위치 mm:ss 를 구하라 인데 

기준시간 넣어두고 

조건 들어가주고 반복문 두개  prev 랑 next 꺼 

넥스트랑 프리브  진행할때  pov 에 10초만큼 ++ 

오프닝 건너뛰기할시 다시 돌아올수도 있다는 조건하에 

pov와 대조 / 오프닝 시간 계산 로직 

 

​

 

당신은 동영상 재생기를 만들고 있습니다. 당신의 동영상 재생기는 10초 전으로 이동, 10초 후로 이동, 오프닝 건너뛰기 3가지 기능을 지원합니다. 각 기능이 수행하는 작업은 다음과 같습니다.

10초 전으로 이동: 사용자가 "prev" 명령을 입력할 경우 동영상의 재생 위치를 현재 위치에서 10초 전으로 이동합니다. 현재 위치가 10초 미만인 경우 영상의 처음 위치로 이동합니다. 영상의 처음 위치는 0분 0초입니다.

10초 후로 이동: 사용자가 "next" 명령을 입력할 경우 동영상의 재생 위치를 현재 위치에서 10초 후로 이동합니다. 동영상의 남은 시간이 10초 미만일 경우 영상의 마지막 위치로 이동합니다. 영상의 마지막 위치는 동영상의 길이와 같습니다.​

오프닝 건너뛰기: 현재 재생 위치가 오프닝 구간(op_start ≤ 현재 재생 위치 ≤ op_end)인 경우 자동으로 오프닝이 끝나는 위치로 이동합니다.

동영상의 길이를 나타내는 문자열 video_len, 기능이 수행되기 직전의 재생위치를 나타내는 문자열 pos, 오프닝 시작 시각을 나타내는 문자열 op_start, 오프닝이 끝나는 시각을 나타내는 문자열 op_end, 사용자의 입력을 나타내는 1차원 문자열 배열 commands가 매개변수로 주어집니다. 이때 사용자의 입력이 모두 끝난 후 동영상의 위치를 "​mm:ss" 형식으로 return 하도록 solution 함수를 완성해 주세요.

prev = 10 초 전 "동영상의 남은 길이가 10초 미만일경우 처음으로 "

 next = 10초 후 "동영상의 남은시간이 10초 미만일경우 영상의 마지막으로  = 영상의 마지막 위치는 동영상 길이와 같음 "

op_start <= 현재 재생 위치 < op_end 

사용자의 입력이 랜덤으로 들어올떄 현재 위치 mm:ss 를 구하라 인데 

기준시간 넣어두고 

조건 들어가주고 반복문 두개  prev 랑 next 꺼 

넥스트랑 프리브  진행할때  pov 에 10초만큼 ++ 

오프닝 건너뛰기할시 다시 돌아올수도 있다는 조건하에 

지금 시간이 오프닝 진행중이라면 스킵 

​

function solution (){
  let cur_s = convertToSec(pos)
  const end_s = convertToSec(videoo_len)

  if(is_inside_op(cur_s, op_start, op_end)){
cur_s = convertToSec (op_end)
}

commands.forEach(command => (
 if (command === 'next') {
  cur_s = next(cur_s , end_s)
   }else {
     cur_s = prev(cur_s , end_s )
}
    if (is_inside_op (cur_s, op_start ,op_end ){
      cur_s = convertToSec(op_end)
} 
)
   )return convertToFormatString(cur_s);
)
  function next (cur_sec , end_sec){
 const result = cur_sec + 10 
 if (result >= end_sec){
     retunr end_sec 
}
return result 


}
function (perv){
const result = cur_sec - 10 
if (result < 0)
    rerurn 0
}
    return result 
}
function is_inside_op(cur_sec , op_start, op_end){
 const [m , s] = formatString.split(':').map(Number) 
    return 60*m + s

    }

function convertToFormatString(sec){
  const m = String (Math.floor(sec / 60 )).padStart(2,"0")
  const s = String (sec % 60 ).padStart(2,"0")
return m + ':' + s

 function converToSec ( sec ){
 const s = String (sec % 60 ). padStart (2,"0")
return ":" + s  }
}



​

 

라고 로직을 짜보긴 했는데 오답 .. 

분 초 쪼개주고 자리 선언해주고 

​

function solution(video_len, pos, op_start, op_end, commands) {
  const convertToSec = (timeStr) => {
    const [m, s] = timeStr.split(':').map(Number);
    return m * 60 + s;
  };

  const convertToFormatString = (sec) => {
    const m = String(Math.floor(sec / 60)).padStart(2, "0");
    const s = String(sec % 60).padStart(2, "0");
    return `${m}:${s}`;
  };

  let cur_s = convertToSec(pos);
  const end_s = convertToSec(video_len);
  const start_op_s = convertToSec(op_start);
  const end_op_s = convertToSec(op_end);

  const checkAndSkipOp = (s) => {
    if (s >= start_op_s && s <= end_op_s) {
      return end_op_s;
    }
    return s;
  };

  cur_s = checkAndSkipOp(cur_s);

  commands.forEach(command => {
    if (command === 'next') {
      cur_s = Math.min(end_s, cur_s + 10);
    } else {
      cur_s = Math.max(0, cur_s - 10);
    }
    cur_s = checkAndSkipOp(cur_s);
  });

  return convertToFormatString(cur_s);
}
​

​

18.  선물을 직접 전하기 힘들 떄 카카오톡 선물하기 기능을 이용해 축하 선물을 보낼 수 있습니다.

당신의 친구들이 이번달까지 선물을 주고받은 기록을 바탕으로 다음 달에 누가 선물을 많이 받을지 예측하려고 합니다 

*두 사람이 선물을 주고받은 기록이 있다면 , 이번달 까지 두 사람 사이에 더 많은 선물을 준 사람이 다음달에 선물을 하나 받습니다. 

   예를들어 a 가 b에게 선물을 5번 줬고 ,

   b가 a에게 선물을 3번 줬다면 다음달엔 a가 b 에게 선물을 하나 받습니다 .

*두 사람이 선물을 주고받은 기록이 하나도 없거나 주고받은 수가 같다면, 선물 지수가 더 큰 사람이 선물지수가 더 작은 사람에게 선물을 하나 받습니다. 

   선물 지수는 이번달까지 자신이 친구들에게 준 선물의 수에서 받은 선물의 수를 뺀 값입니다. 

   예를들어 a 가 친구들에게 준 선물이 3개고 받은 선물이 10개라면 선물지수는 -7 입니다 

   b 가 친구들에게 준 선물이 3개고 받은 선물이 2개라면 , b 의 선물지수는 1 입니다. 

만약 a와  b가 선물을 주고받은적이 없거나 정확히 같은 수로 선물을 주고받았다면 , 다음 달엔 b가 a에게 선물을 하나 받습니다. 

위에서 설명한 규칙대로 다음 달에 선물을 주고받을 때 , 당신은 선물을 가장 많이 받을 친구가 받을 선물의 수를 알고 싶습니다 .

​

친구들의 이름을 담은 1차원 문자배열 friends 이번달까지 친구들이 주고받은 선물기록을 담은 1차원 문자열배열 gifts 가 매개변수로 주어ㅗ진다 

이때 다음달에 선물을 가장 많이 받을 친구가 받는 선물의 수를 리턴 

​

하나하나 카운트 해다가 프렌드로 입력을 받으니 .. 프랜드에서 받을 값에 gifts++ 

선물을 받은 값을 구해서 - 서로 주고받은 값 큰사람이 선물받으니  + 

function solution(friends, gifts) {
  const n = friends.length;
  const friendIndex = {};
  friends.forEach((name, idx) => {
    friendIndex[name] = idx;
  });

  const giftMatrix = Array.from({ length: n }, () => Array(n).fill(0));
  const giftScore = Array(n).fill(0);

  gifts.forEach(gift => {
    const [giver, receiver] = gift.split(' ');
    const giverIdx = friendIndex[giver];
    const receiverIdx = friendIndex[receiver];
    
    giftMatrix[giverIdx][receiverIdx]++;
    giftScore[giverIdx]++;
    giftScore[receiverIdx]--;
  });

  const nextMonthGifts = Array(n).fill(0);

  for (let i = 0; i < n; i++) {
    for (let j = i + 1; j < n; j++) {
      const iToJ = giftMatrix[i][j];
      const jToI = giftMatrix[j][i];

      if (iToJ > jToI) {
        nextMonthGifts[i]++;
      } else if (iToJ < jToI) {
        nextMonthGifts[j]++;
      } else {
        if (giftScore[i] > giftScore[j]) {
          nextMonthGifts[i]++;
        } else if (giftScore[i] < giftScore[j]) {
          nextMonthGifts[j]++;
        }
      }
    }
  }

  return Math.max(...nextMonthGifts, 0);
}
이름을 인식하지 못하니 이름을 index 숫자로 변환 한다 

​네오와 프로도가 숫자놀이를 하고 있습니다. 네오가 프로도에게 숫자를 건넬 떄 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다 . 

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다 .

1478 - > one4seveneight 

234567 - > 23four5six7

10203 - > 1 zerotwozero3

  0 ~ 9 선언하고 for split 쪼개주고 join 으로 다시 병합 

function solution (s) {
 const word = {
 zero : '0',
 one : '1' ,
 two : '2' ,
 three : '3',
 four : '4',
 five : '5',
 six : '6',
 seven : '7',
 eight : '8',
 nine : '9' ,
}
for ( key in word ) {
      s = s.split(key).join(word[key]) } 
return Number(s)
}

k 번째 수   

배열 array 의 i 번째 숫자부터 j 번째 숫자까지 자르고 정렬했을때 , 

k 번째에 있는 숫자를 구하려고 합니다 

예를들어 array가 [1,5,2,6,3,7,4] , i = 2 . j = 5 . k = 3이라면 

블라블라 ~~ 이해 했는데 이문제는 인덱스를  0 부터 세지 않는다

i < j    안쪽에 있는 수를 잡아와서 정렬하고  여기서 k 번째  수를 꺼내라 

SLICE , PUSH , FOR  , SORT 

function solution (array , commands ) {
 let answer = [];
 for (command of commands ) {
      let [i , j , k ]   =  command ; 
 let sliced = array.slice(i - 1 , j ); 
 sliced.sort ((a,b) => a - b );

answer.push (sliced[k - 1 ])

}


}
​

콜라문제 

오래전 유행했던 콜라 문제가 있습니다 . 콜라 문제의 지문은 다음과 같습니다 

정답은 아무에게도 말하지 마세요 . 

콜라 빈 병 2 개를 가져다주면 콜라 1병을 주는 마트가 있다 . 

빈병 20 개를 가져다주면 몇병을 받을 수 있는가 ? 

단, 보유중인 빈병이 2개 미만이라면 콜라를 받을 수 없다 

​

문제를 풀던 살빈이는 콜라문제의 완벽한 해답을 찾았다 

상빈이가 푼 방법은 다음과 같아 우선 콜라 빈병 20 병을 가져가서 10 병을 받는다 

받은 10 병을 모두 마신 뒤 가져가서 5병을 받는다 

5병중 마신 4병을 모두 가져가서 2 병을 받고 또 2병을 모두 마신뒤 가져가서 1병을 받는다 

받은 1 병과 5병을 받았을때 남은 1병을 마신뒤 가져가면 1 병을 또 받을 수 있다 

10 + 5 + 2 + 1 + 1 = 19 병의 콜라를 마셨다 

​

빈병 a 개를 가져다 줬을때 콜ㄹ다 b 병을 주는 마트가 있을때 빈병 n 개를 가져다 주면 마실 수 있는 콜라를 리턴하라 

​

n 을 a로 나눠주고 그 개수를 뭐 ..  newA 라 하고 

b랑 곱해주고  또 a 로 나눌수 있으면 나누고 while  문으로 더이상 a 로 나눌 수 없을때까지 

그 값을 리턴  

​

​

function solution (n , a , b ) {
 let answer = 0;
 while(n>=a ) {
 const exchanged = Math.floor(n / a );
 const newCola =exchanged * b 


 answer += newCola ;
 n = ( n % a) + newCola ;

}

return answer ;

}
명예의 전당 

명예의 전당이라는 tv 프로그램에서는 매일 1명의 가수가 노래를 부르고 , 시청자들의 문자 투표수로 가수에게 점수를 부여합니다 . 

매일 출연한 가수의 점수가 지금까지 출연가수들의 점수 중 상위 k 번째 이내라면 해당 가수의 점수를 명예의 전당이라는 목록에 올려 기념합니다. 즉 프로그램 시작 이후 초기에 k 일까지는 모든 출연 가수의 점수가 ...... ~~~~ 

​