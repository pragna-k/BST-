# Bfs-



#include<stdio.h>
#define MAX 50
int visited[MAX];
int graph[MAX][MAX];
int n,f=-1,r=-1;
int queue[MAX];
void readGraph()
{
    printf("Enter size of the Adjacency Matrix :\n");
    scanf("%d",&n);
    printf("Enter Adjacency Matrix :\n");
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=n;j++)
        {
            scanf("%d",&graph[i][j]);
        }
    }
}
void enque(int x)
{
    if(f==-1)
    {
        f=r=0;
    }
    else
    {
        r=r+1;
    }
    queue[r]=x;
}
int deque()
{
    int x;
    if(f==-1)
    {
        return -1;
    }
    else if(f==r)
    {
        x=f;
        f=r=-1;
        return queue[x];
    }
    else
    {
        x=f;
        f=f+1;
        return queue[x];
    }
}
void BFS(int v)
{
    visited[v]=1;
    printf("%d ",v);
    while(1)
    {
        for(int i=1;i<=n;i++)
        {
            if(visited[i]==0 && graph[v][i]==1)
            {
                enque(i);
                visited[i]=1;
            }
        }
        v=deque();
        if(v==-1)
        {
            break;
        }
        else
        {
            printf("%d ",v);
        }
    }
    printf("\n");
}
void main()
{
    readGraph();
    printf("Breadth First Search :\n");
    for(int j=1;j<=n;j++)
    {
        printf("Graph Start at vertex %d\n",j);
        for(int i=1;i<=n;i++)
        {
            visited[i]=0;
        }
        BFS(j);
    }
}
output:
Enter size of the Adjacency Matrix :
6
Enter Adjacency Matrix :
0
1
1
1
0
0
1
0
1
0
1
0
1
1
0
1
1
1
1
0
1
0
0
1
0
1
1
0
0
0
0
0
1
1
0
0
Breadth First Search :
Graph Start at vertex 1
1 2 3 4 5 6 
Graph Start at vertex 2
2 1 3 5 4 6 
Graph Start at vertex 3
3 1 2 4 5 6 
Graph Start at vertex 4
4 1 3 6 2 5 
Graph Start at vertex 5
5 2 3 1 4 6 
Graph Start at vertex 6
6 3 4 1 2 5 

