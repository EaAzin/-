#include <stdio.h>
#include <stdlib.h>

struct node
{
	int data;
	node* next;
};
typedef node* Linklist;
Linklist Makelist()
{
	Linklist L = (node*)malloc(sizeof(node));
	L->next = NULL;
	return L;
}

int isNULL(Linklist L)
{
	if (L->next == NULL)
		return 1;
	else
		return 0;
}

void Append(Linklist L, int data)
{
	node* p = L;
	while (p->next != NULL)
	{
		p = p->next;
	}
	node* n = (node*)malloc(sizeof(node));
	n->data = data;
	p->next = n;
	n->next = NULL;
}
int Len(Linklist L)
{
	node* p = L;
	int len = 0;
	while (p->next != NULL)
	{
		p = p->next;
		len++;
	}
	return len;
}
void Headin(Linklist L, int data)
{
	node* n = (node*)malloc(sizeof(node));
	n->data = data;
	n->next = L->next;
	L->next = n;
}

void change(Linklist L, int pos, int data)
{
	int i = 0;
	node* p = L;
	while (i != pos - 1)
	{
		p = p->next;
		i++;
	}
	p->next->data = data;
}
void insert(Linklist L, int pos, int data)
{
	printf("正在插入链表元素\n");
	int i = 0;
	node* p = L;
	while (i = pos - 1)
	{
		p = p->next;
		i++;
	}
	node* n = (node*)malloc(sizeof(node));
	n->data = data;
	n->next = p->next;
	p->next = n;
}

void showlist(Linklist L)
{
	node* p = L;
	while (p->next != NULL)
	{
		p = p->next;
		printf("%d  ", p->data);

	}
	printf("\n链表展示完毕");
}
void delet(Linklist L, int pos, int data)
{
	printf("进行删除元素操作中......");
	node* p = L;
	int i = 0;
	while (i != pos - 1)
	{
		p = p->next;
		i++;
	}
	node* q = p->next->next;
	free(p->next);
	p->next = q;
}
void cancel(Linklist L)
{
	node* p = L;
	node* q = p;
	while (p->next != NULL)
	{
		q = p->next;
		free(p);
		p = q;
	}
	printf("\n");
	printf("链表删除成功!\n");
}


int main()
{
	char ch;
	Linklist L = Makelist();
	printf("该链表是否为空:%d(0非空/1空)", isNULL(L));
	while ((ch = getchar()) != '\n')
	{
		Append(L, ch - '0');
	}
	printf("当前链表长度为%d", Len(L));
	while ((ch = getchar()) != '\n')
	{
		Headin(L, ch - '0');
	}

	return 0;
}
