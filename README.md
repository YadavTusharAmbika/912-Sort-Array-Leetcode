Main Function
public int[] sortArray(int[] nums) {
    mergeSort(nums, 0, nums.length - 1);
    return nums;
}


Calls mergeSort on the entire array.

0 → start index

nums.length - 1 → last index

🔁 mergeSort()
public void mergeSort(int[] nums, int s, int e) {


s = start index

e = end index

if (s < e) {


Stop condition.

If only one element left, array is already sorted.

int m = s + (e - s) / 2;


Finds middle index safely (avoids overflow).

mergeSort(nums, s, m);
mergeSort(nums, m + 1, e);


Recursively sorts left half and right half.

merge(nums, s, m, e);


Merges two sorted halves.

🔗 merge()
int n1 = m - s + 1;
int n2 = e - m;


Sizes of left and right sub-arrays.

int[] arr1 = new int[n1];
int[] arr2 = new int[n2];


Temporary arrays to store halves.

arr1[i] = nums[s + i];
arr2[i] = nums[m + 1 + i];


Copies elements from main array into left & right arrays.

int i = 0, j = 0, k = s;

Variable	Purpose
i	Pointer for arr1
j	Pointer for arr2
k	Pointer for nums
while (i < n1 && j < n2) {


Runs until one sub-array is finished.

if (arr1[i] <= arr2[j]) {
    nums[k] = arr1[i];
    i++;
} else {
    nums[k] = arr2[j];
    j++;
}
k++;


Compares both arrays.

Puts smaller element into main array.

Moves pointer.

while (i < n1) {
    nums[k] = arr1[i];
    i++;
    k++;
}


Copies remaining elements of left array.

while (j < n2) {
    nums[k] = arr2[j];
    j++;
    k++;
}


Copies remaining elements of right array.
