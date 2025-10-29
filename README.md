import java.time.DayOfWeek;
import java.time.LocalDate;
import java.util.Scanner;

public class MonthlyCalendar {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Taking input for year and month
        System.out.print("Enter year: ");
        int year = input.nextInt();
        System.out.print("Enter month (1-12): ");
        int month = input.nextInt();

        // Creating LocalDate for the first day of the given month
        LocalDate firstDay = LocalDate.of(year, month, 1);

        // Getting name of the month
        String monthName = firstDay.getMonth().toString().substring(0, 1).toUpperCase() +
                           firstDay.getMonth().toString().substring(1).toLowerCase();

        System.out.println("\nCalendar for the month of " + monthName + ", " + year);
        System.out.println("Su  Mo  Tu  We  Th  Fr  Sa");

        // Determine the day of week for the first day
        DayOfWeek dayOfWeek = firstDay.getDayOfWeek();
        int startDay = dayOfWeek.getValue(); // Monday=1 ... Sunday=7

        // Adjusting startDay to make Sunday=0
        startDay = (startDay == 7) ? 0 : startDay;

        // Printing spaces for the first week
        for (int i = 0; i < startDay; i++) {
            System.out.print("    ");
        }

        // Get number of days in the month
        int daysInMonth = firstDay.lengthOfMonth();

        // Printing days of the month
        for (int day = 1; day <= daysInMonth; day++) {
            System.out.printf("%2d  ", day);

            // Move to new line after Saturday
            if ((day + startDay) % 7 == 0) {
                System.out.println();
            }
        }

        System.out.println(); // final new line
        input.close();
    }
}
