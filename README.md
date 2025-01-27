// password-strength-checker
#include <stdio.h>
#include <string.h>


int checkPasswordStrength(char *password) {
    int length = strlen(password);
    int Upper = 0,Lower = 0,Digit = 0,Special = 0;
    
    
    if (length < 8) {
        return 0; 
    }
    
   
    for (int i = 0; i < length; i++) {
        if (isupper(password[i])) {
            Upper = 1;
        } else if (islower(password[i])) {
            Lower = 1;
        } else if (isdigit(password[i])) {
            Digit = 1;
        } else if (ispunct(password[i])) {
            Special = 1;
        }
    }
    
    
    if (Upper && Lower && Digit && Special) {
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
