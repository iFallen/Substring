### `Swift 3.x String <String.Index>`

>
let numbers = "123456789"

- `[]`

```
let _1 = numbers[numbers.startIndex] // '1' (Character)
```

- `startIndex/endIndex`

>
endIndex 非‘9’的位置

```
let _1 = numbers.substring(to: numbers.index(after: numbers.startIndex)) //"1" (String)
```

- `before/after/offset`

```
let _9          = numbers.substring(from: numbers.index(before: numbers.endIndex)) // "9"
let _23456789   = numbers.substring(from: numbers.index(after: numbers.startIndex)) // "23456789"
let _12         = numbers.substring(to: numbers.index(numbers.startIndex, offsetBy: 2)) // "12"
```

- `range`

```
let startIndex  = numbers.index(numbers.startIndex, offsetBy: 3)
let endIndex    = numbers.index(numbers.endIndex, offsetBy: -3)
let _456        = numbers.substring(with: startIndex..<endIndex) // "456"
```

- `extension`

```
extension String {
    func index(at: Int) -> Index {
        return self.index(startIndex, offsetBy: at)
    }
    
    func substring(from: Int) -> String {
        let fromIndex = index(at: from)
        return substring(from: fromIndex)
    }
    
    func substring(to: Int) -> String {
        let toIndex = index(at: to)
        return substring(to: toIndex)
    }
    
    func substring(with r:Range<Int>) -> String {
        let startIndex  = index(at: r.lowerBound)
        let endIndex    = index(at: r.upperBound)
        return substring(with: startIndex..<endIndex)
    }
}
```

>

```
let _1      = numbers.substring(to: 1) 	// "1"
let _789    = numbers.substring(from: 6)// "789"
let _456    = numbers.substring(with: 4..<7)// "456"
```