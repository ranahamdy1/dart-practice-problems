# Dart Practice Problems

1- Write a function that takes a positive integer n and prints all the numbers from 1 to n, each on a separate line.
```dart
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
```dart
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
```dart
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
```dart
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
```dart
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
```dart
void findPrimeNumber(int number) {
  if(number <=1){
    print("false");
    return; //stop function here
  }

  for(int i=2; i < number; i++){
    if(number%i == 0){
      print("false");
      return; //stop function here => ex 9 when number = 3 it false then stop the function here
    }
  }

  print("true"); // If the loop completes without finding a divisor, the number is prime
}

void main() {
  int n = 9;
  findPrimeNumber(n);
}
```

7- Write a function that takes a string and returns the number of vowels (a, e, i, o, u) in it. The function should ignore uppercase/lowercase differences.
```dart
int vowelsNumber(String num) {
  String lowerText = num.toLowerCase(); //to make all text lower to ignore uppercase/lowercase differences.
  int count = 0;

  for(int i = 0;i < lowerText.length; i++){
    if(lowerText[i] == 'a' ||
       lowerText[i] == 'e' ||
       lowerText[i] == 'i' ||
       lowerText[i] == 'o' ||
       lowerText[i] == 'u'){
      count++;
    }
  }
  return count;
}

void main(){
  String text = "Hello World";
  int result = vowelsNumber(text);
  print(result);
}
```

8- Write a function that takes a list of integers and returns the number that appears most frequently in the list. If multiple numbers appear the same number of times, return any one of them.
```dart
int findMostFrequentNumber(List<int> numbers){
  Map<int, int> frequencyMap = {}; // نستخدم map علشان نحسب كم مرة كل رقم اتكرر

  //  نحسب تكرار كل رقم ونخزن النتيجة في الـ Map
  for(int number in numbers){
    if(frequencyMap.containsKey(number)) {
      frequencyMap[number] = frequencyMap[number]! + 1;
    }else {
      frequencyMap[number] = 1;
    }
  }

  //نحدد الرقم اللي تكرر أكتر
  int mostFrequentNumber = numbers[0];
  int count = 1;
  frequencyMap.forEach((key, value) {
    if(value > count){
      count = value;
      mostFrequentNumber = key;
    }
  });

  return mostFrequentNumber;
}

void main(){
  List<int> n = [1, 2, 3, 4, 5, 1, 2, 3, 1];
  print(findMostFrequentNumber(n));
}
```

9- Write a function that takes a list of integers and returns how many numbers are repeated (appeared more than once) in that list.
```dart
int repeatedNumber(List<int> numbers) {
  Map<int, int> frequencyMap = {};

  //  نحسب تكرار كل رقم ونخزن النتيجة في الـ Map
  for(int number in numbers){
    if(frequencyMap.containsKey(number)){
      frequencyMap[number] = frequencyMap[number]! + 1;
    } else {
      frequencyMap[number] = 1;
    }
  }

  //  نحسب عدد الأرقام اللي اتكررت أكتر من مرة
  int repeatedCount = 0;
  for (int value in frequencyMap.values) {
    if (value > 1) {
      repeatedCount++;
    }
  }

  return repeatedCount;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5, 1, 2, 3];
  int result = repeatedNumber(numbers);
  print(result);
}
```

10- Write a function that takes a list of integers and returns a list of numbers that appear more than once.
```dart
List<int> mostRepeatedNumbers(List<int> numbers){
  Map<int, int> frequency = {};
  for(int number in numbers){
    if(frequency.containsKey(number)){
      frequency[number] = frequency[number]! + 1;
    }else{
      frequency[number] = 1;
    }
  }

  List<int> repeatedList =[];
  for(int value in frequency.keys){
    if(frequency[value]! > 1){
      repeatedList.add(value);
    }
  }
  return repeatedList;
}

void main(){
  List<int> numbers = [1,2,3,4,5,6,7,8,8,9,9,1,10];
  print(mostRepeatedNumbers(numbers));
}
```

11- Write a function that checks whether two lists contain the same elements regardless of order and duplicates.
```dart
bool areListEqual(List<int> list1, List<int> list2){
  Set set1 = list1.toSet();
  Set set2 = list2.toSet();

  return set1.containsAll(set2) && set2.containsAll(set1);
}
void main(){
  List<int> list1 = [1,2,3,4,5];
  List<int> list2 = [1,2,3,4,5];
  print(areListEqual(list1, list2));
}
```

12- Write a function that returns the common elements between two lists (without duplicates).
```dart
Set<int> commonInTwoList(List<int> list1, List<int> list2){
  Set<int> set1 = list1.toSet();
  Set<int> set2 = list2.toSet();

  //intersection() بتجيب العناصر المشتركة فقط بين set1 و set2.
  return set1.intersection(set2);
}
void main(){
  List<int> list1 = [1,2,3,4,5];
  List<int> list2 = [1,2,3,4,5];
  print(commonInTwoList(list1, list2));
}
```

13- Write a function that removes all duplicate values from a list and returns a new list with unique values only.
```dart
List<int> removeDuplicateValues(List<int> list) {
  List<int> setToList = list.toSet().toList();
  return setToList;
}
void main(){
  List<int> list = [1,2,3,4,5,6,7,8,9,10,1,2,3,4,5];
  List<int> result = removeDuplicateValues(list);
  print(result);
}
```

14- Write a function that takes a list of integers and returns the first number that is repeated.
```dart
int firstRepeatedNumber(List<int> numbers){
  Map<int,int> map = {};
  for(int number in numbers){
    if(map.containsKey(number)){
      // لو موجود يبقى ده أول رقم اتكرر نرجّعه فورًا.
      return number;
    }else{
      //لو مش موجود يبقى أول مرة نشوفه فبنضيف الرقم في الماب علشان نفتكره لو شوفناه تاني
      map[number] = 1;
    }
  }
  return -1;
}

void main(){
  List<int> numbers = [1,2,3,4,5,6,7,8,9,10,4,6];
  print(firstRepeatedNumber(numbers));
}
```

15- Write a function that returns the only number in the list that appears exactly once.(Assume that at most one such number exists.) If no such number exists, return -1.
```dart
int repeatOnlyOne(List<int> numbers){
  Map<int, int> frequency = {};

  for (int number in numbers) {
    frequency[number] = (frequency[number] ?? 0) + 1;
  }

  for (int number in numbers) {
    if (frequency[number] == 1) {
      return number;
    }
  }

    return -1;
}

void main(){
  List<int> numbers = [4, 1, 2, 2];
  print(repeatOnlyOne(numbers));
}
```

16- Write a function that returns the list of number that appears exactly once.
```dart
List<int> repeatOnlyOne(List<int> numbers){
  Map<int, int> frequency = {};

  for (int number in numbers) {
    frequency[number] = (frequency[number] ?? 0) + 1;
  }

  List<int> repeatedList =[];
  for (int number in frequency.keys) {
    if (frequency[number] == 1) {
      repeatedList.add(number);
    }
  }
  return repeatedList;
}

void main(){
  List<int> numbers = [4, 1, 2, 2];
  print(repeatOnlyOne(numbers));
}
```

17- Write a function that takes a list of integers from 1 to n with one number missing, and returns the missing number.
```dart
int findMissingNumber(List<int> numbers) {
  int listTotalNumber = numbers.length +1;
  int totalSum = listTotalNumber * (listTotalNumber + 1) ~/ 2; // مجموع الأرقام من 1 إلى n( n * (n + 1) ~/ 2)
  int listSum = numbers.reduce((a, b) => a + b); // مجموع الأرقام الموجودة
  int result = totalSum - listSum;
  return result;
}
void main() {
  List<int> numbers = [1, 2, 3, 5];
  print(findMissingNumber(numbers));
}
```

18- Write a function that checks if a list of integers is the same forwards and backwards.
```dart
bool sameForwardAndBackwards(List<int> numbers) {
  int firstNumber = 0;
  int lastNumber = numbers.length - 1;
  while(firstNumber<lastNumber){
    if(numbers[firstNumber] != numbers[lastNumber]){
      return false;
    }
    firstNumber++;
    lastNumber--;
  }
  return true;
}

void main(){
  List<int> list = [1,2,3,2,1];
  print(sameForwardAndBackwards(list));
}
```

19- Write a function that checks if a number is a perfect square.
```dart
import 'dart:math';
bool isPerfectSquare(int number){
  if(number < 0){
    return false;
  }

  int sqrtNum = sqrt(number).toInt(); // حساب الجذر التربيعي
  return sqrtNum * sqrtNum == number;
}

void main() {
  print(isPerfectSquare(16)); //true
  print(isPerfectSquare(22)); //false
}
```

20- Write a function to find the longest word in a list of strings.
```dart
String findLongestWord(List<String> words) {
  String longestWord = '';
  for (String word in words) {
    if (word.length > longestWord.length) {
      longestWord = word;
    }
  }
  return longestWord;
}

void main(){
  List<String> words = ["apple", "banana", "cherry", "watermelon"];
  print(findLongestWord(words));
}
```

21- Write a function that reverses a string.
```dart
String reverseWord(String word) {
  return word.split('').reversed.join('');
}

void main(){
  String word = "Hello";
  print(reverseWord(word));
}
```

22- Write a function that finds the sum of all even numbers in a list.
```dart
int sumEventNumbers(List<int> numbers) {
  int sum = 0;
  for (int number in numbers){
    if(number % 2 == 0){
      sum += number;
    }
  }
  return sum;
}

void main(){
  List<int> numbers = [1, 2, 3, 4, 5, 6];
  print(sumEventNumbers(numbers));
}
```

23- Write a function to calculate the factorial of a number.
```dart
int factorial(int number) {
  if(number == 0 || number == 1){
    return 1;
  } else {
    return number * factorial(number - 1);
  }
}

void main(){
  int number = 5;
  print("The factorial of $number is ${factorial(number)}");
}
```

24- Write a function to count how many times a specific number appears in a list.
```dart
int numberAppear (List<int> list, int number) {
  int count = 0;
  for(int i =0; i<list.length; i++){
    if(list[i] == number){
      count++;
    }
  }
  return count;
}

void main() {
  List<int> list = [1,2,3,4,5,6,7,8,9,5,10];
  int number = 5;
  print(numberAppear(list, number));
}
```

25- Write a function to merge two lists into a single list.
```dart
List<int> mergeTwoLists(List<int> list1, List<int>list2) {
  List<int> mergedList = [];
  mergedList.addAll(list1);
  mergedList.addAll(list2);
  return mergedList;
}
void main() {
  List<int> list1 = [1, 2, 3];
  List<int> list2 = [4, 5, 6];
  List<int> mergedList = mergeTwoLists(list1, list2);
  print(mergedList);
}
```

26- Write a function that removes all odd numbers from a list.
```dart
List<int> removeOddNumbers(List<int> numbers) {
  List<int> numbersList = [];
  for(int number in numbers) {
    if(number%2 ==0){
      numbersList.add(number);
    }
  }
  return numbersList;
}
void main() {
  List<int> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
  print(removeOddNumbers(numbers));
}
```

27- Write a function that returns the maximum difference between any two elements in a list of integers.
```dart
int maxDifference(List<int> numbers) {
  int maxNum = numbers[0];
  int minNum = numbers[0];
  for (int i = 1; i < numbers.length; i++) {
    if (numbers[i] > maxNum) {
      maxNum = numbers[i];
    }
    if (numbers[i] < minNum) {
      minNum = numbers[i];
    }
  }
  return maxNum - minNum;
}

void main() {
  List<int> numbers = [3, 5, 1, 9, 2];
  print(maxDifference(numbers));
}
```

28- Write a function that returns the second largest number in a list.
```dart
int secondLargestNumber(List<int> number) {
  number.sort();
  return number[number.length - 2];
}

void main() {
List<int> numbers = [1, 2, 3, 4, 5];
  print(secondLargestNumber(numbers));
}

OR

int? secondLargestNumber(List<int> numbers) {
  int maxNumber = numbers[0];
  int? secMaxNumber;

  for(int number in numbers) {
    if (number > maxNumber) {
      secMaxNumber = maxNumber;
      maxNumber = number;
    }else if ((secMaxNumber == null || number > secMaxNumber) && number != maxNumber) {
      secMaxNumber = number;
    }
  }
  return secMaxNumber;
}

void main() {
  List<int> numbers = [4, 1, 2, 6, 9, 5];
  print(secondLargestNumber(numbers));
}
```

29- Write a function that finds all duplicates in a list.
```dart
List<int> findDuplicated(List<int> numbers) {
  Map<int, int> countMap = {};

  for (int number in numbers) {
    if (countMap.containsKey(number)) {
      countMap[number] = countMap[number]! + 1;
    } else {
      countMap[number] = 1;
    }
  }

  List<int> duplicates = [];
  for (var entry in countMap.entries) {
    if (entry.value > 1) {
      duplicates.add(entry.key);
    }
  }
  return duplicates;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5, 1, 2, 3];
  print(findDuplicated(numbers));
}
```

30- Write a function that returns all numbers in a list that are greater than the average of the list.
```
List<int> graterThanAverage(List<int> numbers) {
  int average;
  int sum = 0;
  for (int number in numbers) {
    sum += number;
  }
  average = sum ~/ numbers.length;
  List<int> result = [];
  for (int number in numbers) {
    if (number > average) {
      result.add(number);
    }
  }
  return result;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5];
  print(graterThanAverage(numbers));
}
```
