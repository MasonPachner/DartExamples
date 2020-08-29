# Dart
Functions are 1st order arguments in Dart, meaning that they can be passed as an argument to a function. Use the name of the function(Function pointer) when passing it.
This can be useful when functions have similar requirements, but need something unique done somewhere else in the function.

`main.dart`
```dart
void main(){
  String elmo = "elmo";
  String bert = "bert";
  print(useAFunction(hashtagIt,elmo));
  print(useAFunction(hashtagItSquared,bert));
}

String useAFunction(Function funct, String arg){
  return funct(arg) + "|Fun|";
}

String hashtagIt(String string){
  return "#" + string;
}
String hashtagItSquared(String string){
  return hashtagIt(string) + hashtagIt(string);
}
```
`Output`
```text
#elmo|Fun|
#bert#bert|Fun|
```
## Big arrow syntax
Big arrow syntax is a simple way to make 1 line functions easier to read. A big arrow `=> ... ;` replaces `{return ...;}`. Converting the same example as before

`main.dart`
```dart
void main(){
  String elmo = "elmo";
  String bert = "bert";
  print(useAFunction(hashtagIt,elmo));
  print(useAFunction(hashtagItSquared,bert));
}

String useAFunction(Function funct, String arg) => funct(arg) + "|Fun|";

String hashtagIt(String string) => "#" + string;

String hashtagItSquared(String string) => hashtagIt(string) + hashtagIt(string);

```
`Output`
```text
#elmo|Fun|
#bert#bert|Fun|
```

## Lambdas

Lamdas are great for simple functions that only need to be defined once. We can use big arrow syntax or not, depending on how many lines the function is. Lamda syntax is `(arg,arg2,etc){return ans;}` or with the big arrow, `(arg,arg2,etc)=>ans`

`main.dart`
```dart
void main(){
  String elmo = "elmo";
  String bert = "bert";
  print(useAFunction(hashtagIt,elmo));
  // Lamda with big arrow syntax. All I did was copy in everything past the function name.
  print(useAFunction((String string) => hashtagIt(string) + hashtagIt(string),bert));
  
  // This one is a big trickier. I create and call the lambda in the same expression. 
  print((String printMe){
      return printMe + "!"
  }("Hello world"));

  // Without the immediate call afterwards, this would have printed 'instance of Function' because I just passed the print statment a function, not a string.
  // print((String printMe){
  //   return printMe + "!"
  // });

  // In big arrow syntax, I would have to wrap the definition with parenthesis, so it knows to have "Hello world" as an argument
  // print(((String printMe)=> printMe + "!")("Hello world"));
}

String useAFunction(Function funct, String arg) => funct(arg) + "|Fun|";

String hashtagIt(String string) => "#" + string;

```
`Output`
```text
#elmo|Fun|
#bert#bert|Fun|
Hello world!
```

## Advanced argument lists

Simple functions are easy to write with postitional arguments because it's easy to remember what argument goes where. Once you have tons of small functions or large functions, 
positional arguments can become unweildy, and I advise using named parameters. This first example is a good case to use postitional parameters. The function is simple and the name
is good enough to imply what the function does.

`main.dart`
```dart
void main()=>fibonacci(4);

int fibonacci(int n){
    if(n <= 1){
        return n;
    }
    return fibonacci(n-1) + fibonacci(n-2)
};

```
`Output`
```text
3
```

Next up is a worst case scenario.

`main.dart`
```dart
void main()=>createPerson("Bob","10/3/95","10/3/06","Somewhere",25,2,2,"orange","orange");

void createPerson(String name, String birthday, String hireDate, String address, int age, int children, int legs, String favoriteColor, String favoriteFruit){
    print("Name: $name"); // Imbedded string, uses variable in string
    print("Birthday: $birthday");
    print("hireDate: $hireDate");
    print("address: $address");
    print("age: $age");
    print("children: $children");
    print("legs: $legs");
    print("favoriteColor: $favoriteColor");
    print("favoriteFruit: $favoriteFruit");
};

```
`Output`
```text
Bob
10/3/95
10/3/06
Somewhere
25
2
2
orange
orange
```

Say I want to go in later and change Bob's favorite color... things get a bit weird and hard to read. In order to combat this, we use named parameters. It takes a bit more writing up front, but saves time in the long run. Wrap parameters with curly braces to make them named. I will keep the name parameter positional (Similar to Text widget!)


```dart
void main()=>createPerson("Bob", // saying name: "Bob", would be a syntax error because bob is not named
                            birthday:"10/3/95",
                            hireDate:"10/3/06",
                            address:"Somewhere",
                            age:25,
                            children:2,
                            legs:2,
                            favoriteColor:"orange",
                            favoriteFruit:"orange",
                        );

void createPerson(String name, {String birthday, String hireDate, String address, int age, int children, int legs, String favoriteColor, String favoriteFruit}){
    print("Name: $name"); // Imbedded string, uses variable in string
    print("Birthday: $birthday");
    print("hireDate: $hireDate");
    print("address: $address");
    print("age: $age");
    print("children: $children");
    print("legs: $legs");
    print("favoriteColor: $favoriteColor");
    print("favoriteFruit: $favoriteFruit");
};

```
`Output`
```text
Bob
10/3/95
10/3/06
Somewhere
25
2
2
orange
orange
```