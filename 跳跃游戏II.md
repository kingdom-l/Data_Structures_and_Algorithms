跳跃游戏II

思路：在每次跳跃时取上次覆盖范围内中最大的跳跃范围，那么什么时候跳跃呢？在到达上次跳跃范围的终点时进行跳跃。

```c++
class Solution {
public:
    int jump(vector<int>& nums) {
        int maxstep = 0;//记录本次最大覆盖范围
        int end = 0;//记录上次覆盖范围的终点
        int step = 0;//记录步数
        for(int i = 0; i < nums.size() - 1; ++i){
            if(i <= maxstep){
                maxstep = max(maxstep, nums[i] + i);//更新本次最大覆盖范围
                if(i == end){//如果到达上次覆盖范围的终点时，更新覆盖范围,同时步数加1
                    end = maxstep;
                    ++step;
                }
            }
        }
        return step;
    }
};
```

