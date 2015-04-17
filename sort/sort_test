#include<iostream>
#include<ctime>
using namespace std;
const int N=100;
int a[N];

//打印数组
template<class T>
void print(T a[],int n){
	for(int i=0;i<n;i++){
		cout<<a[i]<<" ";
	}
	cout<<endl;
}

//随机初始化N个数
template<class T>
void init(T a[],int n){
	srand((unsigned)time(NULL));
	for(int i=0;i<n;i++){
		a[i]=rand()%1000;
	}
	cout<<"原数组为："<<endl;
	print(a,n);
}

//交换两个数的值
template<class T>
void Swap(T& a,T& b){
	T temp=a;
	a=b;
	b=temp;
}

//直接插入排序
template<class T>
void insert_sort(T a[],int n){
	for(int i=0;i<n;i++){
		for(int j=i;j>0&&a[j]<a[j-1];j--){
			Swap(a[j],a[j-1]);
		}
	}
	print(a,n);
}

//折半插入排序-二分查找
template<class T>
int binary_search(T a[],int low,int high,T target){
	while(low<=high){
		int mid=(low+high)>>1;
		if(a[mid]==target){
			return mid;
		}
		else if(a[mid]<target){
			low=mid+1;
		}
		else{
			high=mid-1;
		}
	}
	return low;
}

//折半插入排序
template<class T>
void bin_insert_sort(T a[],int n){
	for(int i=1;i<n;i++){
		int index=binary_search(a,0,i-1,a[i]);
		if(i!=index){
			T temp=a[i];
			for(int j=i;j>=index;j--){
				a[j]=a[j-1];
			}
			a[index]=temp;
		}
	}
	print(a,n);
}

//冒泡排序
template<class T>
void buddle_sort(T a[],int n){
	for(int i=0;i<n-1;i++){
		bool issorted=true;
		for(int j=0;j<n-1-i;j++){
			if(a[j+1]<a[j]){
				issorted=false;
				Swap(a[j],a[j+1]);
			}
		}
		if(issorted) break;
	}
	print(a,n);
}

//快速排序-寻找插入点
template<class T>
int partion(T a[],int low,int high){
	T temp=a[low];
	int i=low,j=high;
	while(i<j){
		while((temp<=a[j])&&(i<j)){
			j--;
		}
		a[i]=a[j];
		while((a[i]<=temp)&&(i<j)){
			i++;
		}
		a[j]=a[i];
	}
	a[i]=temp;
	return i;
}

//快速排序
template<class T>
void quick_sort(T a[],int low,int high){
	if(low<high){
		int index=partion(a,low,high);
		quick_sort(a,low,index-1);
		quick_sort(a,index+1,high);
	}
}

//选择排序
template<class T>
void select_sort(T a[],int n){
	for(int i=0;i<n-1;i++){
		int min_index=i;
		for(int j=i+1;j<n;j++){
			if(a[j]<a[min_index]){
				min_index=j;
			}
		}
		if(i!=min_index){
			Swap(a[i],a[min_index]);
		}
	}
	print(a,n);
}

//数组部分直接插入排序，希尔排序将用到
//template<class T>
//void line_sort(T a[],int low,int high){
//	for(int i=low;i<=high;i++){
//		for(int j=i;j>low&&a[j]<a[j-1];j--){
//			Swap(a[j],a[j-1]);
//		}
//	}
//}

//希尔排序
template<class T>
void shell_sort(T a[],int step[],int n,int m){
	if(step[m-1]!=1){
		cout<<"shell排序增量数组不正确!"<<endl;
		return;
	}
	for(int i=0;i<m;i++){
		for(int j=step[i];j<n;j++){
			for(int k=j-step[i];k>=0&&(a[k+step[i]]<a[k]);k-=step[i]){
				Swap(a[k],a[k+step[i]]);
			}
		}
	}
	print(a,n);
}

//堆排序-堆调整
template<class T>
void heap_adjust(T a[],int i,int n){
	int nchild;
	for(;2*i+1<n;i=nchild){
		nchild=2*i+1;
		if((nchild<n-1)&&(a[nchild]<a[nchild+1])){
			nchild++;
		}
		if(a[i]<a[nchild]){
			Swap(a[i],a[nchild]);
		}
		else{
			break;
		}
	}
}

//堆排序
template<class T>
void heap_sort(T a[],int n){
	for(int i=n/2-1;i>=0;i--){
		heap_adjust(a,i,n);
	}
	for(int i=n-1;i>0;i--){
		Swap(a[0],a[i]);
		heap_adjust(a,0,i);
	}
	print(a,n);
}

//归并排序-合并两个有序数组
template<class T>
void merge(T a[],T b[],int low,int mid,int high){
	if(!a||!b){
		cout<<"Error input!"<<endl;return;
	}
	int i=low,j=mid+1,k=0;
	while((i<mid+1)&&(j<=high)){
		if(a[i]<a[j]){
			b[k++]=a[i++];
		}
		else{
			b[k++]=a[j++];
		}
	}
	while(i<mid+1){
		b[k++]=a[i++];
	}
	while(j<high+1){
		b[k++]=a[j++];
	}
	for(int i=0;i<k;i++){
		a[low+i]=b[i];
	}
}

//归并排序
template<class T>
void merge_sort(T a[],T temp[],int low,int high){
	if(low<high){
		int mid=(low+high)>>1;
		merge_sort(a,temp,low,mid);
		merge_sort(a,temp,mid+1,high);
		merge(a,temp,low,mid,high);
	}
}

//基数排序-获取每个位上数字
template<class T>
int getNNumber(T a,int n){
	for(int i=0;i<n;i++){
		a=a/10;
	}
	return a%10;
}

//基数排序
template<class T>
void radix_sort(T a[],int n){
	int ra[N]={0};
	for(int i=0;i<N;i++){
		ra[i]=a[i];
	}
	for(int i=0;i<3;i++){                 //测试数据范围为0~99
		int j;
		for(j=0;j<n;j++){
			ra[j]=getNNumber(a[j],i);
		}
		for(j=0;j<n;j++){
			for(int k=j;k>0&&ra[k]<ra[k-1];k--){
				Swap(a[k],a[k-1]);
				Swap(ra[k],ra[k-1]);
			}
		}
	}
	print(a,n);
}

//验证排序是否成功
template<class T>
void verify(T a[],int n){
	bool result=true;
	for(int i=0;i<n-1;i++){
		if(a[i+1]<a[i]){
			result=false;break;
		}
	}
	if(result){
		cout<<"数组成功排序!"<<endl;
	}
	else{
		cout<<"数组未成功排序!"<<endl;
	}
}

//显示选择界面
void showface(){
    system("cls");         
    cout<<"                  **********排序算法**********      \n";
    cout<<".....................(本系统按从小到大排序).....................\n";
    cout<<"................................................................\n";
    cout<<"         1:直接插入排序                   2:折半插入排序\n";
	cout<<"         3:冒泡排序                       4:快速排序    \n";
	cout<<"         5:选择排序                       6:希尔排序\n";
	cout<<"         7:堆排序                         8:归并排序    \n"; 
	cout<<"         9:基数排序                       q:退出系统    \n";
    cout<<"*****************************************************************\n";
    cout<<"请输入你要执行的操作:\n";
}

//开始程序
template<class T>
void begin(T a[],int n){
	showface();
	int i=0;
	char ch;
	cin>>ch;
	while(ch!='q'){
		switch (ch){
		case '1':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"直接插入排序后："<<endl;
				insert_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数直接插入排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '2':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"折半插入排序后："<<endl;
				bin_insert_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数折半插入排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '3':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"冒泡排序后："<<endl;
				buddle_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数冒泡排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '4':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"快速排序后："<<endl;
				quick_sort(a,0,n-1);
				print(a,n);
				t=clock()-t;
				cout<<N<<"个整数快速排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '5':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"选择排序后："<<endl;
				select_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数选择排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '6':
			{
				init(a,n);
				int step[]={5,3,1};
				int  step_lenth=sizeof(step)/sizeof(int);
				cout<<"增量数组为："<<endl;
				print(step,sizeof(step)/sizeof(int));
				clock_t t=clock();
				cout<<"希尔排序后："<<endl;
				shell_sort(a,step,n,step_lenth);
				t=clock()-t;
				cout<<N<<"个整数希尔排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '7':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"堆排序后："<<endl;
				heap_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数堆排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '8':
			{
				init(a,n);
				int temp[N];
				clock_t t=clock();
				cout<<"归并排序后："<<endl;
				merge_sort(a,temp,0,n-1);
				print(a,n);
				t=clock()-t;
				cout<<N<<"个整数归并排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			case '9':
			{
				init(a,n);
				clock_t t=clock();
				cout<<"基数排序后："<<endl;
				radix_sort(a,n);
				t=clock()-t;
				cout<<N<<"个整数基数排序耗时："<<t<<"毫秒。"<<endl;
				verify(a,n);
				system("pause");
				break;
			}
			default:
			{
				cout<<"请选择1~9\n按“Enter”键返回"<<endl;;
			}
		}
		getchar();
        showface();
		cin>>ch;
	}
}

int main(){
	begin(a,N);
	system("pause");
	return 0;
}
