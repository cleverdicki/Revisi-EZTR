# Revisi EZTR

## Source Code

```c

#include<stdio.h>
#include<stdlib.h>
#define max 100001

struct test{
	char stack[max];
	int top;
}data;

void push(char ch){
	if(data.top==(max-1)) printf("Stack is full\n");
	else{
		data.top++;
		data.stack[data.top]=ch;
	}
}

void pop(){
	data.top--;
}

int main()
{
	data.top=-1;
	int i=0;
	char chr[max];
	scanf("%s",chr);
	while(chr[i]!='\0'){
		if(chr[i]=='(' || chr[i]=='{' || chr[i]=='['){
			push(chr[i]);
		}
		else if(chr[i]==')' || chr[i]=='}' || chr[i]==']'){
			if(chr[i]==')'){
				if(data.stack[data.top]=='(') pop();
				else{
					printf("v:\n");
					return 0;;
				}
			}
			if(chr[i]=='}'){
				if(data.stack[data.top]=='{') pop();
				else{
					printf("v:\n");
					return 0;
				}
			}
			if(chr[i]==']'){
				if(data.stack[data.top]=='[') pop();
				else{
					printf("v:\n");
					return 0;
				}
			}
		}
		i++;
	}
	if(data.top==-1) printf(":v\n");
	else printf("v:\n");
	
	return 0;
}

```
Pada program ini, dilakukan pengecekan bracket dengan stack array dimana kondisinya jika pada inputan terdapat tanda bracket, maka tanda bracket tersebut akan dipush ke dalam stack, sedangkan jika terdapat operand maupun operator akan diabaikan. Hal ini karena pada problem yang diberikan hanya diperintahkan untuk menentukan apakah kalimat matematika yang diinputkan dapat dioperasikan atau tidak. Penentuannya dilakukan berdasarkan tanda bracket yang diinputkan. Syarat kalimat matematika yang dapat dioperasikan adalah jika tanda bracket yang diinputkan memenuhi syarat pengoperasian kalimat matematika. Bracket yang diinputkan yaitu "()", "{}", dan "[]".

#### Inisialisasi dan Pendeklarasian Struct
Bagian ini merupakan inisialisasi program berupa header dan konstanta daripada ```max```. Kemudian, terdapat juga pendeklarasian struct. ```max``` akan menjadi constraint daripada stack yang dapat diiputkan. ```stack[]``` akan menjadi tempat untuk menampung stack bracket yang di push. ```top``` akan menjadi penanda top pada stack. dan ```data``` akan menjadi variabel penanda struct.
```c
#include<stdio.h>
#include<stdlib.h>
#define max 100001

struct test{
	char stack[max];
	int top;
}data;

```

#### Fungsi Push
Bagian ini untuk push stack ketika terdapat tanda bracket pada inputan. Dicek apakah isi stack full atau tidak. Jika penuh maka akan print output ```Stack is full```. Jika tidak full, maka bracket akan di push ke dalam stack. nilai top akan bertambah satu dan bracket akan di push ke dalam stack.
```c
void push(char ch){
	if(data.top==(max-1)) printf("Stack is full\n");
	else{
		data.top++;
		data.stack[data.top]=ch;
	}
}
```

#### Fungsi POP
Bagian ini untuk pop tanda bracket yang ada pada stack. yang dilakukan adalah hanya mengurangi nilai top tanpa mengambil nilai dari stcak yang di pop.
```c
void pop(){
	data.top--;
}
```

#### Main Program
Bagian ini merupakan main program dimana program akan dijalankan. terdapat pendeklarasian niali variabel top=-1 dan pendeklarasian variabel untuk input data. Looping akan terus berlanjut hingga data yang diinputkan. Jika terdapat inputan bracket "(", "{", atau "[", maka akan dipush kedalam stack.
```c
while(chr[i]!='\0'){
	if(chr[i]=='(' || chr[i]=='{' || chr[i]=='['){
		push(chr[i]);
	}
```
Jika terdapat inputan bracket ")", "}", atau "]", maka akan dicek terlebih dahulu stack top. Jika pada stack top berisi pasangan dari tanda buka bracket yang diinputkan, maka tanda buka bracket tersebut akan di pop. Namun jika tidak, akan langsung diprint output ```v:``` yang menandakan bahwa kalimat matematika tidak dapat dioperasikan, dan kemudian program langsung berhenti. Kondisi ini berlaku untuk semua tanda bracket. Kemudian, ```i``` akan bertambah satu setiap looping untuk menandakan nilai stacknya.
```c
else if(chr[i]==')' || chr[i]=='}' || chr[i]==']'){
		if(chr[i]==')'){
			if(data.stack[data.top]=='(') pop();
			else{
				printf("v:\n");
				return 0;;
			}
		}
		if(chr[i]=='}'){
			if(data.stack[data.top]=='{') pop();
			else{
				printf("v:\n");
				return 0;
			}
		}
		if(chr[i]==']'){
			if(data.stack[data.top]=='[') pop();
			else{
				printf("v:\n");
				return 0;
			}
		}
	}
	i++;
}
```
Terakhir, akan dicek data pada stack. Setelah proses pengecekan bracket selesai dan tidak berhenti di tengah pengecekan (tidak salah pada inputan), akan dicek isi stack. Jika stack masih berisi data, maka kalimat matematika tersebut tidak dapat dioperasikan yang ditandai dengan output ```v:```. Jika pada stack tidak bersisa data bracket, maka kalimat matematika tersebut dapat dioperasikan yang ditandai dengan output ```:v```.
```c
if(data.top==-1) printf(":v\n");
	else printf("v:\n");
	
	return 0;
}
```
