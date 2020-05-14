# Data-Structures
#include<iostream>
#include<conio.h>
#include<stdlib.h>
using namespace std;
class Node
{
    public:
        int data;
        Node *next;
};

class list:public Node
{
    Node *listptr,*temp;
    public:
        list()
        {
            listptr=NULL;
            temp=NULL;
        }
        void create();
        void insert_start(int n);
        void insert_last(int n);
        void insert_between(int n);
        void delete_start();
        void delete_last();
        void delete_between();
        void reverse();
        void length();
        void display();
};

int main()
{
    list l;
    int c,k,i,n;
    while(1)
    {
        cout<<"1.Create\n2.Insert at first\n3.Insert at last\n4.Insert inbetween\n5.Delete at start\n6.Delete at last\n7.Delete inbetween\n8.Reverse\n9.Length of linked list\n10.Display\n11.Exit\n";
        cout<<"Enter your choice:\n";
        cin>>c;
        switch(c)
        {
            case 1:cout<<"enter number of nodes:";
                    cin>>k;
                    for(i=0;i<k;i++)
                    {
                        l.create();
                    }
                    break;
            case 2:cout<<"Enter value to insert at the beginning of list:";
                    cin>>n;
                    l.insert_start(n);
                    break;
            case 3:cout<<"Enter value to insert at the end of list:";
                    cin>>n;
                    l.insert_last(n);
                    break;
            case 4:cout<<"Enter value to insert inbetween list:";
                    cin>>n;
                    l.insert_between(n);
                    break;
            case 5:l.delete_start();
                    break;
            case 6:l.delete_last();
                    break;
            case 7:l.delete_between();
                    break;
            case 8:l.reverse();
                    break;
            case 9:l.length();
                    break;
            case 10:l.display();
                    break;
            case 11:return 0;
        }
    }
    return 0;
}
void list::create()
{
    Node *newnode=new Node;
    int n;
    cout<<"Enter an element:";
    cin>>n;
    newnode->data=n;
    newnode->next=NULL;
    if(listptr==NULL)
    {
        listptr=newnode;
        temp=newnode;
        temp=listptr;
    }
    else
    {
        temp->next=newnode;
        temp=temp->next;
    }
}
void list::insert_start(int n)
{
    Node *newnode=new Node;
    newnode->data=n;
    newnode->next=listptr;
    listptr=newnode;
}

void list::insert_last(int n)
{
    Node *newnode=new Node;
    Node *temp;
    temp=listptr;
    newnode->data=n;
    while(temp->next!=NULL)
    {
        temp=temp->next;
    }
    temp->next=newnode;
}

void list::insert_between(int n)
{
    Node *newnode=new Node;
    newnode->data=n;
    newnode->next=temp->next;
    temp->next=newnode;
}

void list::delete_start()
{
    Node *temp;
    temp=listptr;
    listptr=listptr->next;
    free(temp);
}
void list::delete_last()
{
    Node *q,*temp;
    temp=listptr;
    while(temp->next->next!=NULL)
    {
        temp=temp->next;
    }
    q=temp->next;
    free(q);
    temp->next=NULL;
}
void list::delete_between()
{
    Node *q,*temp;
    int n,c=1;
    cout<<"Enter node to delete:";
    cin>>n;
    temp=listptr;
    while(c!=n)
    {
        temp=temp->next;
        c++;
    }
    q=temp->next;
    temp->next=q->next;
    free(q);
}

void list::reverse()
{
    Node *back,*curr,*forw;
    forw=listptr;
    curr=NULL;
   while(forw!=NULL)
   {
	back=curr;
	curr=forw;
	forw=forw->next;
	curr->next=back;
    }
    listptr=curr;
}

void list::length()
{
    temp=listptr;
    int count=0;
    while(temp)
    {
        temp=temp->next;
        count++;
    }
    cout<<"length="<<count<<endl;
}

void list::display()
{
    Node *newnode=listptr;
    if(newnode==NULL)
    {
        cout<<"List is empty";
    }
    while(newnode!=NULL)
    {
        cout<<newnode->data;
        cout<<"-->";
        newnode=newnode->next;
    }
    cout<<"NULL\n";
}
