Created by : seophohoho  
Created datetime : 2023-12-26 11:58  
Tags :  #Data_Structure
## Source code
```C
#include <stdio.h>
#include <stdlib.h>

typedef struct node{
  int data;
  struct node *next;
}Node;

Node *head = NULL;

void printList(){
  Node *ptr = head;
  while(ptr != NULL){
    printf("data %d, next %x\n",ptr->data,ptr->next);
    ptr = ptr->next;
  }
}

void insertLast(int data){
  Node *last = head;
  while(last->next != NULL){
    last = last->next;
  }
  Node *p = (Node*)malloc(sizeof(Node));
  p->data = data;
  p->next = NULL;

  last->next = p;
}

void insertFront(int data){
    Node *p = (Node *)malloc(sizeof(Node));
    p->data = data;
    p->next = head;
    head = p;
}

void deleteLast(){
  Node *last = head;
  Node *prev = head;
  int lastCnt=0;
  while(last->next != NULL){
    if(lastCnt > 0){
      prev = prev->next;
    }
    last = last->next;
    lastCnt++;
  }
  prev->next = NULL;

}

void deleteFront(){
  Node *target = head;
  Node *rm = head->next;
  head = rm;
  free(target);
}

void detectData(int data){
  Node *start = head;
  int isLocated = 0; 
  while(start != NULL){
    if(start->data == data){
      printf("Find %d!!, it is located in %x\n",data,start);
      isLocated = 1;
      break;
    }
    start = start->next;
  }
  if(!isLocated){
    printf("%d is Nothing.....\n",data);
  }
}
int main(){
  insertFront(500);
  insertFront(666);
  insertFront(1000);
  insertFront(10);
  insertFront(20);
  insertFront(30);
  insertLast(999);
  insertLast(899);
  deleteLast();
  printList();
  detectData(30);
  detectData(999);
  detectData(1);

  return 0;
}
```