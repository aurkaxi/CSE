```c
#include <stdio.h>

int find_min_max(int array[], int size, int min) {
    int mid_index = size / 2;
    int left_array[mid_index];
    int right_array[size - mid_index];

    // build left array
    for (int i = 0; i < mid_index; i++) {
        left_array[i] = array[i];
    }
    // build right array
    for (int i = 0; i < size - mid_index; i++) {
        right_array[i] = array[mid_index + i];
    }

    // get peak values
    int left_val = mid_index > 1 ? find_min_max(left_array, mid_index, min) : left_array[0];
    int right_val = (size - mid_index) > 1 ? find_min_max(right_array, size - mid_index, min) : right_array[0];

    // return min/max
    return min ? (left_val < right_val ? left_val : right_val) : (left_val > right_val ? left_val : right_val);
}

int main(int argc, char const* argv[]) {
    int array[] = {95, 98, 83, 35, 36, 81, 55, 66};
    int size = sizeof(array) / sizeof(int);
    int min = find_min_max(array, size, 1);
    int max = find_min_max(array, size, 0);
    printf("min: %d, max: %d\n", min, max);
    return 0;
}
```
