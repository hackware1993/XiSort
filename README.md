**The time complexity is O(n), the space complexity is O(1), and it is stable**

[简体中文](https://github.com/hackware1993/xisort/blob/master/README_CN.md)

Dart code:

```dart
void xiSort(List<int> list) {
  int length = list.length;
  if (length < 2) {
    return;
  }
  int maxIndex = length - 1;
  int maxValue = list[0];
  int minValue = maxValue;
  for (final element in list.skip(1)) {
    if (element > maxValue) {
      maxValue = element;
    }
    if (element < minValue) {
      minValue = element;
    }
  }
  bool isSorted() {
    if (list[0] != minValue || list[maxIndex] != maxValue) {
      return false;
    }
    for (int i = 1, j = length; i < j; i++) {
      if (list[i] < list[i - 1]) {
        return false;
      }
    }
    return true;
  }
  int firstIndex;
  int secondIndex;
  int temp;
  Random random = Random();
  while (!isSorted()) {
    firstIndex = random.nextInt(length);
    secondIndex = random.nextInt(length);
    if (firstIndex != secondIndex) {
      if (list[firstIndex] != list[secondIndex]) {
        temp = list[firstIndex];
        list[firstIndex] = list[secondIndex];
        list[secondIndex] = temp;
      }
    }
  }
}
```

I am proud to announce that this is by far the slowest sorting algorithm with the highest code execution efficiency.

Exhausted various ways to optimize the code to the extreme. From this, we can see that there is a problem with the system, and no matter how to optimize it, it will not help.