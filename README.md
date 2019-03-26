# Revisi EZTR

## Source Code

' ' ' c

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

' ' '
