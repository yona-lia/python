# 用户输入和while循环

## 函数input（）的工作原理

函数input（）让程序暂停运行，等待用户输入文本。获取用户输入后，python将其赋给一个变量，以方便你使用。

```python
message = input("Tell me something, and I will repeat it back to you: ")
print(message)
```

```python
Tell me something, and I will repeat it back to you: hello
hello
```

### 编写清晰的程序

每当使用函数input（）时，都应指定清晰易懂的提示。

```python
name = input("Please tell me your name: ")
print(f"\nHello, {name}!")
```

```python
Please tell me your name: yona

Hello, yona!
```

有时候提示可能超过一行，我们可以把提示赋值给一个变量，再将变量传递给input（），这样即使提示超过一行，input（）语句也会十分清晰。

```python
prompt = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name?  "

name = input(prompt)
print(f"Hello, {name}!")
```

```python
If you tell us who you are, we can personalize the messages you see.
What is your first name?  lia
Hello, lia!
```

### 使用int（）来获取数值输入

使用input（）函数时，python将用户输入解读为字符串。当我们试图用输入用于数值比较时，python会引发错误。为解决这个问题，可使用int（）函数，它让python将输入视为数值。

```python
age = input("How old are yuo? ")

age = int(age)
if age >= 18:
    print("True")
```

```python
How old are yuo? 21
True
```

### 求模运算符

处理数值信息时，**求模运算符**是个很有用的工具，他将两个数相除并返回余数。如果一个数可以被另一个数整除，余数就是0，因此求模运算会返回0。可以利用这一点来判断奇偶数。

```python
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)

if number % 2 == 0:
    print(f"The number {number} is even.")
else:
    print(f"The number {number} is odd.")
```

```python
Enter a number, and I'll tell you if it's even or odd: 42
The number 42 is even.
```

## while循环简介

for循环用于针对集合中的每个元素都执行一个代码块，而while循环则不断运行，知道指定条件不满足为止。

### 使用while循环

```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
```

```python
1
2
3
4
5
```

### 让用户选择何时退出

我们可以在其中定义一个退出值，只要用户不输入这个值，程序接着运行。

```python
prompt = "\nTell me something, and I will repeat it back tu you: "
prompt += "\nEnter 'quit' tu end the program."
message = ""
while message != 'quit':
    message = input(prompt)
    print(message)
```

```python
Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello
hello

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello again
hello again

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.quit
quit
```

修改这个程序，使quit不被打印出来

```python
prompt = "\nTell me something, and I will repeat it back tu you: "
prompt += "\nEnter 'quit' tu end the program."
message = ""
while message != 'quit':
    message = input(prompt)

    if message != 'quit':
        print(message)
```

```python
Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello
hello

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello again
hello again

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.quit
```

### 使用标志

在更复杂的程序中，很多不同的事件会导致程序停止运行。这个时候，我们可定义一个变量，用于判断整个程序是否处于活动状态。这个变量称为标志（flag），充当程序的交通信号灯。可以让程序在标志为True时继续运行，并在任何时间导致标志的值为False时让程序停止运行。

```python
prompt = "\nTell me something, and I will repeat it back tu you: "
prompt += "\nEnter 'quit' tu end the program."

active = True 
while active:
    message = input(prompt)

    if message == 'quit':
        active = False
    else:
        print(message)
```

```python
Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello
hello

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.hello again
hello again

Tell me something, and I will repeat it back tu you:
Enter 'quit' tu end the program.quit
```

### 使用break退出循环

要立即退出while循环，不在运行循环中余下的代码，也不管条件测试的结果如何，可使用break语句。break语句用于控制程序流程，可用来控制哪些代码行将执行，哪些代码行不执行，从而让程序按你的要求执行你要执行的代码。

```python
prompt = "\nPlease enter the name of a city you have visited: "
prompt += "\n(Enter 'quit' when you are finished.)"
while True:
    city = input(prompt)

    if city == 'quit':
        break
    else:
        print(f"I'd love to go to {city.title()}!")
```

```python
Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.)lanzhou
I'd love to go to Lanzhou!

Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.)wuxi
I'd love to go to Wuxi!

Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.)quit
```

### 在循环中使用continue

要返回循环开头，并根据条件测试结果决定是否继续执行循环，可使用continue语句。

```python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue

    print(current_number)
```

```python
1
3
5
7
9
```

## 使用while循环处理列表和字典

for循环试一种遍历列表的有效方式，但不应在for循环中修改列表，否则将导致python难以跟踪其中的元素。要在遍历列表的同时对其进行修改，可使用while循环。**通过将while循环同列表和字典结合起来使用，可收集、存储并组织大量输入，供以后查看和显示。

### 在列表之间移动元素

```python
unconfirmed_users = ['alice','brian','candace']
confirmed_users = []

while unconfirmed_users:
    current_user = unconfirmed_users.pop()

    print(f"Verifying user: {current_user.title()}")
    confirmed_users.append(current_user)

print("\nThe following users have been confirmed: ")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
```

```python
Verifying user: Candace
Verifying user: Brian
Verifying user: Alice

The following users have been confirmed: 
Candace
Brian
Alice
```

### 删除为特定值的所有列表元素

我们可以使用remove（）函数来删除列表中的特定值。如果要删除列表中所有为特定值的元素，可以通过运行一个while循环来实现。

```python
pets = ['dog','cat','dog','goldfish','cat','rabbit','cat']
print(pets)

while 'cat' in pets:
    pets.remove('cat')

print(pets)
```

```python
['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
['dog', 'dog', 'goldfish', 'rabbit']
```

### 使用用户输入来填充字典

可使用while循环提示用户输入任意多的信息。

```python
responses = {}

polling_active = True

while polling_active:
    name = input("\nWhat is your name? ")
    response = input("Which mountain would you like to climb someday? ")

    responses[name] = response

    repeat = input("Would you like tu let another person repond? (yes/ no) ")
    if repeat == 'no':
        polling_active = False

print("\n--- Poll Results ---")
for name, response in responses.items():
    print(f"{name} would like to climb {response}.")
```

```python
What is your name? Eric
Which mountain would you like to climb someday? Denali
Would you like tu let another person repond? (yes/ no) yes

What is your name? Lynn
Which mountain would you like to climb someday? Devil's Thumb
Would you like tu let another person repond? (yes/ no) no

--- Poll Results ---
Eric would like to climb Denali.
Lynn would like to climb Devil's Thumb.
```

# 函数

## 定义函数

```python
def greet_user():
    print("Hello!")

greet_user()
```

```python
Hello!
```

**def** 告诉python，你要定义一个函数。这是**函数定义**，向python指出了函数名，还可能在圆括号内指出函数为完成任务需要什么样的信息。在这里，函数名 greet_user（），他不需要任何信息就能完成工作，因此括号是空的（即便如此，括号也必不可少）。最后，定义以冒号结尾。跟在后面的所有缩进行构成了函数体。

### 向函数传递信息

```python
def greet_user(username):
    print(f"Hello, {username.title()}!")

greet_user('jesse')
```

```python
Hello, Jesse!
```

代码greet_uesr（‘jesse’）调用函数greet_user（），并向他提供执行函数调用print（）所谓的信息。

### 实参和形参

在函数greet_user（）的定义中，变量username是一个**形参（parameter）**，即函数完成工作所需的信息。在代码greet_user（’jesse‘）中，值’jesse‘是一个**实参（argument）**，即调用函数时传递给函数的信息。调用函数时，将要让函数使用的信息放在圆括号内。在greet_user（’jesse‘）中，将实参’jesse‘传递给了函数greet_user（），这个值被赋给了形参username。

## 传递实参

函数定义中可能包含多个形参，因此函数调用中也可能包含多个实参。向函数传递实参的方式很多：可以使用**位置实参**，这要求实参的顺序与形参的孙旭相同；也可以使用**关键字实参**，其中每个实参都由变量名和值组成；还可以使用列表和字典。

### 位置实参

调用函数时，python必须将函数调用中的每个实参都关联到函数定义重点一个形参。为此，最简单的关联方式是基于实参的顺序。

```python
def describe_pet(animal_type,pet_name):
    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet('hamster','harry')
```

```python
I have a hamster.
My hamster's name is Harry.
```

#### 多次调用函数

可根据需要调用函数任意次。

```python
def describe_pet(animal_type,pet_name):
    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet('hamster','harry')
describe_pet('dog','willie')
```

```python
I have a hamster.
My hamster's name is Harry.

I have a dog.
My dog's name is Willie.
```

### 关键字实参

关键字实参是传递给哈数的名称值对。因为直接在参数中将名称和值关联起来，所以向函数传递实参时不会混淆。

```python
def describe_pet(animal_type,pet_name):
    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet(animal_type='hamster',pet_name='harry')
```

```python
I have a hamster.
My hamster's name is Harry.
```

### 默认值

编写函数时，可给每个形参指定**默认值**。在掉用函数中给形参提供了实参时，python将使用指定的实参值；否则，将使用形参的默认值

```python
def describe_pet(pet_name,animal_type='dog'):

    print(f"\nI have a {animal_type}.")
    print(f"My {animal_type}'s name is {pet_name.title()}.")

describe_pet(pet_name='harry')
```

```python
I have a dog.
My dog's name is Harry
```

注意，在这个函数的定义中，修改了形参的排列顺序。因为给animal_type指定了默认值，无需通过实参来指定动物类型，所以在函数调用中只包含了一个实参——宠物的名字。然而，python依然将这个实参视为位置实参，因此如果函数调用中只包含宠物的名字，这个实参将关联到函数定义中的第一个形参。这就是需要将pet_name放在形参列表开头的原因。

## 返回值

函数并非总是直接显示输出，他还可以处理一些数据，并返回一个或一组值。函数返回的值称为**返回值**。在函数中，可以使用return语句将值返回到调用函数的代码行。

### 返回简单值

```python
def get_formatted_name(first_name, last_name):
    full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name('jimi','hendrix')
print(musician)
```

```python
Jimi Hendrix
```

### 让实参变成可选的

```python
def get_formatted_name(first_name, last_name, middle_name=''):
    if middle_name:
        full_name = f"{first_name} {middle_name} {last_name}"
    else:
        full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name('jimi','hendrix')
print(musician)

musician = get_formatted_name('john','hooker','lee')
print(musician)
```

```python
Jimi Hendrix
John Lee Hooker
```

### 返回字典

函数可返回任何类型的值，包括列表和字典等较复杂的数据结构。

```python
def get_formatted_name(first_name, last_name):
    person = {'first': first_name, 'last': last_name}
    return person

musician = get_formatted_name('jimi','hendrix')
print(musician)
```

```python
{'first': 'jimi', 'last': 'hendrix'}
```

扩展

```python
def get_formatted_name(first_name, last_name, age=None):
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person

musician = get_formatted_name('jimi','hendrix',age=27)
print(musician)
```

```python
{'first': 'jimi', 'last': 'hendrix', 'age': 27}
```

### 结合使用函数和while循环

```python
def get_formatted_name(first_name, last_name):
    full_name = f"{first_name} {last_name}"
    return full_name.title()

while True:
    print("\nPlease tell me your name: ")
    print("(enter 'q' at any time to quit)")

    f_name = input("First name: ")
    if f_name == 'q':
        break

    l_name = input("Last name: ")
    if l_name == 'q':
        break
    formatted_name = get_formatted_name(f_name,l_name)
    print(f"\nHello, {formatted_name}!")
```

```python
Please tell me your name:
(enter 'q' at any time to quit)
First name: eric
Last name: matthes

Hello, Eric Matthes!

Please tell me your name:
(enter 'q' at any time to quit)
First name: q
```

## 传递列表

```python
def greet_users(names):
    for name in names:
        msg = f"Hello, {name.title()}!"
        print(msg)

usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
```

```python
Hello, Hannah!
Hello, Ty!
Hello, Margot!
```

### 在函数中修改列表

```python
def print_models(unprinted_designs, completed_models):
    while unprinted_designs:
        current_design = unprinted_designs.pop()
        print(f"Printing model: {current_design}")
        completed_models.append(current_design)

def show_completed_models(completed_models):
    print("\nThe dollowing models have been printed:")
    for completed_model in completed_models:
        print(completed_model)

unprinted_designs = ['pjone case', 'robot pendant', 'dodecahedron']
completed_models = []

print_models(unprinted_designs, completed_models)
show_completed_models(completed_models)
```

```python
Printing model: dodecahedron
Printing model: robot pendant
Printing model: pjone case

The dollowing models have been printed:
dodecahedron
robot pendant
pjone case
```

