# dsa-quicksort
#include<iostream>
using namespace std;


int partition( int arr[], int s, int e) {

    int pivot = arr[s];

    int cnt = 0;
    for(int i = s+1; i<=e; i++) {
        if(arr[i] <=pivot) {
            cnt++;
        }
    }

    
    int pivotIndex = s + cnt;
    swap(arr[pivotIndex], arr[s]);

    
    int i = s, j = e;

    while(i < pivotIndex && j > pivotIndex) {

        while(arr[i] <= pivot) 
        {
            i++;
        }

        while(arr[j] > pivot) {
            j--;
        }

        if(i < pivotIndex && j > pivotIndex) {
            swap(arr[i++], arr[j--]);
        }

    }

    return pivotIndex;

}

void quickSort(int arr[], int s, int e) {

    
    if(s >= e) 
        return ;

    
    int p = partition(arr, s, e);

    
    quickSort(arr, s, p-1);

    
    quickSort(arr, p+1, e);

}

int main() {

   int n;
   cout<<"enter the length of array  : ";
   cin>>n;
   
   int arr[n];
   
   cout<<"enter the elements of array . "<<endl;
   for(int i=0;i<n;i++){
       cout<<"enter "<<i+1<<" : ";
       cin>>arr[i];
   }

    quickSort(arr, 0, n-1);

    for(int i=0; i<n; i++) 
    {
        cout << arr[i] << " ";
    } cout << endl;


    return 0;
}

output:
enter the length of array  : 7
enter the elements of array . 
enter 1 : 4
enter 2 : 2
enter 3 : 1
enter 4 : 4
enter 5 : 5
enter 6 : 4
enter 7 : 6
1 2 4 4 4 5 6 
