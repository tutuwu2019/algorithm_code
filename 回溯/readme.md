# 回溯
> 回溯 常常与递归 强依赖。尤其是涉及”暴力“遍历


核心语义思想
```cpp

current.push_back(xxx);
dfs(candidate, target, index, curretn, ans);
current.pop_back();
```
