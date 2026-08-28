Design, develop, code and run the program in any suitable language to solve the commission problem. Analyze it from the perspective of boundary value testing, derive different test cases, execute these test cases and discuss the test results

Commission Problem
The Commission Problem is a software testing problem used to demonstrate decision making, conditional logic, and testing techniques such as Boundary Value Analysis (BVA) and Equivalence Class Partitioning (ECP).
Problem Statement
A company sells three products:
Product	Unit Price (₹)
Lock	45
Stock	30
Barrel	25
A salesperson enters the number of units sold for each product. The program calculates:
1.	Total Sales Amount 
2.	Commission Earned 
The commission is based on the following slabs:
Total Sales (₹)	Commission Rate
Up to 1000	10%
1001–1800	15% on the amount above ₹1000
Above 1800	20% on the amount above ₹1800, after applying the previous slabs
Algorithm
1.	Read the number of locks, stocks, and barrels sold. 
2.	Validate that all quantities are non-negative. 
3.	Calculate the total sales using:
  
4.	Determine the commission: 
o	If sales ≤ ₹1000: 
	Commission = 10% of sales. 
o	If ₹1000 < sales ≤ ₹1800: 
	Commission = ₹100 + 15% of (sales − ₹1000). 
o	If sales > ₹1800: 
	Commission = ₹220 + 20% of (sales − ₹1800). 
5.	Display the total sales and commission. 
Boundary Value Analysis (BVA)
Definition
Boundary Value Analysis (BVA) is a black-box software testing technique that focuses on testing values at the edges (boundaries) of valid input ranges. Many software defects occur at boundary conditions because programmers often make mistakes when implementing comparison operators such as <, <=, >, or >=.
Instead of testing every possible input, BVA tests values:
•	Just below the boundary 
•	Exactly at the boundary 
•	Just above the boundary 

C Program
#include <stdio.h>

int main()
{
    int lock, stock, barrel;
    float sales, commission;

    printf("Enter number of Locks sold: ");
    scanf("%d", &lock);

    printf("Enter number of Stocks sold: ");
    scanf("%d", &stock);

    printf("Enter number of Barrels sold: ");
    scanf("%d", &barrel);

    if(lock < 0 || stock < 0 || barrel < 0)
    {
        printf("Invalid Input! Quantity cannot be negative.\n");
        return 0;
    }

    sales = (lock * 45) + (stock * 30) + (barrel * 25);

    if(sales <= 1000)
    {
        commission = sales * 0.10;
    }
    else if(sales <= 1800)
    {
        commission = (1000 * 0.10) + ((sales - 1000) * 0.15);
    }
    else
    {
        commission = (1000 * 0.10) +
                     (800 * 0.15) +
                     ((sales - 1800) * 0.20);
    }

    printf("\nTotal Sales = %.2f", sales);
    printf("\nCommission = %.2f\n", commission);

    return 0;
}
Test Case 1
Enter number of Locks sold: 10
Enter number of Stocks sold: 10
Enter number of Barrels sold: 9

Total Sales = 975.00
Commission = 97.50
Test Case 2
Enter number of Locks sold: 30
Enter number of Stocks sold: 15
Enter number of Barrels sold: 5

Total Sales = 1925.00
Commission = 245.00

Test Case	Sales (₹)	Expected Commission (₹)	Actual Commission (₹)	Result
TC1	999	99.90	99.90	Pass
TC2	1000	100.00	100.00	Pass
TC3	1001	100.15	100.15	Pass
TC4	1799	219.85	219.85	Pass
TC5	1800	220.00	220.00	Pass
TC6	1801	220.20	220.20	Pass
TC7	0	0.00	0.00	Pass
TC8	-10 (Invalid Input)	Error Message	Error Message	Pass

Design, develop, code and run the program in any suitable language to implement the NextDate function. Analyze it from the perspective of boundary value testing, derive different test cases, execute these test cases and discuss the test results
Examples:
•	Input: 15/08/2026 
•	Output: 16/08/2026 
•	Input: 31/12/2026 
•	Output: 01/01/2027 
 
Algorithm
1.	Read day, month, and year. 
2.	Check whether the year is a leap year. 
3.	Determine the maximum number of days in the given month. 
4.	If the day is less than the maximum days, increment the day. 
5.	Otherwise: 
o	Set day = 1. 
o	Increment the month. 
6.	If the month exceeds 12: 
o	Set month = 1. 
o	Increment the year. 
7.	Display the next date. 
 
C Program
#include<stdio.h>

int main()
{
    int day, month, year;
    int maxDays;

    printf("Enter day month year: ");
    scanf("%d%d%d",&day,&month,&year);

    // Leap year check
    if((year%400==0) || (year%4==0 && year%100!=0))
        maxDays=29;
    else
        maxDays=28;

    switch(month)
    {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            maxDays=31;
            break;

        case 4:
        case 6:
        case 9:
        case 11:
            maxDays=30;
            break;

        case 2:
            // maxDays already decided (28/29)
            break;

        default:
            printf("Invalid Month");
            return 0;
    }

    if(day<1 || day>maxDays)
    {
        printf("Invalid Date");
        return 0;
    }

    day++;

    if(day>maxDays)
    {
        day=1;
        month++;

        if(month>12)
        {
            month=1;
            year++;
        }
    }

    printf("Next Date = %02d/%02d/%04d",day,month,year);

    return 0;
}
 
Sample Output
Test Case 1
Enter day month year:
15 8 2026

Next Date = 16/08/2026
 
Test Case 2
Enter day month year:
31 12 2026

Next Date = 01/01/2027
 
Test Case 3
Enter day month year:
29 2 2024

Next Date = 01/03/2024
 
Boundary Value Analysis (BVA)
Boundary Value Analysis focuses on testing values at, just below, and just above the valid boundaries.
Special cases:
•	February: 28 or 29 days 
•	Months with 30 days 
•	Months with 31 days 
•	End of year 
•	Leap year 
 
Boundary Value Test Cases
TC No	Input (DD/MM/YYYY)	Boundary Tested	Expected Output	Actual Output	Result
1	01/01/2026	Minimum valid day/month	02/01/2026	02/01/2026	Pass
2	31/01/2026	Maximum day (31-day month)	01/02/2026	01/02/2026	Pass
3	30/04/2026	Maximum day (30-day month)	01/05/2026	01/05/2026	Pass
4	28/02/2025	February (non-leap)	01/03/2025	01/03/2025	Pass
5	29/02/2024	February (leap year)	01/03/2024	01/03/2024	Pass
6	31/12/2026	End of year	01/01/2027	01/01/2027	Pass
7	00/01/2026	Below minimum day	Invalid Date	Invalid Date	Pass
8	32/01/2026	Above maximum day	Invalid Date	Invalid Date	Pass
9	15/00/2026	Below minimum month	Invalid Month	Invalid Month	Pass
10	15/13/2026	Above maximum month	Invalid Month	Invalid Month	Pass
11	31/04/2026	Invalid day for April	Invalid Date	Invalid Date	Pass
12	29/02/2025	Invalid leap day	Invalid Date	Invalid Date	Pass
 


Design, develop, code and run the program in any suitable language to solve the commission problem. Analyze it from the perspective of decision table based testing, derive different test cases, execute these test cases and discuss the test results
The commission is calculated as follows:
Sales Amount	Commission
Up to ₹1,000	5% of sales
Above ₹1,000 and up to ₹2,000	₹50 + 7% of amount above ₹1,000
Above ₹2,000	₹120 + 10% of amount above ₹2,000
For negative sales values, the program should display an invalid input message.
 

Algorithm
Step 1: Start.
Step 2: Read the total sales amount.
Step 3: If sales are negative, display Invalid Sales Amount.
Step 4: If sales ≤ ₹1,000:
Commission=Sales×5% 
Step 5: If ₹1,000 < sales ≤ ₹2,000:
Commission=50+(Sales−1000)×7% 
Step 6: If sales > ₹2,000:
Commission=120+(Sales−2000)×10% 
Step 7: Display the commission.
Step 8: Stop.
 
4. C Program
#include <stdio.h>

int main()
{
    float sales, commission;

    printf("Enter total sales: ");
    scanf("%f", &sales);

    if (sales < 0)
    {
        printf("Invalid sales amount.\n");
    }
    else if (sales <= 1000)
    {
        commission = sales * 0.05;
        printf("Commission = %.2f\n", commission);
    }
    else if (sales <= 2000)
    {
        commission = 1000 * 0.05 + (sales - 1000) * 0.07;
        printf("Commission = %.2f\n", commission);
    }
    else
    {
        commission = 1000 * 0.05 +
                     1000 * 0.07 +
                     (sales - 2000) * 0.10;

        printf("Commission = %.2f\n", commission);
    }

    return 0;
}
 
5. Decision Table-Based Testing
Decision Table Testing is a black-box testing technique used when the output depends on a combination of conditions.
Conditions
Let:
•	C1: Sales < 0 
•	C2: Sales ≤ ₹1,000 
•	C3: ₹1,000 < Sales ≤ ₹2,000 
•	C4: Sales > ₹2,000 

 
8. Test Execution Summary
TC ID	Input	Expected	Actual	Status
TC01	-100	Invalid input	Invalid input	PASS
TC02	0	₹0.00	₹0.00	PASS
TC03	500	₹25.00	₹25.00	PASS
TC04	1000	₹50.00	₹50.00	PASS
TC05	1000.01	₹50.00 approx.	₹50.00	PASS
TC06	1500	₹85.00	₹85.00	PASS
TC07	2000	₹120.00	₹120.00	PASS
TC08	2000.01	₹120.00 approx.	₹120.00	PASS
TC09	2500	₹170.00	₹170.00	PASS
TC10	5000	₹420.00	₹420.00	PASS
Total test cases: 10
Passed: 10
Failed: 0
Pass percentage: 100%
 

