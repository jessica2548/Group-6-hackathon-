#include <stdio.h>

int main()
{
    char stops[5][30] = {
        "Main Gate",
        "Kandoli",
        "Prem Nagar",
        "Nanda Ki Chowki",
        "Clock Tower"};

    float fareTable[5][5] = {
        {0.0, 10.0, 20.0, 25.0, 40.0},
        {10.0, 0.0, 12.0, 18.0, 35.0},
        {20.0, 12.0, 0.0, 10.0, 25.0},
        {25.0, 18.0, 10.0, 0.0, 15.0},
        {40.0, 35.0, 25.0, 15.0, 0.0}};

    int boarding, destination, isStudent;
    float baseFare, concession = 0.0, finalFare;

    printf("=== Campus Shuttle Stops ===\n");
    for (int i = 0; i < 5; i++)
    {
        printf("%d. %s (From Main Gate: %.2f)\n", i + 1, stops[i], fareTable[0][i]);
    }

    printf("\nEnter boarding stop (1-5): ");
    scanf("%d", &boarding);

    printf("Enter destination stop (1-5): ");
    scanf("%d", &destination);

    if (boarding < 1 || boarding > 5 || destination < 1 || destination > 5)
    {
        printf("Invalid stop! Please enter numbers between 1 and 5.\n");
        return 0;
    }

    if (boarding == destination)
    {
        printf("Boarding and destination cannot be the same stop!\n");
        return 0;
    }

    printf("Student concession? (1 for Yes, 0 for No): ");
    scanf("%d", &isStudent);

    baseFare = fareTable[boarding - 1][destination - 1];

    if (isStudent == 1)
    {
        concession = baseFare * 0.20;
    }
    else if (isStudent != 0)
    {
        printf("Invalid choice for student concession! Enter 1 or 0.\n");
        return 0;
    }

    finalFare = baseFare - concession;

    printf("\n--- Journey Summary ---\n");
    printf("From       : %s\n", stops[boarding - 1]);
    printf("To         : %s\n", stops[destination - 1]);
    printf("Base Fare  : %.2f\n", baseFare);
    printf("Concession : %.2f\n", concession);
    printf("Final Fare : %.2f\n", finalFare);
    printf("-----------------------\n");

    return 0;
}
