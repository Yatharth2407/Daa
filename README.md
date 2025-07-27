# Daa
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Generate random float data in the range [min, max]
void generateData(float arr[], int n, float min, float max) {
    for (int i = 0; i < n; i++) {
        arr[i] = min + ((float)rand() / RAND_MAX) * (max - min);
    }
}

// Find index of minimum value
int findMin(float arr[], int n) {
    int min = 0;
    for (int i = 1; i < n; i++) {
        if (arr[i] < arr[min]) {
            min = i;
        }
    }
    return min;
}

// Find index of maximum value
int findMax(float arr[], int n) {
    int max = 0;
    for (int i = 1; i < n; i++) {
        if (arr[i] > arr[max]) {
            max = i;
        }
    }
    return max;
}

int main() {
    int n = 100;
    float temperature[n];
    float pressure[n];
    srand((unsigned)time(NULL));  // Seed random generator

    generateData(temperature, n, -20, 50);
    generateData(pressure, n, 950, 1050);

    clock_t start, end;
    double duration;

    // Time to find minimum temperature
    start = clock();
    int minTempIndex = findMin(temperature, n);
    end = clock();
    duration = (double)(end - start) / CLOCKS_PER_SEC;
    printf("Minimum Temperature: %f\n", temperature[minTempIndex]);
    printf("Time taken to find minimum Temperature: %lf seconds\n", duration);

    // Time to find maximum pressure
    start = clock();
    int maxPressIndex = findMax(pressure, n);
    end = clock();
    duration = (double)(end - start) / CLOCKS_PER_SEC;
    printf("Maximum Pressure: %f\n", pressure[maxPressIndex]);
    printf("Time taken to find maximum Pressure: %lf seconds\n", duration);

    return 0;
}
