#include <stdio.h>

void mergeSort(int a[], int p, int r);
void merge(int a[], int p, int q, int r);
void printArray(int a[], int size);

void mergeSort(int a[], int p, int r)
{
    if (p < r)
    {
        int q = (p + r) / 2;

        mergeSort(a, p, q);
        mergeSort(a, q + 1, r);
        merge(a, p, q, r);
    }
}
void merge(int a[], int p, int q, int r)
{
    int n = r - p + 1;
    int b[n];

    int i = p, j = q + 1, k = 0;

    while (i <= q && j <= r)
    {
        if (a[i] <= a[j])
            b[k++] = a[i++];
        else
            b[k++] = a[j++];
    }

    while (i <= q)
        b[k++] = a[i++];

    while (j <= r)
        b[k++] = a[j++];

    for (i = p, k = 0; i <= r; i++, k++)
        a[i] = b[k];
}

void printArray(int a[], int size)
{
    for (int i = 0; i < size; i++)
        printf("%d ", a[i]);
    printf("\n");
}

int main()
{
    int arr[] = {32, 45, 67, 2, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Given array:\n");
    printArray(arr, n);

    mergeSort(arr, 0, n - 1);

    printf("Sorted array:\n");
    printArray(arr, n);

    return 0;
}




OUTPUT :<img width="1386" height="171" alt="Screenshot 2026-02-05 at 3 15 58 PM" src="https://github.com/user-attachments/assets/5f9a589a-8d53-4e89-a88d-9a65c14318f1" />

