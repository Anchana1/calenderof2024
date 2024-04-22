# calenderof2024
-----------------c program--------------------------
#include <stdio.h>

void month(int year, int month) {
	printf("\n%s %d\n", (month == 1) ? "January" : (month == 2) ? "February" : (month == 3) ? "March" :
						(month == 4) ? "April" : (month == 5) ? "May" : (month == 6) ? "June" :
						(month == 7) ? "July" : (month == 8) ? "August" : (month == 9) ? "September" :
						(month == 10) ? "October" : (month == 11) ? "November" : "December", year);
	printf("Mo Tu We Th Fr Sa Su\n");

	int weekday = (year * 365 + (year - 1) / 4 - (year - 1) / 100 + (year - 1) / 400 + month * 306 + 5) % 7;
	int days_in_month = 0;

	switch (month) {
		case 4:
    case 6:
    case 9:
    case 11:
			days_in_month = 30;
			break;
		case 2:
			days_in_month = ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) ? 29 : 28;
			break;
		default:
			days_in_month = 31;
	}

	for (int i = 0; i < (weekday + days_in_month); i++) {
		if (i < weekday)
			printf(" ");
		else
			printf("%2d%s", i - weekday + 1, (i + 1) % 7 ? " " : "\n");
	}
}

void calendar(int year) {
	for (int month = 1; month <= 12; month++) {
		month(year, month);
	}
}

int main() {
	int year = 2024;
	calendar(year);
	return 0;
}
