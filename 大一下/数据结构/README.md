## 数据结构

#### 基本题型
- 选择题(考察对于概念的理解)
- 填空题(主要是重要算法的计算过程)
- 编程题

根据往年规律，编程题考试内容
1. 第一题考察排序算法，根据题目要求对数组进行排序，重点掌握C语言qsort函数
```C
#include<stdlib.h>
//C语言标准库函数qsort
void qsort(
    void *base, //待排序数组的首地址
    size_t num, //待排序数组的元素个数
    size_t size, //每个元素的大小（字节数）
    int (*compar)(const void *, const void *) //比较函数指针：自定义排序规则
    );

//示例：按照成绩升序排序，成绩相等按序号降序排序
int compare(const void *a, const void *b) {
    Student *studentA = (Student *)a;
    Student *studentB = (Student *)b;

    if (studentA->score != studentB->score) {
        return studentA->score - studentB->score; //成绩升序
    } else {
        return studentB->id - studentA->id; //成绩相等按序号降序
    }
}

qsort(students, numStudents, sizeof(Student), compare);
```

2. 第二题考察栈或对列的应用，下面列举一些基本操作，具体方法依据具体题目要求进行调整。
栈基本操作
```C
int top = -1; //栈顶指针

//入栈
void push(int stack[], int value) {
    stack[++top] = value; //将元素压入栈顶
}

//出栈
int pop(int stack[]) {
    return stack[top--]; //返回栈顶元素并将栈顶指针下移
}

//获取栈顶元素
int peek(int stack[]) {
    return stack[top]; //返回栈顶元素但不修改栈顶指针
}

//判断栈是否为空
int isEmpty() {
    return top == -1; //当栈顶指针为-1时，栈为空
}

//判断栈是否满
int isFull(int maxSize) {
    return top == maxSize - 1; //当栈顶指针等于最大容量-1时，栈为满
}
```
队列基本操作
```C    
int front = 0; //队头指针
int rear = 0; //队尾指针
//入队
void enqueue(int queue[], int value, int maxSize) {
    if ((rear + 1) % maxSize == front) {
        //队列已满，无法入队
        return;
    }
    queue[rear] = value; //将元素放入队尾
    rear = (rear + 1) % maxSize; //更新队尾指针
}
//出队
int dequeue(int queue[], int maxSize) {
    if (front == rear) {
        //队列为空，无法出队
        return -1; //返回-1表示队列为空
    }
    int value = queue[front]; //获取队头元素
    front = (front + 1) % maxSize; //更新队头指针
    return value; //返回出队的元素
}
```

3. 第三题考察树或图的应用，依据每年课程组要求复习

#### 复习参考
重点参考这个[复习仓库](https://github.com/MitakeMoca/BUAA_DS)