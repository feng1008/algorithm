#include<iostream>
#include<algorithm>
#include<stack>
using namespace std;

struct ListNode{
	int value;
	ListNode* next;
};

void swap(int &a, int &b){
	int temp=a;
	a=b;
	b=temp;
}

void print_reverse(ListNode* L){
	L=L->next;
	if(!L){
		cout<<"The List is empty!";return;
	}
	ListNode* p=L;
	stack<int> value;
	while(p){
		value.push(p->value);
		p=p->next;
	}
	while(!value.empty()){
		cout<<value.top()<<" ";
		value.pop();
	}
	cout<<endl;
}

void reverse(ListNode* begin,ListNode* end){
	//ListNode* p=begin->next;
	//ListNode* q=p->next;
	//if(!p){return NULL;}
	//if(!q){return begin;}
	//while (p!=end){
	//	 p->next=q->next;
	//	 q->next=begin;
	//	 begin=q;
	//	 q=p->next;
	//}
	//p->next=NULL;
	//return begin;
	while (begin!=end&&begin!=--end){
		swap(begin->value,end->value);
		//end--;
		begin++;
	}
}

void print(ListNode* L){
	ListNode* p=L->next;
	if(!p){
		cout<<"The list is empty"<<endl;return;
	}
	while(p){
		cout<<p->value<<" ";
		p=p->next;
	}
	cout<<endl;
}

 ListNode* create(int* a,int len){
	ListNode* L=(ListNode*)malloc(sizeof(ListNode));
	ListNode* p=L;
	L->next=NULL;
	//int e;
	//while(cin>>e)
	//{
	//	ListNode* s=(ListNode*)malloc(sizeof(ListNode));
	//	s->next=p->next;
	//	p->next=s;
	//	p=p->next;
	//	p->value=e;
	//}
	//for(int i=0;i<10;i++){
	//	ListNode* s=(ListNode*)malloc(sizeof(ListNode));
	//	s->next=p->next;
	//	p->next=s;
	//	p=p->next;
	//	p->value=i+1;
	//}
	for(int i=0;i<len;i++){
		ListNode* s=(ListNode*)malloc(sizeof(ListNode));
		s->next=p->next;
		p->next=s;
		p=p->next;
		p->value=a[i];
	}
	return L;
 }

 ListNode* insert(ListNode* L,int i,int e){
	 ListNode* p=L->next;
	 if(!p) return NULL;
	 int j=0;
	 while(p&&j<i-1){
		 p=p->next;
		 j++;
	 }
	 if(!p||j>i-1) {
		 return NULL;
	 }
	 ListNode* s=(ListNode*)malloc(sizeof(ListNode));
	 s->next=p->next;
	 p->next=s;
	 s->value=e;
	 print(L);
	 return L;
 }

 ListNode* deleteNode(ListNode* L,int i){
	 ListNode* p=L->next;
	 if(!p) return NULL;
	 int j=0;
	 while(p&&j<i-1){
		 p=p->next;
		 j++;
	 }
	 if(!p||j>i-1) return NULL;
	 ListNode* q=p->next;
	 p->next=q->next;
	 free(q);
	 print(L);
	 return L;
 }

 ListNode* findlastk(ListNode* L,int k){
	 if(!L || k<=0 ){
		cout<<"Invalid input!";
		return NULL;
	 }
	 ListNode* p=L->next;
	 for(int i=0;i<k-1;i++){
		 if(p->next !=NULL){
			 p=p->next;
		 }
		 else{
			 cout<<"Invalid input!";
			 return NULL;
		 }
	 }
	 p=p->next;
	 ListNode* q=L->next;
	 while(p){
		 p=p->next;
		 q=q->next;
	 }
	 cout<<q->value<<endl;
	 return q;
 }

 ListNode* reverseList(ListNode* L){
	 ListNode* p=L->next;
	 ListNode* q=L->next->next;
	 if(!p){
		 cout<<"Invalid input!"<<endl;
		 return L;
	 }
	 while(q){
		 p->next=q->next;
		 q->next=L->next;
		 L->next=q;
		 q=p->next;
	 }
	 p->next=NULL;

	 print(L);
	 return L;
 }

 ListNode* mergeList(ListNode* La,ListNode* Lb){
	 ListNode* p=La->next;
	 ListNode* q=Lb->next;
	 if(!q){
		 return La;
	 }
	 else if(!p){
		 return Lb;
	 }
	 while(p&&q){
		 if(p->value<q->value){
			 ListNode* temp_p=p->next;
			 p->next=q;
			 p=temp_p;
		 }
		 else{
			 ListNode* temp_q=q->next;
			 q->next=p;
			 q=temp_q;
		 }
	 }
	 return La->next<Lb->next?La:Lb;
 }

 ListNode* findFirstCommonNode(ListNode* La,ListNode* Lb){
	int a_len=0,b_len=0;
	ListNode* p=La->next;
	ListNode* q=Lb->next;
	if(!p||!q){
		cout<<"Invalid input!";return NULL;
	}
	while(p){
		a_len++;p=p->next;
	}
	while(q){
		b_len++;q=q->next;
	}
	int dif_len=a_len-b_len;
	for(int i=0;i<abs(dif_len);i++){
		if(dif_len>0){
			p=p->next;
		}
		else{
			q=q->next;
		}
	}
	while(p&&q&&p!=q){
		p=p->next;
		q=q->next;
	}
	ListNode* L=p;
	return L;
 }

//2.2.3
ListNode* partionList(ListNode* L,int x){
	return NULL;
}

//2.2.6
ListNode* rotateListk(ListNode* L,int k,int length){
	if(!L||k<1||k>length){
		cout<<"Invalid input!";
		return NULL;
	}
	ListNode* p=L->next;
	int i=0;
	while(p&&i<k-1){
		p=p->next;
		i++;
	}
	ListNode* q=p->next;
	ListNode* temp=p;
	if(!p){
		cout<<"Invalid input!";
		return NULL;
	}
	while(q){
		q=q->next;
		p=p->next;
	}
	p->next=L->next;
	L->next=temp->next;
	temp->next=NULL;
	print(L);
	return L;
}

//2.2.8
ListNode* swampNodeInPairs(ListNode* L){
	if(!L){
		cout<<"Invalid input";return NULL;
	}
	ListNode* p=L->next;
	ListNode* q=p->next;
	ListNode* k=L;
	while(q){
		p->next=q->next;
		q->next=p;
		k->next=q;
		k=p;
		p=p->next;
		q=p->next;
	}
	print(L);
	return L;
}

//2.2.13
ListNode* reorderList(ListNode* L){
	ListNode* p=L->next;
	ListNode* q=p;ListNode* r=p->next;
	if(!p){
		cout<<"Invalid input!"<<endl;return 0;
	}
	if(!r){
		print(L);
		return L;
	}
	while(r&&r->next){
		p=p->next->next;
		r=p->next;
		q=q->next;
	}
//	q=q->next;r=q;
//	while(r){
//		r=r->next;
//	}
	r=reverseList(q);
	q=r->next;
	r->next=NULL;
	p=L->next;
	while(q){
		r=q->next;
		q->next=p->next;
		p->next=q;
		p=q->next;
		q=r;
	}

	print(L);
	return L;
}

int main(int argc,char* argv){
//	ListNode list;
//	ListNode* L;
//	L=create(&list);
	//int a[]={1,2,3,4,5,6,7,8,9,10};
	//int len=sizeof(a)/sizeof(int);
	//L=create(a,len);
	//int a[]={1,3,6,8,9,12,16,25,34,38,42};
	//int b[]={2,10,14,19,23,28,31,39,45,49};
	//int a_len=sizeof(a)/sizeof(int);
	//int b_len=sizeof(b)/sizeof(int);
	//ListNode* La=create(a,a_len);
	//ListNode* Lb=create(b,b_len);
	//ListNode* L=mergeList(La,Lb);
//	int a[]={2,10,14,19,23,28,31,39,45,49};
	int a[]={2};
	int a_len=sizeof(a)/sizeof(int);
	ListNode* L=create(a,a_len);
	reverseList(L);
//	int k=4;
//	rotateListk(L,k,a_len);	
//	reorderList(L);
//	swampNodeInPairs(L);
	system("pause");
	return 0;
}
