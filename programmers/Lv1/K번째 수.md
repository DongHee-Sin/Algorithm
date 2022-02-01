# K번째 수
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/42748)

# 풀이
```swift
func solution(_ array:[Int], _ commands:[[Int]]) -> [Int] {
    var result: [Int] = []

    for command in commands {
        var resultArray: [Int] = [Int]()
        for index in command[0]-1...command[1]-1 {
            resultArray.append(array[index])
        }
        resultArray.sort()
        result.append(resultArray[command[2]-1])
    }

    return result
}
```
