#include <stdio.h>
#include <string.h>

#define MAX_ENTRIES 100
#define PHONE_NUMBER_LENGTH 15
#define LOCATION_LENGTH 50

typedef struct {
    char phoneNumber[PHONE_NUMBER_LENGTH];
    char location[LOCATION_LENGTH];
} DirectoryEntry;

void displayDirectory(DirectoryEntry directory[], int count) {
    printf("Phone Directory:\n");
    for (int i = 0; i < count; i++) {
        printf("Phone Number: %s, Location: %s\n", directory[i].phoneNumber, directory[i].location);
    }
}

int main() {
    DirectoryEntry directory[MAX_ENTRIES] = {
        {"4624521125", "Pune"},
        {"4848181144", "mumbai"},
        {"1484818418", "navi mumbai"},
        {"1684184184", "nagpur"},
        {"9096980486", "nashik"},
    };
    int count = 5; 
    char inputPhoneNumber[PHONE_NUMBER_LENGTH];
    int choice;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Search for a phone number\n");
        printf("2. Display all entries\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter a phone number to search: ");
                scanf("%14s", inputPhoneNumber);
                int found = 0;
                for (int i = 0; i < count; i++) {
                    if (strcmp(directory[i].phoneNumber, inputPhoneNumber) == 0) {
                        printf("Phone Number: %s, Location: %s\n", directory[i].phoneNumber, directory[i].location);
                        found = 1;
                        break;
                    }
                }
                if (!found) {
                    printf("The phone number %s is not in the directory.\n", inputPhoneNumber);
                }
                break;

            case 2:
                displayDirectory(directory, count);
                break;

            case 3:
                printf("Exiting the program.\n");
                return 0;

            default:
                printf("Invalid choice. Please try again.\n");
                break;
        }
    }

    return 0;
}
