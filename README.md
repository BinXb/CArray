# CArray
c语言数组
### 数组
#### 一维数组的创建和初始化
##### 数组的创建
**数组是一组相同类型元素的集合，数组的创建方式：**
>type_t  arr_name [type_n]
type_t  -- 数组类型
type_name -- 数组名
type_n -- 是一个常量表达式，用来指定数组大小



#### 数组下标的计算
>sz = sizeof(arr)/sizeof(arr[0]);//数组总大小/一个元素所占空间的大小 = 数组下标
```
int main() {
	//创建一个数组-存放整型-10个
	int arr[10];
	//创建一个数组-存放字符型-5个
	char arr2[5];

	return 0;
}
```
##### 数组的初始化
>
```

int main() {
	//创建一个数组-存放整型-10个
	int arr[10]={1,2,3};//不完全初始化，剩下的元素默认初始化为0
	//创建一个数组 - 存放字符型 - 5个
	char arr2[5]={'a','b'};
	char arr3[5] = "ab";
	char arr4[] = "abcdef";
	printf("%d\n", sizeof(arr4));//7
	//sizeof(计算arr4所占空间大小
	printf("%d\n", strlen(arr4));//6
	//strlen求字符串长度

	//1.strlen与sizeof没什么关联
	//2.strlen只能求字符串长度 - 库函数 - 使用需要引头文件
	//3.sizeof 计算变量，数组，类型的大小 - 单位是字节 - 操作符
	return 0;
}

```

```

int main() {
	char arr1[] = "abc";
	char arr2[] = { 'a','b','c' };
	printf("%d\n", sizeof(arr1));//4
	printf("%d\n", sizeof(arr2));//3
	printf("%d\n", strlen(arr1));//3
	printf("%d\n", strlen(arr2));//随机值

	return 0;
}
```
#### 一维数组的使用
>使用数组下表进行访问
```
int main() {
	/*char arr[] = "abcdef";
	int i = 0;
	for (i = 1; i < strlen(arr); i++) {
		printf("%c\n", arr[i]);
	}*/
	int arr[] = { 1,2,3,4,5,6,7,8,9,0 };
	int i = 0;
	int sz = sizeof(arr) / sizeof(arr[0]);
	for (i = 0; i <= sz; i++) {
		printf("%d\n", arr[i]);
	}
	return 0;
}
```

#### 一维数组的内存存储
>
```
int main() {
	int arr[] = { 1,2,3,4,5,6,7,8,9,10 };
	int sz = sizeof(arr) / sizeof(arr[0]);
	int i = 0;
	for (i = 0; i < sz;i++) {
		printf("&arr[%d] = %p\n",i, &arr[i]);
	}
	return 0;
}
```
<img width="628" alt="数组" src="https://user-images.githubusercontent.com/114718718/196068775-c0b90936-36a5-46b8-b586-61706ebaf8c4.png">
数组在内存中时连续存放的 -- 地址是由低到高

#### 二维数组
>arr[行][列
	int arr[3][4];//创建一个三行四列的二维数组
	int arr2[5][6];//创建一个五行六列的二维数组
```
int main() {
	int arr[3][4];
	int arr2[5][6];
	return 0;
}
```
<img width="537" alt="二维数组" src="https://user-images.githubusercontent.com/114718718/196068792-e597b002-dc94-4099-a4c5-38a052d658bf.png">

#### 二维数组的初始化

>arr[行][列]   --   行可以省，列不可以省，不然会报错

>int arr[][4] = { {1,2,3},{4,5} };
```
int main() {
	/*int arr[3][4] = {{1,2,3},{4,5}};
	int arr2[5][6];*/
	int arr[][4] = { {1,2,3},{4,5} };
	return 0;
}
```
#### 二维数组的使用
>
```
int main() {
	int arr[3][4] = {{1,2,3},{4,5}};
	int i = 0;
	for (i = 0; i < 3;i++) {
		int j = 0;
		for (j = 0; j < 4; j++) {
			printf("%d ", arr[i][j]);
		}
		printf("\n");
	}
	/*int arr2[5][6];
	int arr[][4] = { {1,2,3},{4,5} };*/
	return 0;
}
```
#### 二位数组在内存中的储存
>与一维数组类似，
```
int main() {
	int arr[3][4] = {{1,2,3},{4,5}};
	int i = 0;
	for (i = 0; i < 3;i++) {
		int j = 0;
		for (j = 0; j < 4; j++) {
			printf("arr[%d][%d] = %p\n", i, j, &arr[i][j]);
		}
	}
	return 0;
}
```
<img width="541" alt="二维数组的存储" src="https://user-images.githubusercontent.com/114718718/196068818-31f70f13-e4e4-4ac1-be71-e57c16b0c3cf.png">
**每个元素需要四个字节储存，arr[0][0] = 0000006C392FFAA8与arr[0][1] = 0000006C392FFAAC相隔四个字节**
这是在我的电脑上运行的，然后电脑分配的内存空间，在你的电脑上可能不同，但一样的是肯定是每个元素相隔4个字节(64位)
arr[0][0] = 0000006C392FFAA8
arr[0][1] = 0000006C392FFAAC
arr[0][2] = 0000006C392FFAB0
arr[0][3] = 0000006C392FFAB4
arr[1][0] = 0000006C392FFAB8
arr[1][1] = 0000006C392FFABC
arr[1][2] = 0000006C392FFAC0
arr[1][3] = 0000006C392FFAC4
arr[2][0] = 0000006C392FFAC8
arr[2][1] = 0000006C392FFACC
arr[2][2] = 0000006C392FFAD0
arr[2][3] = 0000006C392FFAD4
<img width="777" alt="二维数组的储存2" src="https://user-images.githubusercontent.com/114718718/196068935-f3adf63e-49ff-4764-b4de-89ef49910497.png">
由低 	————————————————————>>> 	到高


### 数组作为函数参数
#### 冒泡排序
```

void bubble_sort(int arr[], int sz) {
	//确定冒泡排序的趟数
	int i = 0;
	for (i = 0; i < sz; i++) {
		int flag = 1;//假设这一趟排序的数据已经有序
		//每一趟冒泡排序
		int j = 0;
		for (j = 0; j < sz - 1 - i; j++) {
			if (arr[j] > arr[j + 1]) {
				int tmp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = tmp;
				flag = 0;//本趟排序的数据不完全有序
			}
		}
		if (flag == 1) {
			break;
		}
	}
}
int main() {
	int arr[] = { 9,8,7,6,5,4,3,2,1,0 };
	int i = 0;
	int sz = sizeof(arr) / sizeof(arr[0]);
	//对arr进行排序，排成升序
	bubble_sort(arr, sz);
	for (i = 0; i < sz; i++) {
		printf("%d ", arr[i]);
	}
	return 0;
}

```
#### 数组名是什么
>数组名就是数组首元素的地址
例外：1.sizeof(数组名) -- 数组名表示真个数组，sizeod(数组名)计算的是整个数组的大小
		2.&数组名 -- 取出的是整个数组的地址

```
int main() {
	int arr[] = { 1,2,3,4 };
	//arr数组首元素的地址
	printf("%p\n", arr);
	printf("%d\n", arr[0]);
	//&arr - 整个数组的地址
	printf("%p\n", &arr);//& - 取地址操作符，取出的是数组的地址,只是显示第一个元素的地址，但其实是整个数组的地址


	return 0;
}
```
















