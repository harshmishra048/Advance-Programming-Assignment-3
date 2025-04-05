# Advance-Programming-Assignment-3
It is a assignment of Advance Programming 


                         Assignment Start From Here
                         
import java.util.Scanner;

public class TravelBooking {

    static String[] flights = {
        "AI101 - Satna to Rewa - 10:00 AM",
        "AI202 - Satna to Maihar - 1:00 PM",
        "AI303 - Maihar to Satna - 3:30 PM",
        "AI404 - Rewa to Satna - 6:00 PM"
    };

    static boolean[] bookedFlights = new boolean[flights.length];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n--- Travel Booking System ---");
            System.out.println("1. View Available Flights");
            System.out.println("2. Book a Flight");
            System.out.println("3. Cancel a Flight");
            System.out.println("4. Exit");
            System.out.print("Enter your choice (1-4): ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    viewFlights();
                    break;
                case 2:
                    bookFlight(scanner);
                    break;
                case 3:
                    cancelFlight(scanner);
                    break;
                case 4:
                    System.out.println("Thank you for using the Travel Booking System.");
                    break;
                default:
                    System.out.println("Invalid choice. Please enter 1-4.");
            }
        } while (choice != 4);

        scanner.close();
    }

    public static void viewFlights() {
        System.out.println("\nAvailable Flights:");
        for (int i = 0; i < flights.length; i++) {
            String status = bookedFlights[i] ? "[Booked]" : "[Available]";
            System.out.println((i + 1) + ". " + flights[i] + " " + status);
        }
    }

    public static void bookFlight(Scanner scanner) {
        viewFlights();
        System.out.print("Enter the flight number to book (1-" + flights.length + "): ");
        int flightNo = scanner.nextInt();

        if (flightNo >= 1 && flightNo <= flights.length) {
            if (!bookedFlights[flightNo - 1]) {
                bookedFlights[flightNo - 1] = true;
                System.out.println("Successfully booked: " + flights[flightNo - 1]);
            } else {
                System.out.println("This flight is already booked.");
            }
        } else {
            System.out.println("Invalid flight number.");
        }
    }

    public static void cancelFlight(Scanner scanner) {
        viewFlights();
        System.out.print("Enter the flight number to cancel (1-" + flights.length + "): ");
        int flightNo = scanner.nextInt();

        if (flightNo >= 1 && flightNo <= flights.length) {
            if (bookedFlights[flightNo - 1]) {
                bookedFlights[flightNo - 1] = false;
                System.out.println("Successfully cancelled: " + flights[flightNo - 1]);
            } else {
                System.out.println("This flight was not booked.");
            }
        } else {
            System.out.println("Invalid flight number.");
        }
    }
}
