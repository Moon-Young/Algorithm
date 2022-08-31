### 새롭게 알게 된 것. isLetter || isNumber 문자인지 , 숫자인지 판단
### filiter 을 한번더 봐야할 것 같고 step2만 아니면 쉬웠던것 같다.

https://school.programmers.co.kr/learn/courses/30/lessons/72410
# [KAKAO] 숫자 문자열과 영단어
<img width="667" alt="image" src="https://user-images.githubusercontent.com/29904301/187600091-8d19e005-605d-4d01-8d99-1fef8456561e.png">
<pre>
<code>
1단계 new_id의 모든 대문자를 대응되는 소문자로 치환합니다.
2단계 new_id에서 알파벳 소문자, 숫자, 빼기(-), 밑줄(_), 마침표(.)를 제외한 모든 문자를 제거합니다.
3단계 new_id에서 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환합니다.
4단계 new_id에서 마침표(.)가 처음이나 끝에 위치한다면 제거합니다.
5단계 new_id가 빈 문자열이라면, new_id에 "a"를 대입합니다.
6단계 new_id의 길이가 16자 이상이면, new_id의 첫 15개의 문자를 제외한 나머지 문자들을 모두 제거합니다.
     만약 제거 후 마침표(.)가 new_id의 끝에 위치한다면 끝에 위치한 마침표(.) 문자를 제거합니다.
7단계 new_id의 길이가 2자 이하라면, new_id의 마지막 문자를 new_id의 길이가 3이 될 때까지 반복해서 끝에 붙입니다.
</pre>
</code>

## Solution 1
<pre>
<code>

import Foundation

func solution(_ new_id:String) -> String {
    
    var answer = new_id
    
    answer = step1(id: answer)
    answer = step2(id: answer)
    answer = step3(id: answer)
    answer = step4(id: answer)
    answer = step5(id: answer)
    answer = step6(id: answer)
    answer = step7(id: answer)
    
    print(answer)
    
    return answer
}
// solution("...!@BaT#*..y.abc1234de-f_g.h%^&*()123123ijklm...")
// solution("1")
//1단계 new_id의 모든 대문자를 대응되는 소문자로 치환합니다.
func step1( id:String ) -> String {

    return id.lowercased()
}

//2단계 new_id에서 알파벳 소문자, 숫자, 빼기(-), 밑줄(_), 마침표(.)를 제외한 모든 문자를 제거합니다.
func step2( id:String ) -> String {
 
    var specialCharacter = ["-","_","."]
    
    return id.filter { $0.isNumber || $0.isLetter || specialCharacter.contains(String($0)) }
}

//3단계 new_id에서 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환합니다.
func step3( id:String ) -> String {
 
    var convertId = id
    
    while convertId.contains("..") {
      convertId = convertId.replacingOccurrences(of: "..", with: ".")
    }
    
    return convertId
}

//4단계 new_id에서 마침표(.)가 처음이나 끝에 위치한다면 제거합니다.
func step4( id:String ) -> String {
 
    var convertId = id
    
    while convertId.first == "." {
        convertId.removeFirst()
    }
    
    while convertId.last == "." {
        convertId.removeLast()
    }
    
    return convertId
}

//5단계 new_id가 빈 문자열이라면, new_id에 "a"를 대입합니다.
func step5( id:String ) -> String {
    return id.isEmpty ? "a" : id
}

//6단계 new_id의 길이가 16자 이상이면, new_id의 첫 15개의 문자를 제외한 나머지 문자들을 모두 제거합니다.
//     만약 제거 후 마침표(.)가 new_id의 끝에 위치한다면 끝에 위치한 마침표(.) 문자를 제거합니다.
func step6( id:String ) -> String {
    
    var convertId = id
    
    while convertId.count >= 16 {
        convertId.removeLast()
    }
    convertId = step4(id: convertId)
    return convertId
}

//7단계 new_id의 길이가 2자 이하라면, new_id의 마지막 문자를 new_id의 길이가 3이 될 때까지 반복해서 끝에 붙입니다.func step6( id:String ) -> String {
func step7( id:String ) -> String {
 
    var convertId = id
    
    while convertId.count <= 2 {
        convertId += convertId.suffix(1)
    }
    
    return String(convertId)
}

</code>
</pre>
