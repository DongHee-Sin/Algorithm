# AC(5430)
[문제 설명](https://www.acmicpc.net/problem/5430)

# 풀이
```swift
func solution() {
    let testCase: Int = Int(readLine()!)!
    
tcLoop: for _ in 1...testCase {
    
    let inputKey: String = readLine()!
    var count: Int = Int(readLine()!)!
    var numArray: [String?] = readLine()!.dropFirst().dropLast().split(separator: ",").map({String($0)})
    
    var toggle: Bool = true
    
    var lIndex: Int = 0
    var rIndex: Int = count-1
    
    for key in inputKey {
        switch key {
        case "R":
            toggle.toggle()
        default:
            guard count > 0 else {
                print("error")
                continue tcLoop
            }
            
            if toggle {
                numArray[lIndex] = nil
                lIndex += 1
            }else {
                numArray[rIndex] = nil
                rIndex -= 1
            }
            
            count -= 1
        }
    }
    
    let temp = toggle ? numArray.compactMap({$0}) : numArray.compactMap({$0}).reversed()
    let result = temp.joined(separator: ",")
    print("[\(result)]")
}
}

solution()
```

<br/>

### toggle(Bool)값을 사용하면서 삭제되는 숫자를 index로 접근하여 nil 할당
### compactMap으로 nil값 제외시키고 사용