# Dart Practice Problems

1- Write a function that takes a list of integers (List<int>) and returns the sum of the even numbers only.
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
