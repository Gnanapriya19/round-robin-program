IMPLEMENTATION OF ROUND ROBINSCHEDULING
ALGORITHM
PROGRAM:
#include<stdio.h> voidmain()
{
int ct=0,y[30],j=0,bt[10],cwt=0; int tq,i,max=0,n,wt[10],t[10],at[10],tt[10],b[10]; float a=0.0,s=0.0;
char p[10][10];
printf("\n enter the no of process:"); scanf("%d",&n);
printf("\nenter the time quantum"); scanf("%d",&tq);
printf("\nenter the process name,bursttime,arrival time");
for(i=0;i<n;i++)
{
scanf("%s",p[i]);
scanf("%d",&bt[i]); scanf("%d",&at[i]); wt[i]=t[i]=0; b[i]=bt[i];
}
printf("\n\t\tGANTT CHART"); printf("\n	\n"); for(i=0;i<n;i++)
{
if(max<bt[i])
max=bt[i];
}
while(max!=0)
{
for(i=0;i<n;i++)
{
if(bt[i]>0)
{
if(ct==0)
wt[i]=wt[i]+cwt;
 
else}wt[i]=wt[i]+(cwt-t[i]);
if(bt[i]==0) cwt=cwt+0;
else if(bt[i]==max)
{
if(bt[i]>tq)
{
cwt=cwt+tq;}
else
{
} 
bt[i]=bt[i]-tq; max=max-tq;
cwt=cwt+bt[i]; bt[i]=0; max=0;
printf("|\t%s",p[i]); y[j]=cwt;
j++;
}
else if(bt[i]<tq)
{
cwt=cwt+bt[i]; bt[i]=0; printf("|\t%s",p[i]); y[j]=cwt;
j++;
}
else if(bt[i]>tq)
{
cwt=cwt+tq; bt[i]=bt[i]-tq;
printf("|\t%s",p[i]); y[j]=cwt;
j++;
}
else if(bt[i]==tq)
{
cwt=cwt+bt[i];
 


printf("|\t%s",p[i]); bt[i]=0; y[j]=cwt; j++;
}
t[i]=cwt;
}
ct=ct+1;
}
for(i=0;i<n;i++)
{
wt[i]=wt[i]-at[i]; a=a+wt[i]; tt[i]=wt[i]+b[i]-at[i]; s=s+tt[i];
}
a=a/n; s=s/n; printf("\n	");
printf("\n0"); for(i=0;i<j;i++)
printf("\t%d",y[i]); printf("\n");
printf("\n	"); printf("\n\t\t ROUND ROBIN\n");
printf("\n	Process	Burst-time	Arrival-time	Waiting-time	Turnaround- time\n");
for(i=0;i<n;i++)
printf("\n\n %d%s \t %d\t\t %d \t\t %d\t\t %d", i+1, p[i], b[i], at[i], wt[i], tt[i]);
printf("\n\nAvg waiting time=%f",a); printf("\n\nAvgturn around time=%f",s);
}
 


OUTPUT:
enter the no of process:3 enter the time quantum2
enter the process name, bursttime, arrival time

p1	2	0
p2	3	1
p3	4	2
GANTT CHART
|	p1|	p2|	p3|	p2|	p3
0	2	4	6	7	9

ROUND ROBIN

Process	Burst-time	Arrival-time	Waiting-time	Turnaround-time
p1	2	0	0	2
p2	3	1	3	5
p3	4	2	3	5
Avg Waiting Time=2.000000 Avg Turnaround Time=4.000000
