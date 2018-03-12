## 题目
>Given a linked list, determine if it has a cycle in it.
>Follow up:
>Can you solve it without using extra space?
## 问题分析：
##### 这道题思路其实很简单，主要是练习了一下链表，判断链表是不是循环的，只需遍历链表每个节点，在链表不为空的情况下，用两个指针，一快一慢，判断它们是否最终会相遇，相遇即为循环，主要问题在于，编写出代码后在主函数中不会调用，判断花了较长时间，解题还是比较容易的。
## 代码实现：
```cpp
c++:

struct ListNode {
      int val;
     ListNode *next;
     ListNode(int x) : val(x), next(NULL) {}
 };
 bool dev(ListNode*head)
 {
 	if(head==NULL||head->next==NULL)
 	return false;
 	ListNode*f=head;
 	ListNode*s=head;
 	do{
	 	
	 	if(f==NULL||f->next==NULL)
	 	return false;
	 	f=f->next->next;
	 	s=s->next;
 	}
	 	while(f==s);
	 	return true;
 }
 ```
 ## 方法二
#### 也可以比较 链表节点的地址 比较节点和下一个节点的值，如果下一个节点的地址值比该节点的地址值小或者相等的话就是循环链表
## 代码实现：
```cpp
bool dev(ListNode*head)  
{       
ListNote *temp = head;    
while(temp!=NULL &&temp->next!= NULL)
{    
if (temp->next<=temp)      
{   
return true;           
}    
temp = temp->next;      
}    
return false;  
} ；
```
