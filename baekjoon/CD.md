# CD(4158)
[문제 설명](https://www.acmicpc.net/problem/4158)

<br/>

#### Goal : 오름차순으로 주어지는 2개의 배열에서 중복되는 값의 수를 출력

<br/>

#### 조건: 
* 각 배열은 최대 1,000,000
* 배열의 크기를 알려주는 input에 "0, 0"이 입력될 때까지 반복


<br>

---

<br>

## 1번 풀이
### 이분탐색 사용
```swift
func binarySearch<T: Comparable>(findValue: T, arr: [T]) -> Bool {
    var min: Int = 0
    var max: Int = arr.count-1
    var mid: Int = 0
    
    while min <= max {
        mid = (min + max) / 2
        
        guard findValue != arr[mid] else {return true}
        
        if findValue > arr[mid] {
            min = mid + 1
        }else {
            max = mid - 1
        }
    }
    
    return findValue == arr[mid]
}


func solution() {
    
    while true {
        let input: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})
        
        guard input != [0, 0] else {break}
        
        var nArray: [Int] = []
        var mArray: [Int] = []
        
        var result: Int = 0
        
        for _ in 0..<input[0] {
            nArray.append(Int(readLine()!)!)
        }
        for _ in 0..<input[1] {
            mArray.append(Int(readLine()!)!)
        }

        
        nArray.forEach({
            if binarySearch(findValue: $0, arr: mArray) {
                result += 1
            }
        })
        
        print(result)
    }
    
}

solution()
```

<br/>

---

<br/>

## 2번 풀이
### 투포인터 사용
```swift
func solution() {

    while true {
        let input: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})

        guard input != [0, 0] else {break}

        var nArray: [Int] = []
        var mArray: [Int] = []

        var nIndex: Int = 0
        var mIndex: Int = 0

        var result: Int = 0

        for _ in 0..<input[0] {
            nArray.append(Int(readLine()!)!)
        }
        for _ in 0..<input[1] {
            mArray.append(Int(readLine()!)!)
        }

        while true {

            guard nIndex < (input[0]) && mIndex < (input[1]) else {
                break
            }

            let nValue: Int = nArray[nIndex]
            let mValue: Int = mArray[mIndex]

            // 값이 같은 경우
            if nValue == mValue {
                nIndex += 1
                mIndex += 1
                result += 1
                continue
            }

            // 값이 다른 경우
            if nValue < mValue {
                nIndex += 1
            }else {
                mIndex += 1
            }
        }

        print(result)
    }

}

solution()
```

<br/>

---

<br/>

## 3번 풀이
### Set 사용
```swift
func solution() {

    while true {
        let input: [Int] = readLine()!.split(separator: " ").map({Int(String($0))!})

        guard input != [0, 0] else {break}

        var nSet: Set<Int> = []

        var result: Int = 0

        for _ in 0..<input[0] {
            nSet.insert(Int(readLine()!)!)
        }
        for _ in 0..<input[1] {
            if nSet.contains(Int(readLine()!)!) {
                result += 1
            }
        }

        print(result)
    }

}

solution()
```

<br/>
<br>

---

<br>
<br>

#### 😡 결론 : 이 문제는 FileIO를 사용하여 빠른입출력을 하지 않으면 Swift에서는 무슨짓을 해도 시간초과가 나온다... ;