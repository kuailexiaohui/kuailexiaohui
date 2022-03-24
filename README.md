记录一下数据结构作业
随便写的，为了熟悉引用和一些传值，大佬看了莫笑
#include<iostream>
#include<stdio.h>
#define N 10
#define ok 1
#define error 0
#define overflow -1
using namespace std;
typedef struct {
	int a;
	int b;
}node;
typedef struct{
	node *elem;
	int length;
}sqlist;
int init(sqlist &L){
	L.elem=new node[N];
	if(!L.elem)
	exit(overflow);
	L.length=0;
	return ok;
}
int insert(sqlist &L,int n,node e){
	for(int i=0;i<n;i++)
	{
		scanf("%d %d",&e.a,&e.b);
		L.elem[i]=e;
		L.length++;
	}
}
void print(sqlist L){
	for(int i=0;i<L.length;i++){
		printf("%d %d\n",L.elem[i].a,L.elem[i].b);
	}
}
int del(sqlist &L){
	printf("请输入想要删除的号\n");
	int m;
	scanf("%d",&m);
	for(int i=0;i<L.length;i++){
		if(m==L.elem[i].a)
		{
			L.elem[i]=L.elem[i+1];
			L.length--;
		}
	}
}
void search(sqlist L,int n){
	for(int i=0;i<L.length;i++)
	{
		if(n==L.elem[i].a){
			printf("%d %d\n",L.elem[i].a,L.elem[i].b);
		}
	}
}
void mod(sqlist &L,int n){
	for(int i=0;i<L.length;i++){
		if(n==L.elem[i].a){
			cin>>L.elem[i].a>>L.elem[i].b;
		}
	}
}
int main(){
	sqlist L;
	node e;
	init(L);
	int m;
	printf("输入几个数据\n");
	scanf("%d",&m);
	insert(L,m,e);
	print(L);
	del(L);
	print(L);
	printf("请输入查找的书号\n");
	int a;
	cin>>a;
	search(L,a);
	printf("请输入想修改的书号\n");
	int b;
	cin>>b;
	mod(L,b);
	print(L);
	
}
