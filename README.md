# ds

```
node * Delete(node *T,int x)
{
    //type your code here
    node *p;
    if(T==NULL)
    {
        return NULL;  // ws - //return T;
    }
    else  if ( x > T->data)
    {
        T->right=Delete(T->right,x);
        if(BF(T)==2)
        {
            if(BF(T->left)>=0)
            {
                T=LL(T);
            }
            else
            {
                T=LR(T);
            }
        }
    }
    else if(x < T->data)
    {
        T->left=Delete(T->left,x);
        if(BF(T)==-2)
        {
            if(BF(T->right)<=0)
            {
                T=RR(T);
            }
            else{
                T=RL(T);
            }
        }
    }
    else  // inide else part we have if else statement..
    {
        if(T->right !=NULL)
        {
            p=T->right;
            while(p->left!=NULL)
            p=p->left;
            T->data=p->data;
            T->right=Delete(T->right,p->data);
            if(BF(T)==2)
            {
                if(BF(T->left)>=0)
                {
                    T=LL(T);
                }
                else{
                    T=LR(T);
                }
            }
        }
        else
        {
            return (T->left);
        }
    }
    // after else part onlyy..
    T->ht=height(T);
    return(T);
   
}

```
```
node * insert(node *T,int x)
{
    // type your code here
    if(T==NULL)
    {
        T=(node*)malloc(sizeof(node));
        T->data=x;
        T->left=NULL;
        T->right=NULL;
    }
    else if( x >T->data)
    {
        T->right=insert(T->right,x);
        if(BF(T)==-2) // minus 2 here....
        {
            if(x>T->right->data)
            {
                T=RR(T);
            }
            else
            {
                T=RL(T);
            }
        }
    }
    else if(x<T->data)
    {
        T->left=insert(T->left,x);
        if(BF(T)==2) // plus 2 here...
        {
            if(x<T->left->data)
            {
                T=LL(T);
            }
            else
            {
                T=LR(T);
            }
        }
    }
    T->ht=height(T);
    return (T);
}

```
