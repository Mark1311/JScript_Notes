# Js 100 Question


```python
let a = []
let b = []

print(a == b) # False
print(a === b) # False

Bcz's actual memory location are diff of both variable's.
```


```python
let a = []
let b = a

print(a == b) # False
print(a === b) # True

Bcz's both variables has located on same memory. var b is directly reference to var a.
```


```python
let a = [20]
let b = [20]
print(a[0] == b[0]) # True
print(a[0] === b[0]) # True

locaion memory compare nhi ho rhi ha direct value compare ho rhi ha yaha.
```


```python
console.log(typeof NaN)
#output ==> Number
```


```python
let data = {name:"bittu"}
console.log(delete data.name) # True
ye batata ha ki data delete hua ha ya nhi.

console.log(delete data) # False.
data ko directly delete nhi kr shkte ha.
```


```python
let data = {name: bittu, age : 25}
let {name} data
let {age} = data

console.log(name) # bittu
console.log(age) # 25
```


```python
let data = {name: bittu, age : 25}
let ingo = {add: delhi}
console.log(data, ...info)
# {data: {name: bittu, age : 25}, add: "delhi"}
```


```python
let data = {name: bittu, age : 25}
let ingo = {add: delhi}
console.log(...data, ...info)
# {name: bittu, age : 25, add: "delhi"}
```


```python
console.log(isNaN ("String")) # True
console.log(isNaN (34)) # False
```


```python
let data = "True"
console.log(!data) # False
```


```python
let data = 'true'
console.log(!!data) # True
```


```python
let data = ["anil", "pet", "det"]
delete data[1]
console.log(data)
# [anil, empty, det]
```


```python
let a = 30
let A = 300
console.log(a) # 30
console.log(A) # 300
```


```python
let a = "like"
let b = 'like'
print(a === b) # True
```


```python
let a = 1
let b = 2
print(--b === a) # True
```


```python
a = 1
b = 1
c = 2
print(a === b ===-c)
# True
```


```python
console.log(a)
var a
# Undefind
```


```python
console.log(b)
# not defind
```


```python
for(var i =0, i<3, i++){
    console.log(i)
}
# output:-  3
            3
            3
```


```python
for(let i =0, i<3, i++){
    console.log(i)
}
# output:-  0
            1
            2
```


```python
console.log(typeof +ture)
# Number
```


```python
console.log(! " string") #False
console.log(typeof ("bittu")) #string
```


```python
let c = {name : "bittu"}
let d
d = c
c.name = "anil"
console.log(d.name) # anil
```


```python
var x;
var x = 10
print(x) #10
```


```python
var x;
let x = 10
print(x) #error
```


```python
let a = 3
let b = new Number(3)
console.log(a == b) #True
console.log(a === b) # False
```


```python
function sum(a, b){
    return a+b;
}
console.log(sum(1, "2"))
# 12
```


```python
let a = 2
print(a++) # 2
print(++a) # 3
print(a) # 2
```


```python
console.log(typeof typeof 1)
# String
console.log(typeof 1)
# Number
```


```python
const a = [1,2,3]
a[6] =12
console.log(a)
# [1,2,3, empty, empty, empty, 6]
```


```python
const a = [1,2,3]
a[9] =a
console.log(a)
# <ref *1> [ 1, 2, 3, <6 empty items>, [Circular *1] ]
# Infinity position tkk array runn hoga.
```


```python
console.log(!! null) # False
console.log(!! "") #False
console.log(!! 1) True
```


```python
console.log([..."bittu"])
# [b,i,t,t,u]
```


```python
let data = 1+2+"3"
typeof data
# String
# 33
```


```python
print(3+4++"5")
# 12
# Number
```


```python
print([]===[])
# False
```


```python
console.log(!true - true)
# -1
```


```python
console.log(true + +"10")
# 11
```

# Convert String to Array


```python
console.log(str.split())
console.log([str])
console.log([...str])
console.log(str.split(''))
```


```python
# Replace Char.

console.log(str.replace("H","Z"))
```


```python
# Remove Last Char.
console.log(Str.Substring(0, Str.length -1))
```


```python
# Substring Create:-
console.log(Str.Substring(Staring Index, Ending Index))
```

Note:- Undefinde is take the memory but not defind is not take memory.

# Diff between Function and Method.

### Function:- 


```python
1. A block of Code.

2. Call directly.

3. invoked => ()

4. function live on its own.
```

# Methods


```python
1. An obj property that has a fun value.

2. obj = {methodName : fun(){
    
}}

obj.methodName()

3. Called using obj Name with . (dot Notation).

4. Function Assiocated with an obj property.
```

# Event propagation

Event propagation web development me ek process hai jisme events, jaise ki click, keypress, ya mouseover, ek HTML element se dusre element tak propagate karte hain. Ye process do tariko se hoti hai: Bubbling aur Capturing.

## Event Bubbling:

Jab ek event ek element pe trigger hota hai, to wo pehle us element ko affect karta hai jahan event hua, phir wo us element ke parent ko affect karta hai, aur aise hi ye chain me propagate hota rehta hai jab tak root element tak nahi pahuchta.
    
### Example: 
Agar ek button ke click event ko ek div ke andar wrap kiya gaya ho, to pehle button ka event handle hoga, phir div ka event, aur phir uske parent elements tak propagate karega.

## Event Capturing (Phase):

Capturing me, event sabse pehle document ke root element se start hota hai, aur phir wo target element tak propagate karta hai.
    
### Example: 
    
Agar ek event div ke andar trigger hota hai, to wo pehle parent elements ko affect karega, aur phir target element tak pahuchta hai.

### Stop Propagation:
Agar aap nahi chahte ke event propagate ho, to aap event.stopPropagation() use kar sakte hain. Isse event ka propagation ruk jata hai aur wo sirf usi element tak limited rahata hai jahan wo trigger hua tha.

### Practical Use:
Event propagation ka istemal aap event delegation me karte hain, jisme aap parent element pe event listener laga kar child elements ke events handle karte hain, jo ki dynamically generate hote hain.

Kuch is tarah se event propagation ko samjha ja sakta hai!
