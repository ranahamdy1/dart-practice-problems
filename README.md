# Dart Practice Problems

1- Given a name S. Print "Welcome, (name)"
```dart
import 'dart:io';
void main(){
  print("Enter your name");
  String name = stdin.readLineSync()!;
  print("Welcome, $name");
}
```

2- You are given a person's systolic blood pressure,A ,and diastolic blood pressure,B, Find the mean arterial pressure,C ,which we define as follows: C = ((A−B)/3)+B
```dart
import 'dart:io';
void main() {
  int A = int.parse(stdin.readLineSync()!);
  int B = int.parse(stdin.readLineSync()!);
  double C = ((A - B)/3)+B;
  print(C);
}
```

3- Write a function that takes a positive integer n and prints all the numbers from 1 to n, each on a separate line.
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

4- Write a function that takes a positive integer n and returns the sum of all numbers from 1 to n.
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

5- Write a function that takes a list of integers (List<int>) and returns the sum of the even numbers only.
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

6- Write a function that takes a list of integers and returns the maximum number in that list.
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

7- Write a function that takes a string and returns the string reversed.
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

8- Write a function that checks if a number is a prime number. (A prime number is a number greater than 1 that has no positive divisors other than 1 and itself).
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

9- Write a function that takes a string and returns the number of vowels (a, e, i, o, u) in it. The function should ignore uppercase/lowercase differences.
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

10- Write a function that takes a list of integers and returns the number that appears most frequently in the list. If multiple numbers appear the same number of times, return any one of them.
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

11- Write a function that takes a list of integers and returns how many numbers are repeated (appeared more than once) in that list.
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

12- Write a function that takes a list of integers and returns a list of numbers that appear more than once.
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

13- Write a function that checks whether two lists contain the same elements regardless of order and duplicates.
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

14- Write a function that returns the common elements between two lists (without duplicates).
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

15- Write a function that removes all duplicate values from a list and returns a new list with unique values only.
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

16- Write a function that takes a list of integers and returns the first number that is repeated.
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

17- Write a function that returns the only number in the list that appears exactly once.(Assume that at most one such number exists.) If no such number exists, return -1.
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

18- Write a function that returns the list of number that appears exactly once.
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

19- Write a function that takes a list of integers from 1 to n with one number missing, and returns the missing number.
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

20- Write a function that checks if a list of integers is the same forwards and backwards.
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

21- Write a function that checks if a number is a perfect square.
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

22- Write a function to find the longest word in a list of strings.
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

23- Write a function that reverses a string.
```dart
String reverseWord(String word) {
  return word.split('').reversed.join('');
}

void main(){
  String word = "Hello";
  print(reverseWord(word));
}
```

24- Write a function that finds the sum of all even numbers in a list.
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

25- Write a function to calculate the factorial of a number.
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

26- Write a function to count how many times a specific number appears in a list.
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

27- Write a function to merge two lists into a single list.
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

28- Write a function that removes all odd numbers from a list.
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

29- Write a function that returns the maximum difference between any two elements in a list of integers.
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

30- Write a function that returns the second largest number in a list.
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

31- Write a function that finds all duplicates in a list.
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

32- Write a function that returns all numbers in a list that are greater than the average of the list.
```dart
List<int> greaterThanAverage(List<int> numbers) {
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
  print(greaterThanAverage(numbers));
}
```

33- Write a function that returns the top 2 most frequent numbers in a list.
```dart
List<int> topTwoFrequent(List<int> numbers) {
  Map<int, int> freq = {};

  // نحسب التكرارات
  for (int number in numbers) {
    if (freq.containsKey(number)) {
      freq[number] = freq[number]! + 1;
    } else {
      freq[number] = 1;
    }
  }

  int? firstMax;
  int? secondMax;
  int firstCount = 0;
  int secondCount = 0;

  for (var entry in freq.entries) {
    if (entry.value > firstCount) {
      secondMax = firstMax;
      secondCount = firstCount;
      firstMax = entry.key;
      firstCount = entry.value;
    } else if (entry.value > secondCount) {
      secondMax = entry.key;
      secondCount = entry.value;
    }
  }

  // نرجّعهم في List
  List<int> result = [];
  if (firstMax != null) result.add(firstMax);
  if (secondMax != null) result.add(secondMax);
  return result;
}

void main() {
  List<int> numbers = [4, 1, 2, 4, 2, 2, 3, 1, 4];
  print(topTwoFrequent(numbers));
}
```

34- Given a number N. Print a diamond that has 2N rows.
```
    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *

```
```dart
void diamond(int n){
  // Upper part (including middle)
  for (int i = 1; i <= n; i++) {
    String spaces = ' ' * (n - i);
    String stars = '*' * (2 * i - 1); //علشان نطبع عدد فردي من النجوم (1, 3, 5, 7...)
    //2*1 -1 = 2-1 = 1
    //2*2 -1 = 4-1 = 3
    //2*3 -1 = 6-1 = 5
    //2*4 -1 = 8-1 = 7
    //2*5 -1 = 10-1 = 9 (middle)
    print(spaces + stars);
  }
  // Lower part
  for(int i=n-1; i >= 1; i--){
    String spaces = ' ' * (n - i);
    String stars = '*' * (2 * i - 1);
    //2*4-1=7
    //2*3-1=5
    //2*2-1=3
    //2*1-1=1
    print(spaces + stars);
  }
}
void main() {
  int number = 5;
  diamond(number);
}
```

35- Given a number N and an array A of N numbers. print the sum of maximum 4 number and minimum 4 number
```dart
void maxAndMinNumber(int N, List<int> A) {
  if (N < 4) {
    print('The list must contain at least 4 numbers.');
    return;
  }
  A.sort(); //يقوم بترتيب القائمة A من الأصغر إلى الأكبر
  int minSum = A.sublist(0, 4).reduce((a, b) => a + b);     // مجموع أصغر 4 أرقام
  //A.sublist(0, 4) → يأخذ أول 4 عناصر من القائمة
  // .reduce((a, b) => a + b) → يجمعهم مع بعض
  int maxSum = A.sublist(N - 4, N).reduce((a, b) => a + b); // مجموع أكبر 4 أرقام
  //A.sublist(N - 4, N) → يأخذ آخر 4 عناصر
  // .reduce((a, b) => a + b) → يجمعهم
  print('Sum of smallest 4 numbers: $minSum');
  print('Sum of largest 4 numbers: $maxSum');
}

void main(){
  int number = 5;
  List<int> list = [5,4,3,2,1];
  maxAndMinNumber(number, list);
}
```

36- You're given a list of integers. Write a function that counts how many times each number appears.
```dart
void timeNumberAppear(List<int> numbers) {
  Map<int,int> frequency ={};

  for (int number in numbers) {
    if (frequency.containsKey(number)) {
      frequency[number] = frequency[number]! + 1;
    } else {
      frequency[number] = 1;
    }
  }
  print(frequency);
}

void main() {
  List <int> numberList =[1,2,3,2,3];
  timeNumberAppear(numberList);
}
```

37- Given a list of integers, sort the list in ascending order and return the result.
```dart
List<int> sortedList(List<int> list) {
  list.sort();
  return list;
}

void main() {
  List<int> list = [1,12,3,14,5];
  print(sortedList(list));
}
```

38- Given a sorted list of integers and a target number, return true if the number exists in the list, otherwise return false. (Use binary search logic (don't use .contains() or .indexOf())).
```dart
bool isNumInList(List<int>list, int number) {
  int left = 0;
  int right = list.length - 1;

  while(left <= right) {
    int mid = (left + right) ~/ 2;

    if (list[mid] == number) {
      return true;
    } else if(list[mid] <number){
      left = mid + 1;
    }else{
      right = mid - 1;
    }
  }
  return false;
}

void main() {
  List<int> list = [1,4,6,8];
  int number = 4;
  print(isNumInList(list, number));
}
```

39- Write a recursive function to calculate the factorial of a number n.
```dart
num factorial (int number) {
  if(number == 0 || number == 1){
    return 1;
  }else{
    return number * factorial(number-1);
  }
}

void main() {
  int number = 5;
  print(factorial(number));
}
```

40- Write a recursive function to find the sum of all natural numbers from 1 to n.
```dart
int sumOfNumber(int number) {
  if(number ==0){
    return 0;
  }else {
    return number + sumOfNumber(number - 1);
  }
}

void main() {
  int number = 5;
  print(sumOfNumber(number));
}
```

41- Write a recursive function to find the n-th Fibonacci number. (0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...) (كل رقم فيها = مجموع الرقمين اللي قبله)
```dart
int fibonacci(int n) {
  if (n == 0) {
    return 0;
  } else if (n == 1) {
    return 1;
  } else {
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}

void main() {
  int n = 6;
  print(fibonacci(n));
}
```

42- Write a function that checks if a list is a palindrome using two pointers. (A palindrome list is one that reads the same forward and backward)
```dart
bool palindrome(List<int> list) {
  int left = 0;
  int right = list.length - 1;
  while(left<right) {
    if(list[left] != list[right]) {
      return false;
    }
    left++;
    right--;
  }
  return true;
}

void main() {
  List<int> list = [1, 2, 3, 2, 1];
  print(palindrome(list));
}
```

43- Write a function that checks if there are two numbers in a sorted list that sum to a target.
```dart
bool twoNumber(List<int> list, int target) {
  list.sort();
  int left = 0;
  int right = list.length - 1;
  while(left < right) {
    int sum = list[left] + list[right];
    if (sum == target) {
      return true;
    }else if(sum < target) {
      left++;
    }else{
      right--;
    }
  }
  return false;
}

void main() {
  List<int> list = [1, 2, 3, 4, 5];
  int target = 9;
  print(twoNumber(list, target));
}
```

44- Write a function that checks if there are two numbers in a sorted list that sum to a target.
```dart
List<List<int>> twoNumber(List<int> list, int target) {
  list.sort();
  int left = 0;
  int right = list.length - 1;
  List<List<int>> result = [];

  while (left < right) {
    int sum = list[left] + list[right];
    if (sum == target) {
      result.add([list[left], list[right]]);

      // تجاهل الأرقام المكررة
      int currentLeft = list[left];
      int currentRight = list[right];
      while (left < right && list[left] == currentLeft) left++;
      while (left < right && list[right] == currentRight) right--;

    } else if (sum < target) {
      left++;
    } else {
      right--;
    }
  }
  return result;
}

void main() {
  List<int> list = [1, 2, 2, 3, 4, 5];
  int target = 4;
  print(twoNumber(list, target));
}
```

45- You are given a list of integers where every element appears twice except one element, which appears only once.
```dart
int uniqueElement(List<int> list) {
  int unique = 0;
  for (int i = 0; i < list.length; i++) {
    unique ^= list[i]; // XOR operation
  }
  return unique;
}

void main() {
  List<int> list = [1, 2, 3, 4, 5, 1, 2, 3, 4];
  print(uniqueElement(list));
}
```

46- Given a list of integers and a target value, count how many pairs (i, j) exist such that i < j and arr[i] + arr[j] == target.
```dart
int numberOfPairs(List<int> list, int target) {
  int count = 0;
  for(int i= 0; i<list.length ; i++) {
    for(int j = i+1; j<list.length; j++) {
      if(list[i] + list[j] == target) {
        count++;
      }
    }
  }
  return count;
}

void main() {
  List<int> arr = [1, 2, 3, 4, 5];
  int target = 6; // 2 >> [2,4] , [1,5]
  print(numberOfPairs(arr, target));
}
```

47- Write a Dart function that returns the index of the first element in a list that is equal to a target number. If the number is not found, return -1.
```dart
int indexInList(List<int> list, int target) {
  for(int i = 0; i < list.length; i++) {
    if(list[i] == target) {
      return i;
    }
  }
  return -1;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5];
  int target = 3;
  print(indexInList(numbers, target));
}
```
48- Write a Dart function that returns a list of all pairs of numbers in the input list that sum up to a given target.
```dart
List<List<int>> pairNumber(List<int> list, int target) {
  List<List<int>> result = [];
  for(int i = 0; i < list.length; i++) {
    for(int j = i + 1; j < list.length; j++) {
      if(list[i] + list[j] == target) {
        result.add([list[i], list[j]]);
      }
    }
  }
  return result;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5];
  int target = 3;
  print(pairNumber(numbers, target));
}
```

49- Write a Dart function that counts how many even numbers are in a list.
```dart
int numberOfEven(List<int> numbers) {
  int count = 0;
  for(int i =0; i<numbers.length; i++) {
    if(numbers[i] % 2==0) {
      count++;
    }
  }
  return count;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  print(numberOfEven(numbers));
}
```

50- Given a list of integers, return true if there exists a subarray (of at least 2 elements) whose sum is a multiple of k.
```dart
bool subarraySum(List<int> numbers, int target) {
  for(int i = 0; i<numbers.length; i++) {
    for(int j = i+1; j<numbers.length; j++) {
      int sum = 0;
      for(int k = i; k<=j; k++) {
        sum += numbers[k];
      }
      if(sum % target == 0) {
        return true;
      }
    }
  }
  return false;
}

void main() {
  List<int> numbers = [23, 2, 4, 6, 7];
  int target = 6;
  print(subarraySum(numbers, target));
}
```

51- Given a number N Print the Summation of its divisors.
```dart
int divisors(int number) {
  int sum = 0;
  for(int i = 1; i <= number; i++) {
    if (number % i == 0) {
      sum += i;
    }
  }
  return sum;
}

void main() {
  int number = 9;
  print(divisors(number));
}
```

52- Given a list of numbers (which may contain duplicates), return the sum of the two largest unique numbers.
```dart
int sumLargestUniqueNumbers(List<int> list) {
  Set<int> uniqueNumbers = list.toSet();
  List<int> sorted = uniqueNumbers.toList()..sort();
  int maxNumber = sorted[sorted.length - 1];
  int secondMaxNumber = sorted[sorted.length - 2];

  if (sorted.length < 2) return -1;

  return maxNumber + secondMaxNumber;
}

void main() {
  List<int> numbers = [1, 2, 3, 4, 8, 5, 6];
  print(sumLargestUniqueNumbers(numbers));
}
```

53- Given a sentence, return the longest word.
```dart
String longestWord(String sentence) {
  String longest = '';
  List<String> words = sentence.split(RegExp(r'[\s.,!?;:]')); // Split by spaces and punctuation
  int maxLength = 0;

  for (String word in words) {
    if (word.isNotEmpty && word.length > maxLength) {
      longest = word;
      maxLength = word.length;
    }
  }
  return longest;
}

void main() {
  String sentence = "Hello world123 567";
  print(longestWord(sentence));
}
```

54- Find the first non-repeating character in a string. If there is no unique character, return -1.
```dart
String uniqueCharacter(String str) {
  Map<String, int> charCount = {};

  // Count the occurrences of each character
  for(int i =0; i <str.length; i++) {
    String char = str[i];
    if(charCount.containsKey(char)){
      charCount[char] = charCount[char]! + 1;
    }else{
      charCount[char] = 1;
    }
  }

  // Find the first unique character
  for(int i =0; i <str.length; i++) {
    String char = str[i];
    if(charCount[char] == 1){
      return char;
    }
  }

    return "-1";
}

void main() {
  String str = "leetcode";
  print(uniqueCharacter(str));
}
```

55- You have N friends, and each of them knows his name and salary. You must sort them in decreasing order according to their salaries and if two of them have the same salary, you must sort them according to their names in a lexicographically increasing order.
```dart
void orderAccordingSalary(List<Map<String, dynamic>> friends) {
  friends.sort((a,b){
    if(a['salary'] == b['salary']) {
      return a['name'].compareTo(b['name']);
    }else{
      return b['salary'].compareTo(a['salary']); //بيرتب الرواتب تنازليًا (من الأكبر للأصغرb>a)
      //return a['salary'].compareTo(b['salary']); //بيرتب الرواتب تصاعديًا (من الأصغر للأكبر)، a<b<c<d
    }
  });
  for(var friend in friends) {
    print("${friend['name']}, ${friend['salary']}");
  }
}

void main() {
  List<Map<String, dynamic>> friends = [
    {"name": "John", "salary": 5000},
    {"name": "Alice", "salary": 7000},
    {"name": "Bob", "salary": 5000},
    {"name": "Charlie", "salary": 6000}
  ];

  orderAccordingSalary(friends);
}
```

56- Given a list of strings, find the first element that does not repeat in the list.
```dart
void firstElementNotRepeat(List<String> list) {
  Map<String, int> countMap = {};

  //عدّ عدد مرات تكرار كل عنصر داخل list وتخزينه في countMap.
  for (String element in list) {
    countMap[element] = (countMap[element] ?? 0) + 1;
  }

  for (String element in list) {
    if (countMap[element] == 1) {
      print(element);
      return ;
    }
  }
  print("All elements repeat.");
}

void main() {
  List<String> list = ["a", "b", "c", "a", "b", "c", "d", "e"];
  firstElementNotRepeat(list);
}
```

57- Write a function to check if a password is strong. A strong password must:

Be at least 8 characters long

Contain at least one uppercase letter

Contain at least one lowercase letter

Contain at least one digit

Contain at least one special character (e.g., !@#\$%^&*)

```dart
void strongPassword(String password) {
      password.contains(RegExp(r'[A-Z]')) &&
      password.contains(RegExp(r'[a-z]')) &&
      password.contains(RegExp(r'[0-9]')) &&
      password.contains(RegExp(r'[!@#\$%^&*]')) &&
      password.length >= 8
      ? print("true") : print("false");
}

void main() {
  String password = "Password123!";
  strongPassword(password);
}
```

58- Given a list of strings, group the strings that are anagrams of each other.
```dart
List<List<String>> groupAnagrams(List<String> words) {
  Map<String, List<String>> map = {};
  for(var word in words) {
    List<String> sorted = word.split('')..sort();
    String key = sorted.join();

    if (map.containsKey(key)) {
      map[key]!.add(word);
    } else {
      map[key] = [word];
    }
  }
  return map.values.toList();
}

void main() {
  List<String> strings = ["eat", "tea", "tan", "ate", "nat", "bat"];
  print(groupAnagrams(strings));
}
```

59- Write a function that takes an integer number of seconds as input and converts it to a string formatted as hours, minutes, and seconds (HH:MM:SS). The requirements are:

Each part (hours, minutes, and seconds) must be represented as a two-digit number (for example, "07:04:09").

The number of hours can exceed 24.
```dart
void formattedTime(int second) {
  int hours = second ~/ 3600;
  int minutes = (second % 3600) ~/ 60;
  int seconds = second % 60;

  String formattedTime = '${hours.toString().padLeft(2, '0')}:${minutes.toString().padLeft(2, '0')}:${seconds.toString().padLeft(2, '0')}';
  print(formattedTime);
}

void main() {
  int second = 3661;
  formattedTime(second);
}
```
