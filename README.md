# algorithm
演算法筆記 </br>
需知道:
* 對數
* Big O

## 二元搜尋法
二元搜尋法跟簡易搜尋法差別在於，二元搜尋法可以從中間數字開始猜，每次都會排除一半的數字，簡易搜尋法的話就是一個一個慢慢比對，比如說:1-999，最差情況下我需要執行999次才會得知答案。</br>
所以我們可以得知二元搜尋法是log n 個步驟，簡易搜尋法則是n個步驟。</br>

以下以php code 範例展示:

```php
<?php

function binarySearch($needle, $array) {
  $low = 0;
  $high = count($array) - 1;

  while ($low <= $high) {
    $middle = floor(($low + $high) / 2);

    if ($array[$middle] == $needle) {
      return $middle;
    }

    if ($array[$middle] > $needle) {
      $high = $middle - 1;
    } else {
      $low = $middle + 1;
    }
  }

  return null;
}

$array = [1, 3, 5, 7, 9];
echo binarySearch(3, $array) . "\n";
echo binarySearch(-1, $array) . "\n";
```
---
## 二元搜尋法省下的時間
| 簡易搜尋法        | 二元搜尋法   |
| :-------------: |:-------------:|
| 100個元素 -> 執行100次| 100個元素 -> 執行7次      |
| 40億個元素 -> 執行40億次        | 40億個元素 -> 執行32次      |
| O(n) 線性時間      | O(Log n)對數時間    |

注意！這邊指的時間是指運算次數，而二元法及簡易法的執行時間並不會隨著元素量增加而呈等比增加。
