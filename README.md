# MENG
课程作业
#include<stdio.h>
#include<windows.h>
#include<string.h>
#include<conio.h>
#define m 9
#define n 11
char a[m][n+1]={
	{"*#*********"},
	{"***###*###*"},
	{"###**#****#"},
	{"*#**###**#*"},
	{"***********"},
    {"#####*##*##"},
	{"**#*****#*E"},
    {"***#*###**#"},
	{"*#*********"},
    };
void map()
{
	for(int i=0;i<m;i++)
    {
    	puts(a[i]);
	}	
}
void show_cursor(int x,int y)
{
	COORD pos;
	pos.X=x;
	pos.Y=y;
	printf("curX=%d,curY=%d\n",x,y);
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}
int curX,curY;
int main()
{
	while(1)
	{
		system("cls");
	   map();
       show_cursor(curX,curY);
       char t=getch();	
       if(t=='8')
       {
       	if((curY-1)>=0&&(a[curY-1][curX]=='*'||a[curY-1][curX]=='E'))//条件一 
       	curY--;
	   }
	   else if(t=='5')
	   {
	   	if((curY+1)<=m&&(a[curY+1][curX]=='*'||a[curY+1][curX]=='E'))//条件二 
	   	curY++;
	   }
	   else if(t=='4')
	   {
	   	if((curX-1)>=0&&(a[curY][curX-1]=='*'||a[curY][curX-1]=='E'))//条件三 
	   	curX--;
	   }
	   else 
	   {
	   	if(t=='6')
	   	{
	   		if((curX+1)<=n&&(a[curY][curX+1]=='*'||a[curY][curX+1]=='E'))//条件四 
	   	curX++;
		   }
	   }
	   if(a[curY][curX]=='E') 
	      break;
	 } 
	 printf("恭喜你走出迷宫\n"); 
	return 0;
 }
