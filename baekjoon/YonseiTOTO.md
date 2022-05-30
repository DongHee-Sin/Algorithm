# Yonsei TOTO(12018)
[문제 설명](https://www.acmicpc.net/problem/12018)

<br/>

#### Goal : 주어진 마일리지로 가능한 많이 수강신청 하기
* 각 과목의 정원, 수강신청 인원, 각 학생들이 해당 과목에 사용한 마일리지가 입력값으로 주어진다.
* 같은 마일리지를 사용한다면 사용자에게 우선순위가 주어진다.
* 수강신청을 위해선 최소 1 마일리지가 필요하다.

<br>

# 풀이
1. 각각의 과목을 수강신청하기 위한 최소한의 마일리지를 구한다.
2. 오름차순 정렬한 후, 주어진 마일리지를 사용하여 하나씩 수강신청 한다.
3. 보유한 마일리지가 0 아래로 떨어지면 break
```swift
func solution() -> Int {
    let input: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})
    var point: Int = input[1]

    // 과목을 수강하기 위해 필요한 마일리지
    var needPoints: [Int] = []
    
    for _ in 0..<input[0] {
        let subjectInfo: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})
        var appliedPointArray: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})
        let appliedCount: Int = subjectInfo[0]
        let maxCount: Int = subjectInfo[1]
        
        // 정원보다 신청인원이 같거나 큰 경우
        if appliedCount >= maxCount {
            appliedPointArray.sort(by: <)
            needPoints.append(appliedPointArray[appliedCount-maxCount])
        }
        // 정원보다 신청인원이 더 적은 경우
        else {
            needPoints.append(1)
        }
        
    }
    
    var result: Int = 0
    
    needPoints.sort(by: <)
    
    for eachPoint in needPoints {
        point -= eachPoint
        
        if point >= 0 {
            result += 1
        }else {
            break
        }
    }
    
    return result
}

print(solution())
```
