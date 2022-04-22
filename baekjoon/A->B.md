# A->B(16953)
[문제 설명](https://www.acmicpc.net/problem/16953)

# 풀이
```swift
let input: [Int] = readLine()!.split(separator: " ").map({Int($0)!})

let startNum: Int = input[0]

var targetNum: Int = input[1]

var count: Int = 1

while targetNum > startNum {
    
    if targetNum % 2 == 0 {
        targetNum /= 2
    }else if targetNum % 10 == 1 {
        targetNum /= 10
    }else {
        break
    }
    
    count += 1
}

print(targetNum == startNum ? count : -1)
```

<br/>

한참 삽질을 했는데 B에서 A로 방법을 추적하면 간단하게 풀리는 문제였다.
<br/>
<br/>

b가 짝수인 경우 : /= 2 <br/>
b의 마지막 숫자가 1인 경우 : /= 10 (마지막 숫자 1 버리기) <br/>
그 외 : break (a로 돌아갈 수 없음)