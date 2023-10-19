# 类

## 创建和使用类

### 创建Dog类

```python
class Dog:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def sit(self):
        print(f"{self.name} is now sitting.")
    def roll_over(self):
        print(f"{self.name} rolled over!")

```

**方法\__init__\()**

类中的函数称为**方法**。前面学到的有关函数的一切都适用于方法，就目前而言，唯一重要的差别就是调用方法的方式。这个方法是一个特殊方法，每当你根据Dog类创建新实例时，python都会自动运行他。在这个方法的名称中，开头和末尾各有两个下划线，这是一种约定，旨在避免python默认方法与普通方法发生名称冲突。务必确保其两边都有两个下划线,否则当你使用类来创建实例时，将不会自动调用这个方法，进而引发难以发现的错误。

我们将方法\__init__\()定义成包含三个形参：self，name和age。在这个方法的定义中，形参self必不可少，而且必须位于其他形参的前面。因为python在调用这个方法来创建Dog实例时，将自动传入实参self。每个与实例相关联的方法调用都自动传递实参self，他是一个只想实例本身的引用，让实例能够访问类中的属性和方法。

两个变量前都有前缀self。以self为前缀的变量可供类中的所有方法使用，可以通过类的任何实例来访问。self.name = name获取与形参name相关联的值，并将其赋给变量那么，然后改变量呗关联到当前创建的实例。self.age = age的作用与此类似。像这样可通过实例访问的变量称为**属性**。

#### 1.访问属性

```python
class Dog:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def sit(self):
        print(f"{self.name} is now sitting.")
    def roll_over(self):
        print(f"{self.name} rolled over!")

my_dog = Dog('Willie',6)

print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} year old.")
```

```python
My dog's name is Willie.
My dog is 6 year old.
```

#### 2.调用方法

```python
class Dog:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def sit(self):
        print(f"{self.name} is now sitting.")
    def roll_over(self):
        print(f"{self.name} rolled over!")

my_dog = Dog('Willie',6)

my_dog.sit()
my_dog.roll_over()
```

```python
Willie is now sitting.
Willie rolled over!
```

#### 3.创建多个实例

```python
class Dog:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def sit(self):
        print(f"{self.name} is now sitting.")
    def roll_over(self):
        print(f"{self.name} rolled over!")

my_dog = Dog('Willie',6)
your_dog = Dog('Lucy',3)

print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
my_dog.sit()

print(f"\nYour dog's name is {your_dog.name}.")
print(f"Your dog is {your_dog.age} years old.")
your_dog.sit()
```

```python
My dog's name is Willie.
My dog is 6 years old.
Willie is now sitting.

Your dog's name is Lucy.
Your dog is 3 years old.
Lucy is now sitting.
```

## 使用类和实例

可使用类来模拟显示世界中的很多情景。类编写好后，大部分时间将花在根据类创建的实例上。我们需要执行的一个重要任务就是修改实例的属性。可以直接修改实例的属性，也可以编写方法以特定方式进行修改。

### Car类

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
my_new_car = Car('audi', 'a4', 2019)
print(my_new_car.get_descriptive_name()) 
```

```python
2019 Audi A4
```

在下面定义了一个名为get_descriptive_name（）的方法。它使用属性year，make和model创建一个对汽车进行描述的字符串，让我们无需分别打印每个属性的值。为在这个方法中访问属性的值，使用了self.make，self.model，self.year。然后根据Car类创建了一个实例，并将其赋给变量my_new_car.接下来，调用方法get_descriptive_name（），指出我们拥有一辆什么样的汽车。

下面我们给他添加一个随时间变化的属性，用于存储汽车的总里程。

### 给属性指定默认值

创建实例时，有些属性无需通过形参来定义，可在方法\__init__（）中为其指定默认值。、

下面添加一个名为odometer_reading的属性，其初始值总为0.我们还添加了一个名为read_odometer()的方法，用于读取骑车的里程表：

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"Thisccar has {self.odometer_reading} miles on it.")
my_new_car = Car('audi', 'a4', 2019)
print(my_new_car.get_descriptive_name()) 
my_new_car.read_odometer()
```

```python
2019 Audi A4
Thisccar has 0 miles on it.
```

### 修改属性的值

#### 直接修改属性的值

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"Thisccar has {self.odometer_reading} miles on it.")
my_new_car = Car('audi', 'a4', 2019)
print(my_new_car.get_descriptive_name()) 

my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```

```python
2019 Audi A4
Thisccar has 23 miles on it.
```

#### 通过方法修改属性的值

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def update_odometer(self, mileage):
        self.odometer_reading = mileage
    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"Thisccar has {self.odometer_reading} miles on it.")
my_new_car = Car('audi', 'a4', 2019)
print(my_new_car.get_descriptive_name()) 

my_new_car.update_odometer(23)
my_new_car.read_odometer()
```

```python
2019 Audi A4
Thisccar has 23 miles on it.
```

添加方法update_odometer（），这个方法接受了一个里程值，并将其赋给self.odometer_reading。在后面，调用update_odometer（），并向它提供了实参23。它将里程表读数设置为23，而方法read_odometer()打印该读数。

#### 通过方法对属性的值进行递增

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def update_odometer(self, mileage):
        self.odometer_reading = mileage
    def increment_odometer(self, miles):
        self.odometer_reading += miles 
    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")
my_new_car = Car('subaru', 'outback', 2015)
print(my_new_car.get_descriptive_name()) 

my_new_car.update_odometer(23_500)
my_new_car.read_odometer()
my_new_car.increment_odometer(100)
my_new_car.read_odometer()
```

```python
2015 Subaru Outback
This car has 23500 miles on it.
This car has 23600 miles on it.
```

新增方法increment_odometer（）接受一个单位为英里的数，并将其加入self.odometer_reading中。

## 继承

编写类时，并非总是要从空白开始。如果要编写的类时另一个现成类的特殊版本，可使用**继承**。一个类**继承**另一个类时，将自动获得另一个类的所有属性和方法。原有的类称为**父类**，而新类称为**子类**。子类继承了父类所有属性和方法，同时还考研定义自己的属性和方法。

### 子类方法\__init__()

在既有类的基础上编写新类时，通常要调用父类的方法\__init__()。这将初始化在父类\__init__()方法中定义的所有属性，从而让子类包含这些属性。

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def update_odometer(self, mileage):
        self.odometer_reading = mileage
    def increment_odometer(self, miles):
        self.odometer_reading += miles 
    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")
    
class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)


my_tesla = ElectricCar('tesla', 'model s', 2019)
print(my_tesla.get_descriptive_name()) 
```

```python
2019 Tesla Model S
```

首先时Car类的代码。创建子类时，父类必须包含在当前文件按中，且位于子类前。然后定义子类ElectricCar。定义子类时，必须在圆括号内指定父类的名称。方法\__init__()接受创建Car时所需的信息。

super（）是一个特殊函数，让你能够调用父类的方法。这行代码让python调用Car类的方法\__init__(),让ElectricCar实例包含这个方法中定义的所有属性。父类也称**超类**，super由此而来。

### 给子类定义属性和方法

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def update_odometer(self, mileage):
        self.odometer_reading = mileage
    def increment_odometer(self, miles):
        self.odometer_reading += miles 
    def get_descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name.title()
    def read_odometer(self):
        print(f"This car has {self.odometer_reading} miles on it.")
    
class ElectricCar(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model, year)
        self.battery_size = 75
    def describe_battery(self):
        print(f"This car has a {self.battery_size}-kwh battery.")

my_tesla = ElectricCar('tesla', 'model s', 2019)
print(my_tesla.get_descriptive_name()) 
my_tesla.describe_battery()
```

```python
2019 Tesla Model S
This car has a 75-kwh battery
```

在上面，添加了新属性self.battery_size，并设置其初始值（75）。根据ElectricCar类创建的所有实例都将包含该属性，但所有Car实例都不包含它。还添加了一个名为describe_battery（）的方法，打印有关电瓶的信息。调用这个方法时，将看到一条电动汽车特有的描述。

### 重写父类的方法

对于父类的方法，只要它不符合子类模拟的实物行为，都可以进行重写。为此，可在子类中定义一个与要重写的父类方法同名的方法。这样，python将不会考虑这个父类方法，而只关注你在子类中定义的相应方法。

假设Car类有个名为fill_gas_tank()的方法，它对全电动汽车来说毫无意义，因此你可能像重写它。

```python
class ElectricCar(Car):
    --snip--
    
    def fill_gas_tank(self):
        print("This car doesn't need a gas tank!")
```

现在，如果对电动汽车调用方法fill_gas_tank()，python将忽略Car类中的方法fill_gas_tank（），转而运行上述代码。使用继承时，可让子类保留从父类那里继承而来的精华，并剔除不需要的糟粕。

## 



### 



