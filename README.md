# 5-Toplogical

Topological Sorting Algorithm:
#include<stdio.h>
#include<conio.h>
int indegree[20],t[20],a[20][20],n;
void t_sort()
{
int top=-1,k=0,i,j,sum=0,s[20],u,v;
for(j=1;j<=n;j++)
{
sum=0;
for(i=1;i<=n;i++)
sum=sum+a[i][j];
indegree[j]=sum;
}
for(i=1;i<=n;i++)
{
if(indegree[i]==0)
{
top=top+1;
s[top]=i;
}
}
while(top!=-1)
{
u=s[top];
top=top-1;
t[k++]=u;
for(v=1;v<=n;v++)
{
if(a[u][v]==1)
{
indegree[v]--;
if(indegree[v]==0)
{
top=top+1;
s[top]=v;
}
}
}
}
printf("\n Topological sequence is: \n");
for(i=0;i<k;i++)
printf("%d\t",t[i]);
}
void main()
{
int i,j;
printf("enter the no. of vertices\n");
scanf("%d",&n);
printf("enter the adjacency matrix\n");
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
scanf("%d",&a[i][j]);
}
t_sort();
}
