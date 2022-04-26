数组中的第K个最大的元素

思路：可以使用快排算法来寻找第K个最大元素，先选择数组[l, r]中的一个基准值ref，通过随机种子可以找到一个随机下标，然后利用这个基准值ref来对[l, r]之间的数组进行划分，使得ref左边的值大于ref，ref的右边小于ref。之后判断ref对应的下标ref_index是否是下标K，如果是，直接返回nums[ref_index]，否则判断ref_index是在[l, ref_index - 1]还是在[ref_index + 1, r]，随后在相应的范围进行快排递归。

```C++
class Solution {
public:
    static bool cmp(int a, int b){
        return a > b;
    }
    /*//超出时间限制
    void quickSort(vector<int>& nums, int left, int right, int k){
        if(left >= right || right < k || left > k){
            return;
        }
        int temp = nums[left];
        int start = left;
        int end = right;
        while(left < right){
            while(nums[right] < temp && left < right){
                --right;
            }
            while(nums[left] > temp && left < right){
                ++left;
            }
            swap(nums[left], nums[right]);   
        }
        if(right == k){
            return ;
        }
        quickSort(nums, start, right - 1, k);
        quickSort(nums, right + 1, end, k);
    }*/
    int quicksort(vector<int>& nums, int l, int r, int index){

        int ref_index = random(nums, l, r, index);
        if(ref_index == index){
            return nums[index];
        }
        return (ref_index > index) ? quicksort(nums, l, ref_index - 1, index) : quicksort(nums, ref_index + 1, r, index);
    }
    //获取随机的基准值
    int random(vector<int>& nums, int l, int r, int index){
        int ind_rand = rand() % (r - l + 1) + l;%l是起始值，r是终止值，r - l + 1是整数的范围
        swap(nums[ind_rand], nums[r]);
        return partition(nums, l, r, index);
    }
    //
    int partition(vector<int>& nums, int l, int r, int index){
        int ref = nums[r];
        int j = l - 1;//用于记录大于基准值ref的下标
        for(int i = l; i < r; ++i){
            if(nums[i] > ref){
                swap(nums[++j], nums[i]);
            }
        }
        //将基准值放入[l, r]之间，左边为大于ref的，右边为小于ref的
        swap(nums[j + 1], nums[r]);
        return j + 1;
    }
    int findKthLargest(vector<int>& nums, int k) {
        //sort(nums.begin(), nums.end(), cmp);
        //return nums[k - 1];
        //快排
        srand(time(0));
        return quicksort(nums, 0, nums.size() - 1, k - 1);
    }
};
```

