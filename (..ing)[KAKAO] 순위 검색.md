### 답이아니라 이진탐색으로 풀어야 속도가 나옴...


# [KAKAO] 순위 검색

https://school.programmers.co.kr/learn/courses/30/lessons/72412

## Solution 1
<pre>
<code>


func solution(_ info:[String], _ query:[String]) -> [Int] {
    
    var information = info
    var querys = query
    
    var count:[Int] = Array(repeating: 0, count: querys.count)
    
    var language:[String] = Array()
    var backOrFront:[String] = Array()
    var juniorOrSenior:[String] = Array()
    var food:[String] = Array()
    var score:[String] = Array()

    for i in 0..<information.count {
        
        let spl = information[i].components(separatedBy: " ")
        
        language.append(spl[0])
        backOrFront.append(spl[1])
        juniorOrSenior.append(spl[2])
        food.append(spl[3])
        score.append(spl[4])

//        print("\(language) , \(backOrFront) , \(juniorOrSenior) , \(food) , \(score)")
    }
    
    for i in 0..<querys.count {
        
        let split = querys[i].replacingOccurrences(of: "- ", with: "").replacingOccurrences(of: " and", with: "").replacingOccurrences(of: "and ", with: "").components(separatedBy: " ")
        
        print(split)
    }
    
    
    return []
}



solution(["java backend junior pizza 150",
          "python frontend senior chicken 210",
          "python frontend senior chicken 150",
          "cpp backend senior pizza 260",
          "java backend junior chicken 80",
          "python backend senior chicken 50"],
         
         ["java and backend and junior and pizza 100",
          "python and frontend and senior and chicken 200",
          "cpp and - and senior and pizza 250",
          "- and backend and senior and - 150",
          "- and - and - and chicken 100",
          "- and - and - and - 150"])
 </code>
 </pre>
