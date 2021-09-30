# Programmers Weekly Challenge 8주차
## 문제 설명
명함 지갑을 만드는 회사에서 지갑의 크기를 정하려고 합니다. 다양한 모양과 크기의 명함들을 모두 수납할 수 있으면서, 작아서 들고 다니기 편한 지갑을 만들어야 합니다. 이러한 요건을 만족하는 지갑을 만들기 위해 디자인팀은 모든 명함의 가로 길이와 세로 길이를 조사했습니다.

아래 표는 4가지 명함의 가로 길이와 세로 길이를 나타냅니다.

명함 번호	가로 길이	세로 길이

1	60	50

2	30	70

3	60	30

4	80	40

가장 긴 가로 길이와 세로 길이가 각각 80, 70이기 때문에 80(가로) x 70(세로) 크기의 지갑을 만들면 모든 명함들을 수납할 수 있습니다.

하지만 2번 명함을 가로로 눕혀 수납한다면 80(가로) x 50(세로) 크기의 지갑으로 모든 명함들을 수납할 수 있습니다.

이때의 지갑 크기는 4000(=80 x 50)입니다.

모든 명함의 가로 길이와 세로 길이를 나타내는 2차원 배열 sizes가 매개변수로 주어집니다.

모든 명함을 수납할 수 있는 가장 작은 지갑을 만들 때, 지갑의 크기를 return 하도록 solution 함수를 완성해주세요.

## 제한사항

sizes의 길이는 1 이상 10,000 이하입니다.

sizes의 원소는 [w, h] 형식입니다.

w는 명함의 가로 길이를 나타냅니다.

h는 명함의 세로 길이를 나타냅니다.

w와 h는 1 이상 1,000 이하인 자연수입니다.

## 입출력 예

sizes	result

[[60, 50], [30, 70], [60, 30], [80, 40]]	4000

[[10, 7], [12, 3], [8, 15], [14, 7], [5, 15]]	120

[[14, 4], [19, 6], [6, 16], [18, 7], [7, 11]]	133

## 풀이

### 처음 풀었을때
```js
function solution(sizes) {
    let firstNum=[];
    let secondNum=[];


     const tt = sizes.map((card,i) => {

        card[0] < card[1] ?
            (firstNum.push(card[1]),
            secondNum.push(card[0])) :
            (firstNum.push(card[0]),
            secondNum.push(card[1]));
        firstNum.sort((a,b) =>
                b - a);
        secondNum.sort((a,b) =>
                b - a); 

    });
    var answer = firstNum[0]*secondNum[0];
    return answer;
}
```

## 코드 정리 후
```js
function solution(sizes) {
    let mostWidth = 0;
    let mostHeight = 0;
     sizes.forEach((item) => {
    const [width,height] = item.sort((a,b)=>b-a);
        width > mostWidth ? mostWidth = width : null;
        height > mostHeight ? mostHeight = height : null;
    });
    return mostHeight * mostWidth;
}
```

## 수정이유

배열이라서 push로 해결했으나 생각해보니 재할당으로 해결하는게 더 빠를것 같았음.


## 느낀점

처음 코드를 작성할 때부터 컨벤션을 생각하는게 좋을 것 같다.

무지성으로 생각의 흐름으로 풀어보니 시간복잡도가 높았고 이후 정리하는데 시간이 걸렸다.
