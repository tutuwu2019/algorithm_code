# 环  %n


思路来源 leetcode 3379

一个整数数组 nums，按照指定规则生成 相同大小的 result 数组

- i (0 <= i <= nums.size())
- nums[i] > 0 从下标 i 开始，向右移动 nums[i] 步
- nums[i] < 0 从下标 i 开始，向左移动 nums[i] 步
- nums[i] = 0 直接将 nums[i] 赋值给 result[i] 你可以理解为原地踏步


```cpp
// 核心思想

  int index = nums[i] % n;
  int idx (i + index + n) % n;
  ans[i] = nums[idx];

```
