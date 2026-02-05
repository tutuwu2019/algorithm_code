# 环  %n


思路来源 leetcode 3379

一个整数数组 nums，按照指定规则生成 相同大小的 result 数组

- i (0 <= i <= nums.size())
- nums[i] > 0 从下标 i 开始，向右移动 nums[i] 步
- nums[i] < 0 从下标 i 开始，向左移动 nums[i] 步
- nums[i] = 0 直接将 nums[i] 赋值给 result[i] 你可以理解为原地踏步


```cpp
// 核心思想

  int index = nums[i] % n;    // index 理解为偏移量
  int idx (i + index + n) % n;  // i 理解为起始位置， +n 理解为第二轮
  ans[i] = nums[idx];

```


其实类似的模型思想在很多场景都遇到过，比如 线程名的标识id 通过 std::to_string(i % thread_size)

更多的还有：
| 场景          | 同一模型                          |
| ----------- | ----------------------------- |
| Ring Buffer | `(head + k) % size`           |
| TCP 序号      | `seq % 2^32`                  |
| 时间轮         | `(tick + delay) % wheel_size` |
| 哈希桶         | `hash % bucket_count`         |
| CPU ROB     | `(idx + 1) & mask`（n 为 2^k）   |



