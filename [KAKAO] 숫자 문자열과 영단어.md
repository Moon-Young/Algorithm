### 배열을 만들어서 검사하고 변경해주는 방식을 했음, 무식하게 하나씩 replacingOccurrences 다쓰고싶지 않아서...ㅎㅎ
### 다른 풀이법 봐도 내께 더 난것같음!


# [KAKAO] 숫자 문자열과 영단어

<img width="672" alt="image" src="https://user-images.githubusercontent.com/29904301/187358097-ea6d13e3-8556-4f45-8a09-89f4a5899cae.png">
<img width="658" alt="image" src="https://user-images.githubusercontent.com/29904301/187358126-562aa8ca-3665-4a6f-9d76-935e48fc88c3.png">
<img width="653" alt="image" src="https://user-images.githubusercontent.com/29904301/187358184-2978bcf4-0905-4072-8729-dab304fe7d53.png">


## Solution 1
<pre>
<code>
func solution(_ s:String) -> Int {
    
    var answer = s
    
    var wordList = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"]
    var numList = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
    
    for i in 0..'<'wordList.count {
        if answer.contains(wordList[i]) {
            answer = answer.replacingOccurrences(of: wordList[i], with: numList[i])
        }   
    }
    return Int(answer)!
}
</pre>
</code>

## Solution 2
<pre>
<code>
func solution(_ s:String) -> Int {
    let arr = ["zero","one","two","three","four","five","six","seven","eight","nine"]
    var str = s
    for i in 0..'<'arr.count {
        str = str.replacingOccurrences(of: arr[i], with: String(i))
    }
    return Int(str)!
}
</pre>
</code>

