# Dart Practice Problems
1- Write a function that takes a positive integer n and prints all the numbers from 1 to n, each on a separate line.
```
void positiveIntegerNum(int n) {
  for (int i = 1; i <= n; i++){
    print(i);
  }
}

void main() {
  int n = 5;
  positiveIntegerNum(n);
}
```
2- Write a function that takes a positive integer n and returns the sum of all numbers from 1 to n.
```
int positiveIntegerNum(int n) {
  int sum = 0;
  for (int i = 1; i <= n; i++) {
    sum += i;
  }
  return sum;
}

void main(){
  int n = 5;
  int result = positiveIntegerNum(n);
  print(result);
}
```
3- Write a function that takes a list of integers (List<int>) and returns the sum of the even numbers only.
```
int sumEvenNumbers(List <int> n) {
  int sum = 0;
  for (int number in n) {
    if(number % 2 == 0) {
      sum += number;
    }
  }
  return sum;
}

void main(){
  List<int> x =[1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  print(sumEvenNumbers(x)); 
}
```
4- Write a function that takes a list of integers and returns the maximum number in that list.
```
int findMaxNum(List<int> number) {
  int max = number[0];
  for(int i = 1; i < number.length; i++){
    if(number[i] > max){
      max = number[i];
    }
  }
  return max;
}

void main(){
  List<int> n = [0,2,7,4];
  int result = findMaxNum(n);
  print(result);
}
```
5- Write a function that takes a string and returns the string reversed.
```
String reverseText(String text){
  String reversedText = '';
  for(int i = text.length - 1; i >= 0 ;i--){
    reversedText += text[i];
  }
  return reversedText;
}

void main(){
  String text ="Hello";
  String result = reverseText(text);
  print(result);
}

OR

String reverseText(String text){
  return text.split('').reversed.join();
}

void main(){
  String text ="Hello";
  String result = reverseText(text);
  print(result);
}
```
6- Write a function that checks if a number is a prime number. (A prime number is a number greater than 1 that has no positive divisors other than 1 and itself).
```
void findPrimeNumber(int number) {
  if(number <= 1){
    print(false);
  }
  for(int i = 2; i< number; i++){
    if(number % i == 0){
      print("false"); // إذا العدد يقبل القسمة على أي رقم من 2 لحد العدد نفسه، يبقى مش أولي
      return;
    }
  }
  print("true");
}

void main() {
  int n = 7;
  findPrimeNumber(n);
}
```
