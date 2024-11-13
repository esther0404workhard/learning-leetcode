209.长度最小的子数组

题目建议： 本题关键在于理解滑动窗口，这个滑动窗口看文字讲解 还挺难理解的，建议大家先看视频讲解。  拓展题目可以先不做。 

题目链接：https://leetcode.cn/problems/minimum-size-subarray-sum/
文章讲解：https://programmercarl.com/0209.%E9%95%BF%E5%BA%A6%E6%9C%80%E5%B0%8F%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84.html
视频讲解：https://www.bilibili.com/video/BV1tZ4y1q7XE

Code: 
```
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int result=INT32_MAX;
        int sum=0; //滑動窗口的和
        int start=0; //窗口開始的位置
        int slideWindowLen=0;
        for(int end=0;end<nums.size();end++){
            sum+=nums[end];
            while(sum>=target){
                slideWindowLen=end-start+1;
                result=result<slideWindowLen?result:slideWindowLen;
                sum-=nums[start++];
            }
        }

        return result<INT32_MAX?result:0;
        
    }
};
```
解題思路：此題就是滑動窗口很經典的題目，透過暴力的雙層迴圈也能解題，但時間複雜度會太大，若用滑動窗口的概念，就能巧妙地降低時間複雜度

59.螺旋矩阵II

题目建议：  本题关键还是在转圈的逻辑，在二分搜索中提到的区间定义，在这里又用上了。 

题目链接：https://leetcode.cn/problems/spiral-matrix-ii/
文章讲解：https://programmercarl.com/0059.%E8%9E%BA%E6%97%8B%E7%9F%A9%E9%98%B5II.html
视频讲解：https://www.bilibili.com/video/BV1SL4y1N7mV/

Ｃode:
```
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n,vector<int>(n,0));
        int startx=0,starty=0; //起點的x,y
        int loop=n/2; //旋轉的圈數
        int offset=1; //轉角處不計算
        int count=1;//給空格數值
        int i,j;
        int mid=n/2;

        while(loop--){
           for(j=starty;j<n-offset;j++){
                res[offset-1][j]=count++;
           }
           for(i=startx;i<n-offset;i++){
                res[i][n-offset]=count++;
           }
           for(;j>starty;j--){
                res[n-offset][j]=count++;
           }
           for(;i>startx;i--){
                res[i][offset-1]=count++;
           }
           startx++;
           starty++;

           offset++;
        }

        if(n%2){
            res[mid][mid]=count;
        }
        
        return res;

        
    }
};
```
思路：建議搭配圖型加上座標輔助，起始位置＆轉角處都要注意








