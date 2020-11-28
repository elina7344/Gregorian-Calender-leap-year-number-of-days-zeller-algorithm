
//GREGORIAN CALENDAR PROGRAM + TO FIND THE YEAR IS A LEAP YEAR OR NOT + TO PRINT THE NUMBER OF DAYS A YEAR HAS + ZELLER ALGORITHM TO FIND DAY USING DATE AS INPUT//
#include <stdio.h>
#include <stdlib.h>
//To calculate the starting day of the first January of the year inputed by the user we have to add another function//
//If this function return 0 that means the starting day of 1st January is Sunday.//
//If it returns 1 then the starting day of 1st January is Monday//
//Thus this function will return any value from 0-6 including 0 and 6//
int get_1st_weekday(int year)
{
//To convert the Gregorian date to a date of the week
    int day;
//Given the year this will find the day of the week for January 1, where Sunday is 0 and Saturday is 6//
    day = (((year - 1) * 365) + ((year - 1) / 4) - ((year - 1) / 100) + ((year) / 400) + 1) % 7;
    return day;
}
int main()
{
//Set the background color as purple and text color as white//
//This code is included in #include <stdlib.h> header file//
system("Color 05F");
//Variable Declaration//
int year,i,j,k,m=0,n;
printf("\nEnter the year to view its calender(YYYY):");
scanf("%d",&year);
//Character and Pointer Array. DataType = Character//
//If elements are specified no need to give size//
char *month[]={"JANUARY","FEBRUARY","MARCH","APRIL","MAY","JUNE","JULY","AUGUST","SEPTEMBER","OCTOBER","NOVEMBER","DECEMBER"};
//Integer Array for dates of the months//
int day[]={31,28,31,30,31,30,31,31,30,31,30,31};
//Defining the case for leap year//
if((year%4==0 && year%100!=0) || year%400==0)
    day[1]=29;
//This will give which week day will be first January of the year//
n=get_1st_weekday(year);
//for loop for printing months and week days//
for(i=0;i<12;i++)
{
    k=day[i];
    printf("\n\n~~~~~~~~~~~~~~~~%s~~~~~~~~~~~~~~~~~\n",month[i]);
printf("\n  Sun  Mon  Tue  Wed  Thurs  Fri  Sat\n");

for(n=0;n<m;n++)

printf("     ");

for(j=1;j<=k;j++)
{
    printf("%5d",j);

//Condition checking for days of the week are greater than 6//
//Initialized Sunday as 6//

    if(++m>6)
    {
//when is the condition is crossed the dates will shift to a new line//
         printf("\n");
//to run the program code for each line we have to initialize m=0//
         m=0;
    }
}
n=m;
}
//Program code to find if a year is leap year or not//
if(year % 400 == 0)
{

printf("\n\n%d is a Leap Year",year);
}
else if (year % 100 == 0)
{
    printf("\n\n%d is not a Leap Year.",year);
}
else if(year % 4 == 0)
{
    printf("\n\n%d is a Leap Year.",year);
}
else
{
 printf("\n\n%d is not a Leap Year.",year);
}
//Program code to find the number of days in a year//
if(year % 400 == 0)
{

printf("\n\nThere are 366 days in the year %d",year);
}
else if (year % 100 == 0)
{
    printf("\n\nThere are 365 days in the year %d",year);
}
else if(year % 4 == 0)
{
    printf("\n\nThere are 366 days in the year %d",year);
}
else
{
 printf("\n\nThere are 365 days in the year %d",year);
}
//Zeller Algorithm//
//Zeller’s congruence is an algorithm devised by Christian Zeller//
//It is used to calculate the day of the week for any Gregorian calendar date//
 int h,q,s,t,u,D,M,Y;
  printf("\n\nTo find the particular day on the date please enter(dd/mm/yyyy)\n");
  scanf("%i/%i/%i",&D,&M,&Y);
  if(M == 1)
  {
    M = 13;
    Y--;
  }
  if (M == 2)
  {
    M = 14;
    Y--;
  }
  q = D;
  s = M;
  t = Y % 100;
  u = Y / 100;
  h = q + floor(13/5*(s+1)) + t + floor(t/4) +  floor(u/4) + 5 * u;
  h = h % 7;
  switch(h)
  {
    case 0 : printf("\nThe day is : Saturday \n");
break;
    case 1 : printf("\nThe day is : Sunday \n");
break;
    case 2 : printf("\nThe day is : Monday \n");
break;
    case 3 : printf("\nThe day is : Tuesday \n");
break;
    case 4 : printf("\nThe day is : Wednesday \n");
break;
    case 5 : printf("\nThe day is : Thursday \n");
break;
    case 6 : printf("\nThe day is : Friday \n");
break;
  }
return 0;
}
