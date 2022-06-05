**时间复杂度是 O(n), 空间复杂度是 O(1), 且是稳定的**

[English](https://github.com/hackware1993/xisort/blob/master/README.md)

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

我很自豪的宣布，这是迄今为止代码执行效率最高的最慢排序算法。

穷尽了各种方法将代码优化到了极致。从中我们可以看出，制度有问题，再怎么优化都无济于事。