# A와 B(12904)
[문제 설명](https://www.acmicpc.net/problem/12904)

# 풀이
```swift
let start: String = readLine()!
var target: [String] = readLine()!.map({String($0)})

while target.count != start.count {
    
    guard target.last! != "A" else {
        target.removeLast()
        continue
    }
    
    target.removeLast()
    target = target.reversed()
    
}

print(target.joined(separator: "") == start ? 1 : 0)
```

<br/>

문제를 완전 잘못 이해하고 풀어서 한참 삽질했다;; <br/>
뒤집는다는게 A를 B로, B를 A로 뒤집는다는줄 알고 풀었음..; <br/>
유형은 백트래킹을 수행하면 쉽게 풀리는 문제라 바로 풀었다.

<br/>

### 문제를 **잘** 읽자...