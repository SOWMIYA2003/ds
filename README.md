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
```
node * LR(node *T)
{
// type your code here
T->left=rotateleft(T->left);
T=rotateright(T);
return(T); // T
}
```
```
// Delete operaiton
void delete (int item, struct BTreeNode *myNode) {
  // type your code here
  struct BTreeNode *temp; // see the parameter..
  if(delValFromNode(item,myNode) && myNode->count==0)
  {
      temp=myNode;
      myNode=myNode->linker[0];
      free(temp);
  }
  root=myNode;
  return; // just return..
}
```
```
// Insert the value
void insert(int val) {
  //type your code here
  int flag,i;
  struct BTreeNode *child; // child pointer ..
  flag=setValue(val,&i,root,&child);
  if(flag)
  {
      root=createNode(i,child);  // createNode..
  }
}
```
```
void create_graph()
{ int i,max_edges,origin,destin;
        //type your code here...
        scanf("%d",&n);
        max_edges=n*(n-1);
        for(i=1;i<=max_edges;i++)
        {
            scanf("%d",&origin);
            scanf("%d",&destin);
        
        if(origin==-1 && destin ==-1)  // conditions inside for loop only ..
        {  
            break;
        }
        if(origin>=n||destin>=n||origin<0||destin<0)
        {
            printf("Invalid Edge");
            i--;
        }
        else
        {
            adj[origin][destin]=1;
        }
        }
      }

```
```
int main()
{ int e1,e2,me,n,i;
  scanf("%d",&V);
  int adjMatrix[V][V];
  init(adjMatrix);
  n=V;
  me=n*(n-1)/2;
  for(i=0;i<=me;i++)
  {
      scanf("%d%d",&e1,&e2);
      addEdge(adjMatrix,e1,e2);
      if(e1==-1 && e2==-1)
      {
          break;
      }
  }
  printAdjMatrix(adjMatrix);
  
  
  //type your code here...
}

```
```
int main(void)
{   //type your code here....
int i,n;
scanf("%d",&N); // first capital N
scanf("%d",&n);

struct Edge edges[n];
for(i=0;i<n;i++)
{
    scanf("%d",&edges[i].src);
    scanf("%d",&edges[i].dest);
}
struct Graph *graph= createGraph(edges,n);
printGraph(graph);
return 0;
}

```
```
void bfs(struct Graph* graph, int startVertex) {
 //type your code here
 struct queue *q = createQueue();
 graph->visited[startVertex]=1;
 enqueue(q,startVertex);
 while(!isEmpty(q))
 {
     printQueue(q);
     int currentVertex=dequeue(q);
     printf("Visited %d\n ",currentVertex);
     
     struct node* temp = graph->adjLists[currentVertex];
     while(temp)
     {
         int adjVertex=temp->vertex; // temp vertex
         if(graph->visited[adjVertex]==0)
         {
             graph->visited[adjVertex]=1;
             enqueue(q,adjVertex);
         }
         temp=temp->next; // next temp..
     }
 }
}
```
