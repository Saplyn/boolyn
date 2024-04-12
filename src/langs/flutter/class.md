# Dart Classes

<div class="warning">

**This page is <u>INCOMPLETE</u>**

This page is incomplete and is still being written.

</div>

## Classes

```dart
class Cat {
    String name;
    int age;

    // constructor
    Cat(this.name, this.age);

    // named constructor
    Cat.fromName(String name) {
        this.name = name;
    }

    // method
    void meow() {
        print('Meow!');
    }
}
```

## Inheritance

```dart
class Animal {
    String name;
    int age;

    Animal(this.name, this.age);

    void eat() {
        print('$name is eating.');
    }
}

class Cat extends Animal {
    // propagate constructor
    Cat(String name, int age) : super(name, age);

    void meow() {
        print('Meow!');
    }
}
```

## Mixins

```dart
```
