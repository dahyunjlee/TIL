#Linked Lists

##Reverse Print
###Iteration
```cpp
void ReversePrint(Node *head)
{
    int length = 0;
    Node* temp = head;
    if (!head)
        return;
    while (temp->next) {
        length++;
        temp = temp->next;
    }
    while(length >= 0) {
        cout << temp->data << endl;
        length--;
        temp = head;
        for (int i = 0; i < length; i++)
            temp = temp->next;
    }
}
```
###Recursion
```cpp
void RecursiveReverse(Node *head)
{
    if (!head)
        ;
    else {
        RecursiveReverse(head->next)
        cout << head->data << endl;
    }
}
```

##Reverse List
###Iteration
```cpp
Node* Reverse(Node *head)
{
    Node *prevNode, *nextNode;
    if (head == NULL || head->next == NULL)
        return head;
    
    while (head) {
        nextNode = head->next;
        head->next = prevNode;
        prevNode = head;
        head = nextNode;
    }
    head = prevNode;
    return head;
}
```

###Recursion
```cpp
Node* Reverse (Node *head)
{
    // base case
    if (head == NULL || head->next == NULL)
        return head;

    Node *nextNode = head->next;
    head->next = null;
    Node *newHead = Reverse(nextNode);  
        //will return tail node, right before  NULL, which is the new Head of the reversed list
    nextNode->next = head;
        // Head node in lower level is nextNode in higher -> reversing list

    return newHead;
}
```
