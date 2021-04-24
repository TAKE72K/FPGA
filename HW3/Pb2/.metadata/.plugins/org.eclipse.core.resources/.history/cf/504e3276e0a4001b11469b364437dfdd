#include "xparameters.h"
#include "xgpio.h"
#include "xil_printf.h"
#include <iostream>


using namespace std;



#define SW_DEVICE_ID  XPAR_GPIO_0_DEVICE_ID
XGpio SW_Gpio;
void Merge_Sort(int A[],int p,int q);
void Merge(int A[], int p, int q, int m);

int main()
{
	int SW_Status;
	SW_Status = XGpio_Initialize(&SW_Gpio, SW_DEVICE_ID);
	XGpio_SetDataDirection(&SW_Gpio, 1, 0x0f);
	u32 sw_data;
    int a[10];
    while(true){
        for(int i=0;i<10;i++){
            cin>>a[i];
        }
        Merge_Sort(a,0,9);
		sw_data = XGpio_DiscreteRead(&SW_Gpio, 1);
		if(sw_data==0){
			for(int i=0;i<10;i++){
				cout<<a[i]<<" ";
			}
		}
		else{
			for(int i=9;i>=9;i--){
				cout<<a[i]<<" ";
		}
        cout<<"\n";
    }
    return 0;
}
void Merge_Sort(int A[], int p, int q) {
	if (p < q) {
		int m = (p + q) / 2;
		Merge_Sort(A, p, m);  
		Merge_Sort(A, m + 1, q); 
		Merge(A, p, q, m);  
	}
}
void Merge(int A[], int p, int q, int m) {
	int n1 = m - p + 1;
	int n2 = q - m;
	int* L = new int[n1];
	int* R = new int[n2];

	for (int i = 0; i < n1; i++) {
		L[i] = A[p+i]; 
	}
	for (int i = 0; i < n2; i++) {
		R[i] = A[i+m+1]; 
	}
	L[n1] = 2147483647;
	R[n2] = 2147483647;
	int i = 0, j = 0;
	for (int k = p; k <= q; k++) {
		if (L[i] <= R[j]) {
			A[k] = L[i];
			i++;
		}
		else {
			A[k] = R[j];
			j++;
		}
	}
}
