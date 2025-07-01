#include <iostream>
#include <algorithm>  // For sort()
using namespace std;
int binarySearch(int arr[], int left, int right, int target) {
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    } return -1;
}
int exponentialSearch(int arr[], int size, int target) {
    if (arr[0] == target)
        return 0;
    int i = 1;
    while (i < size && arr[i] <= target)
        i *= 2;
    return binarySearch(arr, i / 2, min(i, size - 1), target);
}
int main() {
    int arr[] = {3, 10, 20, 40, 45, 60, 70, 80, 90};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 45;
    sort(arr, arr + size);
    cout << "Sorted array: ";
    for (int i = 0; i < size; ++i)
    cout << arr[i] << " ";
    cout << endl;
    int result = exponentialSearch(arr, size, target);
    if (result != -1)
        cout << "Element " << target << " found at index " << result << "." << endl;
    else
        cout << "Element " << target << " not found in the array." << endl;
    return 0;
}
