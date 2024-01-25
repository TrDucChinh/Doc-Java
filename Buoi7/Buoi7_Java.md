- [Buổi 7: INTERFACE VÀ TRỪU TƯỢNG](#buổi-7-interface-và-trừu-tượng)
  - [Interface là gì?](#interface-là-gì)
    - [Cú pháp khai báo interface](#cú-pháp-khai-báo-interface)
    - [Lợi ích của interface](#lợi-ích-của-interface)
    - [Sử dụng interface khi](#sử-dụng-interface-khi)
  - [Abstract class](#abstract-class)
    - [Mục đích sử dụng](#mục-đích-sử-dụng)
  - [Khi nào sử dụng abstract class và interface](#khi-nào-sử-dụng-abstract-class-và-interface)
  - [So sánh interface và abstract class](#so-sánh-interface-và-abstract-class)
  - [Tính trừu tượng](#tính-trừu-tượng)

# Buổi 7: INTERFACE VÀ TRỪU TƯỢNG

## Interface là gì?
- Interface gần giống như aabstract class nhưng không phải class.
- Interface là một bản nguyên mẫu (hợp đồng) chỉ ra những hành động mà các lớp **implements** nó phải tuân thủ.
- Interface là một khái niệm trừu tượng, nó chỉ ra những gì mà một đối tượng có thể làm, nhưng không nói ra làm thế nào để đối tượng đó làm được điều đó.
- **VD:** Khi ta đăng ký một dịch vụ nào đó, sau khi đăng ký thì chung ta biết đã đăng ký dịch vụ đó và hằng ngày sử dụng nó còn chúng ta không hề biết nơi mà mình đăng ký nó thực hiện dịch vụ như nào. 
- Interface chỉ chứa các hằng số, các phương thức abstract, các phương thức default.
- Mặc định tất cả các phương thức trong interface là **public abstract**.
- Các biến trong interface là **public static final**

### Cú pháp khai báo interface

```Java
public interface People {
    public void eat();
    public void work();
}
```
- Interface People chỉ ra một People có thể làm được 2 việc là ăn và làm việc, nhưng không nói là làm thế nào để ăn và làm việc.
- Ví dụ ta có 1 class `Student` và `Teacher` thì ta có thể implement interface People vào 2 class này như sau:
```Java
public class Student implements People{
    @Override
    public void eat() {
        System.out.println("Eat rice");
    }

    @Override
    public void work() {
        System.out.println("Learn Java");
    }
}

public class Teacher implements People{
    @Override
    public void eat() {
        System.out.println("Eat noodle");
    }

    @Override
    public void work() {
        System.out.println("Teach Java");
    }
}
```
- Lúc này, ta có thể khởi tạo 2 đối tượng `Student` và `Teacher` và gọi các phương thức `eat()` và `work()` mà không cần quan tâm đến cách thức của 2 phương thức này.

```Java
public class main(){
    public static void main(String[] args) {
        People student = new Student();
        People teacher = new Teacher();

        student.eat();  //Eat rice
        student.work(); //Learn Java

        teacher.eat();  //Eat noodle
        teacher.work(); //Teach Java
    }
}
```
### Lợi ích của interface
- Chỉ ra những hành vi cần phải thực hiện ở các lớp **implements** nó.
- Cho phép đạt được tính trừu tượng hoàn toàn (Trong interface chỉ có phương thức abstract trừ phương thức default)
- Cho phép đa kế thừa: Một lớp chỉ có thể kế thừa một lớp khác nhưng có thể **implements** nhiều interface
- Cho phép đạt được tính chất loose coupling

**Tham Khảo: [Loose coupling](https://wiki.tino.org/loose-coupling-la-gi/)**

### Sử dụng interface khi
- Muốn đạt được tính chất đa kế thừa
- Đạt được tính trừ tượng hoàn toàn
- Muốn chỉ ra một hành động cụ thể nào đó cần thực hiện nhưng không quan tâm lớp nào sẽ thực hiện hành động đó

## Abstract class
**Tham Khảo: [Lớp Trừu Tượng](https://www.youtube.com/watch?v=FHxIAH0sXz0)**
- Abstract Class - Lớp trừu tượng, là 1 lớp trong Java, nhưng có thể chứa cả các phương thức trừu tượng (abstract method) và các phương thức thường (non-abstract method).

- Abstract Class không thể khởi tạo đối tượng, nhưng có thể khai báo biến kiểu Abstract Class, và khởi tạo đối tượng của class con của Abstract Class.

- Là lớp được khai báo với keyword `abstract`
- Thường chưa một hoặc nhiều phương thức `abstract`
- Phương thức abstract là phương thức chỉ khai báo, không định nghĩa. Việc định nghĩa cụ thể sẽ do các lớp con đảm nhiệm
- Nếu lớp con không định nghĩa các phương thức abstract của lớp cha thì nó phải trờ thành lớp abstract

**Question: Lớp abstract có thể có phương thức khỏi tạo hay không?**
> - Có thể chưa phương thức khỏi tạo nhưng ta không thể tạo đối tượng của lớp abstract.
> - Có thể tạo biến của lớp trừu tượng để tham chiếu đến các lớp con không phải là lớp abstract của lớp trừu tượng đó

- Có thể chứa cả các phương thức đã được định nghĩa và các thuộc tính, các trường static

### Mục đích sử dụng
- Ẩn giấu các cách thực thi cụ thể
- Cho phép thực hiện kế thừa nhưng không cho phép tạo đối tượng của lớp

**Ví Dụ:**
```Java
public abstract class Animal {
    public abstract void eat();
    public void travel() {
        System.out.println("Animal is travelling");
    }
}

public class Dog extends Animal {
    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }
}

public class Cat extends Animal {
    @Override
    public void eat() {
        System.out.println("Cat is eating");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        Animal cat = new Cat();

        dog.eat();
        dog.travel();

        cat.eat();
        cat.travel();
    }
}

//Dog is eating
//Animal is travelling
//Cat is eating
//Animal is travelling
```

## Khi nào sử dụng abstract class và interface

- **Sử dụng `abstract class` nếu:**
  - Chia sẻ code giữa các lớp trong quan hệ kế thừa
  - Muốn lớp này chứa cả các thành phần private, protected
  - Muốn lớp này chứa cả những thành phần khác statc, final
- **Sử dụng `interface` nếu:**
  - Định nghĩa các chức năng, các giá trị chung cho các lớp không có mối quan hệ liên quan với nhau
  - Muốn tận dụng lợi ích của đa kế thừa
  - Muốn xác định các hành vi nhưng không quan tâm lớp nào sẽ thực thi chúng

**Ví Dụ**
- **Abstract class**
```Java
public abstract class Animal{
    private String someProperty;
    protected float otherProperty;

    public abstract void move();
    public abstract void eat();
}

public class Bird extends Animal(){
    @Override
    public void move(){

    }

    @Override
    public void eat(){

    }
}

public class Fish extends Animal(){
    @Override
    public void move(){

    }
    
    @Override
    public void eat(){

    }
}
```
- **Interface**
```Java
public interface MyInterface{
    String MESSAGE = "Hihi";
    void saySomething(String something); //Phương thức dùng chung
}

```

## So sánh interface và abstract class

| Interface | Abstract Class |
| --- | --- |
| Interface chỉ có thể chứa các phương thức trừu tượng | Abstract Class có thể chứa cả các phương thức trừu tượng và các phương thức thường |
| Interface không thể khởi tạo đối tượng | Abstract Class không thể khởi tạo đối tượng |
| Biến trong interface mặc định là `public static final` | Biến trong abstract class không có mặc định gì cả |
| Interface không có constructor | Abstract Class có constructor |
| Interface không có gì để ghi đè | Abstract Class có thể có các phương thức để ghi đè |
| Interface có thể kế thừa nhiều interface khác | Abstract Class chỉ có thể kế thừa 1 abstract class khác |
| Các class implement interface có thể implement nhiều interface khác | Các class kế thừa từ abstract class chỉ có thể kế thừa 1 abstract class khác|

## Tính trừu tượng
- Tính trừu tượng là gì?
  - Là một trong bốn tính chất cơ bản của lập trình hướng đối tượng trong Java.
  - Tính trừu tượng giúp bạn tập trung vào những cốt lõi cần thiết của đối tượng thay vì quan tâm đến cách nó thực hiện.
  - Tính trừu tượng là một tiến trình ẩn các chi tiết trình triển khai và chỉ hiển thị tính năng tới người dùng. Tính trừu tượng cho phép bạn loại bỏ tính chất phức tạp của đối tượng bằng cách chỉ đưa ra các thuộc tính và phương thức cần thiết của đối tượng trong lập trình.