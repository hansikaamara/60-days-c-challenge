#include <stdio.h>

int main() {
    int choice;
    double balance = 10000.0;
    double amount;

    do {
       
        printf("Mini Banking System Menu:\n");
        printf("1. Deposit Money\n");
        printf("2. Withdraw Money\n");
        printf("3. Check Balance\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                printf("Enter amount to deposit: ₹");
                scanf("%lf", &amount);
                if (amount <= 0) {
                    printf("Deposit amount must be positive.\n");
                } else {
                    
                    if (amount > 25000) {
                        double bonus = amount * 0.01;
                        amount += bonus;
                        printf("1%% bonus of ₹%.2lf applied.\n", bonus);
                    }
                   
                    balance += amount;
                    balance -= 5;
                    printf("Deposit successful. ₹5 service charge applied.\n");
                }
                break;

            case 2: 
                printf("Enter amount to withdraw: ₹");
                scanf("%lf", &amount);
                if (amount <= 0) {
                    printf("Withdrawal amount must be positive.\n");
                } else if (amount > balance) {
                    printf("Warning: Insufficient balance. Withdrawal denied.\n");
                } else {
                    balance -= amount;
                    balance -= 5; 
                    printf("Withdrawal successful. ₹5 service charge applied.\n");
                }
                break;

            case 3: 
                printf("Current balance: ₹%.2lf\n", balance);
                break;

            case 4:
                printf("Exiting program. Thank you!\n");
                break;

            default:
                printf("Invalid choice. Please enter 1-4.\n");
        }
    } while (choice != 4);

    return 0;
}
