### Solution 1 - 실패라서 ,,,Fomagran님꺼를 참고해서 하니까 가독성도,,이해도 엄처 잘됨,,,solution 2


# [KAKAO] 오픈채팅방

https://school.programmers.co.kr/learn/courses/30/lessons/42888
<img width="661" alt="image" src="https://user-images.githubusercontent.com/29904301/188076146-75de019e-a61e-4f7a-a2d4-18f683cba57a.png">

## Solution 2

<pre>
<code>
func solution(_ record:[String]) -> [String] {
  
    var userId:[String] = [String]()
    var userNick:[String:String] = [String:String]()
    var answer:[String] = [String]()
    var confirm:[String] = [String]()
    
    for r in record {
        
        let split = r.components(separatedBy: " ")
        
        if split[0] == "Enter" {
            
            answer.append("님이 들어왔습니다.")
            
            userNick[split[1]] = split[2]
            
            userId.append(split[1])
            
            
        } else if split[0] == "Leave" {
            
            answer.append("님이 나갔습니다.")
            userId.append(split[1])
            
        } else if split[0] == "Change" {
            
            userNick[split[1]] = split[2]
            
        }
    }
    
    for i in 0..'<'answer.count {
        confirm.append("\(userNick[userId[i]]!)\(answer[i])")
    }
    return confirm
}

solution(["Enter uid1234 Muzi", "Enter uid4567 Prodo","Leave uid1234","Enter uid1234 Prodo","Change uid4567 Ryan"])
</code>
</pre>


## Solution 1 - 실패,,,,,,

<pre>
<code>
func solution(_ record:[String]) -> [String] {
    
//    var dict:[[String]] = Array()
//    var setId: [[String]] = Array(repeating: [], count: record.count)
//    var recordLog: [String] = Array()
//    solution(["Enter uid1234 Muzi", "Enter uid4567 Prodo","Leave uid1234","Enter uid1234 Prodo","Change uid4567 Ryan"])
    
    
//    user log 공백으로 나눈후 배열처리
    var dict =  record.map { $0.components(separatedBy: " ") }
//    user 명단 필터
    var Id = dict.filter { !$0.contains("Change") }
//    user 중에 닉네임 변경될 사람 찾기 필터
    var changeId = dict.filter { $0.contains("Change") }

    
//  "step1 ID Change 처리
    Id = step1(Id: Id, changeId: changeId)
//  "step2 id 최신화 리스트 만들기
    var confirmId = step2(Id: Id)
//    print("Id :  \(Id)")
//    print("co :  \(confirmId)")
//  "step3 영어 텍스트 컨버트
    var newId = step3(Id: Id)
//    print("ne :  \(newId)")
//  "step4 호출하기(이름검색해서)
    //["Prodo님이 들어왔습니다.", "Ryan님이 들어왔습니다.", "Prodo님이 나갔습니다.", "Prodo님이 들어왔습니다."]
    var answer = step4(newId: newId, confirmId: confirmId)
//    print("an : \(answer)")
    
    return answer
}

solution(["Enter uid1234 Muzi", "Enter uid4567 Prodo","Leave uid1234","Enter uid1234 Prodo","Change uid4567 Ryan"])



// id를 비교해서 해당하는 id면 닉네임 최신화 처리함.
func step1(Id: [[String]], changeId: [[String]]) -> [[String]] {

    var convertId = Id
    var chId = changeId
    
    for i in 0..'<'convertId.count {
        for j in 0..'<'chId.count {
            if convertId[i][1] == chId[j][1] {
                convertId[i][2] =  chId[j][2]
            }
        }
    }
    
    return convertId
}

//  id 닉네임 최신 리스트 만들기
func step2(Id: [[String]]) -> Dictionary<String, String> {
    
    var confirmId = Dictionary<String, String>()
    
    for i in 0..<Id.count {
        
        for j in 0..<Id[i].count {
            if Id[i].count == 3 {
                confirmId.updateValue(Id[i][2], forKey: Id[i][1])
            }
        }
    }
    return confirmId
}

// 텍스트 변경
func step3(Id:[[String]]) -> ([[String]]) {
    
    var newId = Id
    
    for i in 0..'<'newId.count {
        switch newId[i][0] {
        case "Enter":
            newId[i][0] = "들어왔습니다."
        case "Leave":
            newId[i][0] = "나갔습니다."
        default:
            ""
        }
    }
    return newId
}

func step4 (newId:[[String]], confirmId: Dictionary<String, String>)->([String]) {
    
    var newId = newId
    var confirmId = confirmId
    
    var answer:[String] = Array()
    for i in 0..'<'newId.count {
            
        var nickCode = newId[i][1]
        var nickName = confirmId[nickCode]
            
        answer.append("\(nickName!)님이 \(newId[i][0])")

    }
    return answer
}
</code>
</pre>


