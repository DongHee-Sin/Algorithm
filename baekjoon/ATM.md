# ATM(11399)
[문제 설명](https://www.acmicpc.net/problem/11399)

# 풀이
```swift
let input: String = readLine()!

let timeArray: [Int] = readLine()!.split(separator: " ").map({Int($0)!}).sorted()

var result: Int = 0
var time: Int = 0

for tm in timeArray {
    time += tm
    
    result += time
}

print(result)
```
