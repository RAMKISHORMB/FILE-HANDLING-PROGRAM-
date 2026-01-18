# FILE HANDLING PROGRAM 
File-Handling-C-Program/
│
├── file_handling.c
├── README.md
Create, Read, Write & Append (file_handling.c)!!
#include <stdio.h>
#include <stdlib.h>

void writeFile() {
    FILE *fp;
    char data[1000];

    fp = fopen("data.txt", "w");
    if (fp == NULL) {
        printf("Error opening file!\n");
        return;
    }

    printf("Enter data to write into file:\n");
    getchar(); // clear buffer
    fgets(data, sizeof(data), stdin);

    fprintf(fp, "%s", data);
    fclose(fp);

    printf("Data written successfully.\n");
}

void readFile() {
    FILE *fp;
    char ch;

    fp = fopen("data.txt", "r");
    if (fp == NULL) {
        printf("File not found!\n");
        return;
    }

    printf("\nFile contents:\n");
    while ((ch = fgetc(fp)) != EOF) {
        printf("%c", ch);
    }

    fclose(fp);
}

void appendFile() {
    FILE *fp;
    char data[1000];

    fp = fopen("data.txt", "a");
    if (fp == NULL) {
        printf("Error opening file!\n");
        return;
    }

    printf("Enter data to append:\n");
    getchar();
    fgets(data, sizeof(data), stdin);

    fprintf(fp, "%s", data);
    fclose(fp);

    printf("Data appended successfully.\n");
}

int main() {
    int choice;

    do {
        printf("\n--- FILE HANDLING MENU ---\n");
        printf("1. Write to file\n");
        printf("2. Read file\n");
        printf("3. Append to file\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                writeFile();
                break;
            case 2:
                readFile();
                break;
            case 3:
                appendFile();
                break;
            case 4:
                printf("Exiting program.\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 4);

    return 0;
}
