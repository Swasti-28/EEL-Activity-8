# EEL-Activity-8
#include <stdio.h>

int strLen(char s[]) {
    int i = 0; while (s[i] != '\0') i++; return i;
}

int strCmp(char a[], char b[]) {
    int i = 0;
    while (a[i] != '\0' || b[i] != '\0') {
        if (a[i] != b[i]) return 0;
        i++;
    }
    return 1;
}

void strCopy(char d[], char s[]) {
    int i = 0;
    while (s[i] != '\0') { d[i] = s[i]; i++; }
    d[i] = '\0';
}

void strConcat(char d[], char a[], char b[]) {
    int i = 0, j = 0;
    while (a[j] != '\0') d[i++] = a[j++];
    j = 0;
    while (b[j] != '\0') d[i++] = b[j++];
    d[i] = '\0';
}

int main() {
    char reg[40], name[40], movie[40];
    char ticket[150], temp[150];

    printf("Registered name: "); scanf("%s", reg);
    printf("Enter your name: "); scanf("%s", name);

    if (!strCmp(reg, name)) {
        printf("Name mismatch! Entry denied.\n");
        return 0;
    }

    printf("Enter movie title (no spaces): ");
    scanf("%s", movie);

    int len = strLen(movie);
    if (len < 2 || len > 30) {
        printf("Invalid title length!\n");
        return 0;
    }

    strCopy(ticket, "Name: ");
    strConcat(ticket, ticket, name);

    strCopy(temp, " | Movie: ");
    strConcat(ticket, ticket, temp);
    strConcat(ticket, ticket, movie);

    strConcat(ticket, ticket, " | Time: 7PM | Seat: A12");

    printf("\n--- FINAL TICKET ---\n%s\nEntry Granted!\n", ticket);
    return 0;
}
