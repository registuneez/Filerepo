# my name is regis
🔸I'm student in dreamize Africa 
📍 I'm in Rwanda 🌍


🔸I'm one who build big thing in future 
🔸a computer 👨‍💻 is my heart beat 
🔺ask me something you need 
🔹work with me 
🔹call me ☎️ regis


#include <stdio.h>
#include <stdlib.h>

#define MAX_TRAINS 5
#define MAX_SEATS 10

// Structure to represent a train
struct Train {
    int train_id;
    char train_name[50];
    int available_seats;
};

// Declare an array of trains
struct Train trains[MAX_TRAINS];

// Function to initialize train data
void initializeTrains() {
    for (int i = 0; i < MAX_TRAINS; i++) {
        trains[i].train_id = i + 1;
        sprintf(trains[i].train_name, "Train-%d", i + 1);
        trains[i].available_seats = MAX_SEATS;
    }
}

// Function to display available trains
void displayTrains() {
    printf("\nAvailable Trains:\n");
    for (int i = 0; i < MAX_TRAINS; i++) {
        printf("Train ID: %d | Train Name: %s | Available Seats: %d\n", 
               trains[i].train_id, trains[i].train_name, trains[i].available_seats);
    }
}

// Function to book a ticket
void bookTicket() {
    int train_id, seats;
    printf("\nEnter Train ID to book ticket: ");
    scanf("%d", &train_id);
    
    if (train_id < 1 || train_id > MAX_TRAINS) {
        printf("Invalid Train ID.\n");
        return;
    }
    
    printf("Enter number of seats to book: ");
    scanf("%d", &seats);
    
    if (seats <= 0 || seats > trains[train_id - 1].available_seats) {
        printf("Not enough seats available.\n");
    } else {
        trains[train_id - 1].available_seats -= seats;
        printf("%d seats booked successfully on Train %d.\n", seats, train_id);
    }
}

// Function to cancel a ticket
void cancelTicket() {
    int train_id, seats;
    printf("\nEnter Train ID to cancel ticket: ");
    scanf("%d", &train_id);
    
    if (train_id < 1 || train_id > MAX_TRAINS) {
        printf("Invalid Train ID.\n");
        return;
    }
    
    printf("Enter number of seats to cancel: ");
    scanf("%d", &seats);
    
    if (seats <= 0 || seats > MAX_SEATS - trains[train_id - 1].available_seats) {
        printf("No such reservation found.\n");
    } else {
        trains[train_id - 1].available_seats += seats;
        printf("%d seats canceled successfully on Train %d.\n", seats, train_id);
    }
}

// Function to view current reservations
void viewReservations() {
    printf("\nCurrent Reservations:\n");
    for (int i = 0; i < MAX_TRAINS; i++) {
        printf("Train ID: %d | Train Name: %s | Reserved Seats: %d\n", 
               trains[i].train_id, trains[i].train_name, MAX_SEATS - trains[i].available_seats);
    }
}

int main() {
    int choice;
    initializeTrains();
    
    while (1) {
        printf("\nWelcome to Railway Reservation System\n");
        printf("1. View Available Trains\n");
        printf("2. Book a Ticket\n");
        printf("3. Cancel a Ticket\n");
        printf("4. View Reservations\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                displayTrains();
                break;
            case 2:
                bookTicket();
                break;
            case 3:
                cancelTicket();
                break;
            case 4:
                viewReservations();
                break;
            case 5:
                printf("Exiting system... Goodbye!\n");
                exit(0);
                break;
            default:
                printf("Invalid choice, please try again.\n");
        }
    }

    return 0;
}
