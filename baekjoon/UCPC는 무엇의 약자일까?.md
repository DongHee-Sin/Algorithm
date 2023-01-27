# UCPC는 무엇의 약자일까?(15904)
[문제 설명](https://www.acmicpc.net/problem/15904)

<br/>

# 풀이
```swift
let inputString: String = readLine()!

func check() -> String {
    var ucpc: [Character] = ["U", "C", "P", "C"]
    
    for i in inputString {
        if i == ucpc[0] {
            ucpc.removeFirst()
            if ucpc.isEmpty { return "I love UCPC" }
        }
    }
    
    return "I hate UCPC"
}

print(check())
```
