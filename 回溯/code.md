# code 



### leetcode 39 组合总和


```cpp

void dfsd(vector<int> candidate, int target, int start, vector<int>& current, vector<vector<int>>& result){
  if(target == 0){
    result.push_back(current);
    return;
  }

  for(int i = start; i < candidate.size(); i++){
    if(candidate[i] > target){
      break;
    }
    current.push_back(candidate[i]);
    dfs(candidate, target - candidate[i], i, current, result);
    current.pop_back();
  }
  return;
} 

vector<vector<int>> combinationSum(vector<int>& candidate, int target){

  vector<vector<int>> ans;
  vector<int> current;
  sort(candidate.begin(), candidate.end());

  dfs(candidate, target, 0, current, ans);

  return ans;

}


```

### 40 组合总和II

要求每个元素只能在每个组合中出现一次

- 那么每轮新的回溯 idex 需要更新为 -> index + 1
>  由原来的  index1 index1 index1    ->  index1 index2 index3
- 可能处出现
```cpp

void dfsd(vector<int> candidate, int target, int start, vector<int>& current, vector<vector<int>>& result){
  if(target == 0){
    result.push_back(current);
    return;
  }

  for(int i = start; i < candidate.size(); i++){
    if(candidate[i] > target){
      break;
    }
    // 可能会存下多个相同值，然后使用多次比如 1 1 2  -> [index1, index3]、[index2, index3]
    if(i > start && candidate[i] == candidate[i - 1]) continue;
    current.push_back(candidate[i]);
    // [10,1,2,7,6,1,5]  这里避免一直使用通过一个值
    dfs(candidate, target - candidate[i], i + 1, current, result);
    current.pop_back();
  }
  return;
} 

vector<vector<int>> combinationSum(vector<int>& candidate, int target){

  vector<vector<int>> ans;
  vector<int> current;
  sort(candidate.begin(), candidate.end());

  dfs(candidate, target, 0, current, ans);

  return ans;

}

```

```
###################
正确的与错误的例子对比参考

root (target=3, start=0)
│
├─ 选 index0 (1) → current=[1], target=2, start=1
│   │
│   ├─ 选 index1 (1) → current=[1,1], target=1, start=2
│   │   └─ 选 index2 (2) → 2>1 break → 无解
│   │
│   └─ 选 index2 (2) → current=[1,2], target=0 → ✓ 记录 [1,2]
│
└─ 选 index1 (1) → current=[1], target=2, start=2   (注意：这是另一条分支，选的是第二个1)
    │
    └─ 选 index2 (2) → current=[1,2], target=0 → ✓ 记录 [1,2]   ← 重复记录！


---------------------------------------------------------------------------------------------------

root (target=3, start=0)
│
├─ i=0 (1) → 可以选（i == start，不跳过）
│   │  current=[1], target=2, start=1
│   │
│   ├─ i=1 (1) → i>start且cand[1]==cand[0] → 跳过！不选第二个1
│   │
│   └─ i=2 (2) → 选 → current=[1,2], target=0 → ✓ 记录 [1,2]
│
└─ i=1 (1) → i>start且cand[1]==cand[0] → 跳过！整个分支被剪掉

```
