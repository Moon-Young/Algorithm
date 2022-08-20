### map은 역시 갓 ㅇ_     ㅇ ;;;;


# x만큼 간격이 있는 n개의 숫자

<img width="657" alt="image" src="https://user-images.githubusercontent.com/29904301/185754415-2ca32d03-911e-40b9-bedd-2c84247496bc.png">



## Solution 1
<pre>
<code>
func solution(_ x:Int, _ n:Int) -> [Int64] {
    
    var result: [Int64] = []
    
    for i in 1...n {
        
      // result.append(Int64(x) * Int64(i))
         result.append(Int64(x * i))
        
        
    }
    return result
}
</pre>
</code>

## Solution 2
<pre>
<code>
func solution(_ x:Int, _ n:Int) -> [Int64] {

  return Array(1...n).map{ Int64($0 * x) }

}
</pre>
</code>

<img width="918" alt="image" src="https://user-images.githubusercontent.com/29904301/185754691-9e9cd354-dcdb-4f10-b92a-214d145d2234.png">

