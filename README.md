# Exponential-search
#include <iostream>
#include <algorithm>
using namespace std;

int binarySearch(int arr[], int left, int right, int x) {
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == x) return mid;
        else if (arr[mid] < x) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

int exponentialSearch(int arr[], int n, int x) {
    if (arr[0] == x) return 0;
    int i = 1;
    while (i < n && arr[i] <= x)
        i *= 2;
    return binarySearch(arr, i/2, min(i, n-1), x);
}

int main() {
    int arr[] = {2, 4, 8, 16, 32, 64, 128};
    int n = sizeof(arr)/sizeof(arr[0]);
    int x = 32;
    int result = exponentialSearch(arr, n, x);
    if (result != -1)
        cout << "Element found at index " << result << endl;
    else
        cout << "Element not found" << endl;
    return 0;
}
