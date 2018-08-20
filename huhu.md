YAML讲义

字典
```python
{"age" : "18", "name" : "liqing"}
```

```yaml
age: "18"
```
列表
```python
[1, 2, xiaoming]
```
```yaml
- "1"
- "2"
- "xiaoming"
```

字典和列表的嵌套
- 字典与字典的嵌套
```python
{person1:{age:18, name : xiaoming}, person2:{age:19, name : xiaohong} , num: 20}
```

```yaml
person1:
  age: "18"
  name: "xiaoming"
person2:
  age: "19"
  name: "xiaohong"
num: "20"
```
- 字典嵌套列表
```python
{person1: xiaoming, person2: [1, 2, 3]}
```

```yaml
person1: "xiaoming"
person2: 
  - "1"
  - "2"
  - "3"
```
- 列表嵌套字典
```python
[{person1:18}, 2, 3, {person2:20}]
```

```yaml
- 
  person1: "18"
- "2"
- "3"
- 
  person2: "20"
```
- 列表嵌套列表
```python
[1, 2, [3, 4, 5], 6]
```

```yaml
- "1"
- "2"
- 
  - "3"
  - "4"
  - "5"
- "6"
```
- yaml 的读

```python
import yaml
with open("./data.yaml") as f:
  yaml.load(f)
```
- yaml 的写

```python
import yaml
aproject = {'name': 'Silenthand Olleander',
            'race': 'Human',
            'traits': ['ONE_HAND', 'ONE_EYE']
            }

print(yaml.dump(aproject，))
```

- 练习1
```python
{key1 : {age: 18, name: xiaoming, person: [1, 2, 3, {person2: 4, person3: 5}], height: 100}, key2:[7, 8, 9]}
```

```yaml
key1: 
  age: "18"
  name: "xiaoming"
  person:
    - "1"
    - "2"
    - "3"
    - 
       person2: "4"
       person3: "5"
  height: "100"
key2:
  - "7"
  - "8"
  - "9"
```
- 练习2

```python
[1, 2, 3, [4,5,6], {person:[1, 2, 3,]}, 5, {age:18,name:xiaoming}, [7,{age:18,name: xiaohong}] ]
```
```yaml
- "1"
- "2"
- "3"
- 
  - "4"
  - "5"
  - "6"
- 
  person: 
    - "1"
    - "2"
    - "3"
- "5"
- 
  age: "18"
  name: "xiaoming"
- 
  - "7"
  - 
     age: "18"
     name: "xiaohong"
```
- 纯量
```yaml
str1: "1"
str2: "x"
int1: 1
int2: 20
decimal1: 3.14
float1: 3.1415926535897932384626433
boolean1: True
boolean2: False
boolean3: true
boolean4: TRUE
null1: null
null2: Null
null3: NULL
time1: 2018-01-01 10:38:20.2060
```
- 布尔类型仅支持全大写，全小写，首字母大写
- 空值使用null来表示
- yaml 中不是字符串的包括：整数， float， bool， none， time
- yaml 与 py 的相互转换
- 锚点和引用
```yaml
data: &info
  value: "456"
name:
  value1: "123"
  <<: *info
```

- 常见错误
  - yaml 中包含中文
  - yaml 中空格位数不对
  - yaml 中的数据是直接复制的，使用了 tab 键，pycharm 不能转换
  - yaml 不能表示元组（yaml 是各种语言通用的）
