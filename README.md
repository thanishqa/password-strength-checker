// password-strength-checker
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int checkPasswordStrength(char *password) {
    int length = strlen(password);
    int hasUpper = 0, hasLower = 0, hasDigit = 0, hasSpecial = 0;
    
    
    if (length < 8) {
        return 0; 
    }
    
   
    for (int i = 0; i < length; i++) {
        if (isupper(password[i])) {
            hasUpper = 1;
        } else if (islower(password[i])) {
            hasLower = 1;
        } else if (isdigit(password[i])) {
            hasDigit = 1;
        } else if (ispunct(password[i])) {
            hasSpecial = 1;
        }
    }
    
    
    if (hasUpper && hasLower && hasDigit && hasSpecial) {
        return 1;  
    }
    
    return 0;  
}

int main() {
    char password[100];
    
    printf("Enter your password: ");
    scanf("%s", password);
    
   
    if (checkPasswordStrength(password)) {
        printf("Password is strong!\n");
    } else {
        printf("Password is weak. Make sure it's at least 8 characters long, contains:\n");
        printf("- At least one uppercase letter\n");
        printf("- At least one lowercase letter\n");
        printf("- At least one digit\n");
        printf("- At least one special character\n");
    }
    
    return 0;
} 
