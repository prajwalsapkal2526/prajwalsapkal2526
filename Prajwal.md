
#include <stdio.h>
#include <stdlib.h>
int isLeapYear(int year) 
{
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}
int daysInMonth(int month, int year)
 {
    switch (month) {
        case 1: case 3: case 5: case 7: case 8: case 10: case 12:
            return 31;
        case 4: case 6: case 9: case 11:
            return 30;
        case 2:
            return isLeapYear(year) ? 29 : 28;
        default:
            return 0;
    }
}

int main() {
    int birthDay, birthMonth, birthYear;
    int currentDay, currentMonth, currentYear;
    printf("Enter your birth date (DD MM YYYY): ");
    scanf("%d %d %d", &birthDay, &birthMonth, &birthYear);
    printf("Enter the current date (DD MM YYYY): ");
    scanf("%d %d %d", &currentDay, &currentMonth, &currentYear);
    int ageYears = currentYear - birthYear;
    int ageMonths = currentMonth - birthMonth;
    int ageDays = currentDay - birthDay;
    if (ageDays < 0) 
	{
        ageMonths--;
        ageDays += daysInMonth((currentMonth == 1 ? 12 : currentMonth - 1), currentYear);
    }
    if (ageMonths < 0)
	 {
        ageYears--;
        ageMonths += 12;
    }
    printf("Your age is: %d years, %d months, and %d days.\n", ageYears, ageMonths, ageDays);

    return 0;
}


OUTPUT:

 
