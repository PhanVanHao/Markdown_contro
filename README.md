# Con trỏ
##1.Các Khái niệm
###-Địa chỉ 
Dựa vào kiểu dữ liệu khi khai báo biến máy sẽ cấp phát cho biến một địa chỉ để lưu trữ biến đó trên vùng nhớ. Mỗi biến có kiểu khác nhau thì được lưu vào các địa chỉ khác nhau
###-Con trỏ
Con trỏ là một biến dùng để chứa địa chỉ. Mỗi loại địa chỉ thì có loại con trỏ tương ứng. Trước khi sử dụng biến con trỏ ta phải khai báo trước khi sử dụng
####Khai báo:	
```
<kiểu_DL> * <tên_biến_con_trỏ>;
```
VD1:		
```
int x, y, *p, *c;
```
	x, y là hai biến kiểu nguyên, p, c là hai biến con trỏ kiểu nguyên
 VD2:		
 ```
 float *t, *d ;
 ```
	//Khai báo biến con trỏ t và d có kiểu thực
Biến con trỏ được dùng  theo hai trường hợp sau:
Tên con trỏ chỉ đến địa chỉ của biến được lưu trong con trỏ: 
```
    float a,*p,*q;
		p=&a; /* lưu địa chỉ của biến a vào con trỏ p */
		q= p; /* lưu địa chỉ trong p vào con trỏ q*/ 
```
Dạng khai báo của con trỏ chỉ đến giá trị lưu tại vùng nhớ mà con trỏ trỏ tới. 
	VD:	 
```
float x=5, y , z=20, *px, *pz;,*py;
		px=& x; /* khi đó *px = x =5*/
		pz=&z; /* *pz=z=20*/
	khi đó ba biểu thức sau là tương đương:
	y=3*x+z;		*py=3*x+z;		*py=3*(*px)+*pz;
```
##Con trỏ và mảng nhiều chiều
 Các phần tử của mảng có thể được xác định thông qua con trỏ. Ta có khai báo :	float a[10];	
		//Khai báo mảng gồm 10 phần tử kiểu thực
	Ta có tên mảng chính là một hằng địa chỉ trỏ tới địa chỉ phần tử đầu tiên của mảng và 
		a 	tương đương với    &a[0]
		a+i 	tương đương với    &a[i]
		*(a+i) tương đương với 	a[i]
Các cách viết a[i], *(a+i), *(p+i), p[i] là tương đương nhau
VD: Nhập từ bàn phím các phần tử của mảng và tính tổng các phần tử đó

```
#include<stdio.h>
#include<stdio.h>
void main()
{		float a[5], s ; int i;
		for(i=0;i<5;i++) {
			printf(“\na[%d]= ”,i); scanf(“%f”,&a[i]); }
		s=0;
	for (i=0;i<5;i++)		s+=a[i];
	printf(“\n Tong =%8.2f”,s);
	getch();
}
```
Phép toán lấy địa chỉ nói chung không dùng được đối với các thành phần của mảng nhiều chiều (trừ trường hợp mảng hai chiều các số nguyên). 
	Ðể tính toán địa chỉ của thành phần a[i][j] chúng ta sử dụng công thức sau :
			(float *)a+i*n+j. 
	a là một hằng con trỏ trỏ đến các dòng của một ma trân hai chiều, vì vậy
		a trỏ đến dòng thứ nhất
		a+1 trỏ đến dòng thứ hai
		a+2 trỏ đến dòng thứ ba

Ðể tính toán được địa chỉ của phần tử ở dòng i cột j chúng ta phải dùng phép chuyển đổi kiểu bắt buộc đối với a: (float * )a 
	a là con trỏ trỏ đến thành phần a[0][0] của ma trận.
	a[i][j] sẽ có địa chỉ là (float *a) +i*n+j
	Xét VD nhập giá trị của ma trận hai chiều: Tro2


###Phân loại con trỏ
Con trỏ kiểu int dùng để chứa địa chỉ các biến kiểu int. Tương tự ta có con trỏ kiểu float,
kiểu double vv.

```
#include <stdio.h>
#include <stdio.h>
void main()
{		float a[10][20];	int i,j,n;
		printf("Nhap vao kich thuoc ma tran n=");
		scanf("%n",&n); 
	for(i=0;i<n;i++)
		for(j=0;j<n;j++)
	{	printf("a[%d][%d] = ",i,j);
		scanf("%f",(float *)a+i*20+j);
		}
	getch();
}
```
###Phép toán trên con trỏ
#####Phép gán: chỉ nên thực hiện trên các con trỏ có cùng kiểu, khi thực hiện trên con trỏ phải thực hiện phép ép kiểu:
	Vd: 
```
int x;
		char *p;
		p=(char*)(&x);
```
#####Phép tăng giảm địa chỉ
	VD:
```
float x[30], *px;
	px=&x[10];// p là con trỏ thực trỏ tới phần tử x[10]
		px+i trỏ tới phần tử x[10+i]
		px – i trỏ tới phần tử x[10-i]
```
Phép gán: chỉ nên thực hiện trên các con trỏ có cùng kiểu, khi thực hiện trên con trỏ phải thực hiện phép ép kiểu:
	Vd: 
```
int x;
		char *p;
		p=(char*)(&x);
```
Phép tăng giảm địa chỉ
	VD: 
```  
float x[30], *px; 

```
	
  px=&x[10];// p là con trỏ thực trỏ tới phần tử x[10]
		px+i trỏ tới phần tử x[10+i]
		px – i trỏ tới phần tử x[10-i]

###Mảng con trỏ

Mảng con trỏ là một mảng mà mỗi phẩn tử của nó có thể chứa một địa chỉ nào đó. Mảng con trỏ có nhiều kiểu, mỗi phẩn tử của mảng kiểu nào thì sẽ chứa địa chỉ kiểu tương ứng với nó. Mảng con trỏ được khai báo theo mẫu sau:


```
<kiểu Dl> *<tênmảng>[N]
```
Khi gặp khai báo mảng con trỏ thì máy sẽ cấp phát N khoảng nhớ liên tiếp cho N phần tử tương ứng trong mảng
Chú ý: Mảng con trỏ không dùng để lưu số liệu, trước khi sử dụng mảng con trỏ cần gán cho mỗi phần tử một giá trị là địa chỉ của một biến hoặc của một phần tử trong mảng




