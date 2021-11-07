### Array Rotation

Time Complexity - O(n)
Space Complexity - O(1)


- [LeetCode Problem](https://leetcode.com/problems/rotate-array/)
- [Where I studied the solution](https://youtu.be/8-jkYi6kmSQ)


Code in C++:
```C++
	void swap(int *x, int *y){
        int temp = *x;
        *x = *y;
        *y = temp;
    }
    

    // Example:
 	// Input: nums = [1,2,3,4,5,6,7], k = 3
	// Output: [5,6,7,1,2,3,4]

    // nums is the array to be rotated
    // k is the number of clockwise rotations to be performed on the array
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;
        int front = n - k, rear = n - 1;
        while(front < rear){
            swap(&nums[front++], &nums[rear--]);
        }
        
        front = 0;
        rear = n - k - 1;
        while(front < rear){
            swap(&nums[front++], &nums[rear--]);
        }
        front = 0; 
        rear = n - 1;
        while(front < rear){
            swap(&nums[front++], &nums[rear--]);
        }
    }

```