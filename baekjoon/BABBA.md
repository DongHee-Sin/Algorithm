# BABBA(9625)
[문제 설명](https://www.acmicpc.net/problem/9625)

# 풀이
```swift
func solution() {
    let n: Int = Int(readLine()!)!
    
    guard n > 1 else {
        print("0 1")
        return
    }
    
    var dpTable: [(Int, Int)] = Array(repeating: (0, 0), count: n+1)
    dpTable[1] = (0, 1)
    
    
    for i in 2...n {
        dpTable[i].0 = dpTable[i-1].1
        dpTable[i].1 = (dpTable[i-1].0 + dpTable[i-1].1)
    }
    
    print("\(dpTable[n].0) \(dpTable[n].1)")
}

solution()
```
