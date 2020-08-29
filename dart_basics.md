# Dart
Dart files use the .dart file extension, and by tradition the launch file in named main. `main.dart`
Inside of `main.dart` there should be a `main` function. This is mandatory and is the entry point of
you program. You can run files in the terminal with `dart ./main.dart` (with proper pathing)
`main.dart`
```dart
void main(){
  print("Hello world");
}
```
`Output`
```text
Hello world
```

Dart has standard C style loops, conditions and variable assignment (white lie)

`main.dart`
```dart
void main(){
  String hello = "Hello world";
  int a = 100;
  for(int i = 0; i < a; i+=10){
    print(i);
  }
  while(false){
    print("false false!");
  }
  bool notTrue = false;
  if(notTrue){
    print("Broken.");
  }
  print(hello);
}
```
`Output`
```text
00
10
20
30
40
50
60
70
80
90
Hello world
```

Functions have several ways of taking arguments. They can take arguments, positionally, optional posistionally, optional named, and required named. Postional arguments are traditional arguments. I'll talk about the other methods later.

`main.dart`
```dart
void main(){
  String elmo = "elmo";
  String ans = concatStrings(elmo,"bert");
  print(ans);
}
String concatStrings(String a, String b){
  return a + ", " + b;
}
```
`Output`
```text
elmo, bert
```


