# EEL-Activity-8
#include <stdio.h>

// simple copy
void strCopy(char d[], char s[]) {
    int i = 0;
    while (s[i] != '\0') {
        d[i] = s[i];
        i++;
    }
    d[i] = '\0';
}

// simple concatenation (add s at end of d)
void strConcat(char d[], char s[]) {
    int i = 0, j = 0;

    while (d[i] != '\0')   // move to end of d
        i++;

    while (s[j] != '\0')   // copy s after it
        d[i++] = s[j++];

    d[i] = '\0';           // close final string
}

// simple compare (1 = same, 0 = different)
int strCmp(char a[], char b[]) {
    int i = 0;
    while (a[i] != '\0' || b[i] != '\0') {
        if (a[i] != b[i]) return 0;
        i++;
    }
    return 1;
}

int main() {
    char reg[40], name[40], movie[40];
    char ticket[200];
    FILE *f;

    printf("Registered name: ");
    scanf("%s", reg);

    printf("Enter your name: ");
    scanf("%s", name);

    if (!strCmp(reg, name)) {
        printf("Name mismatch! Entry denied.\n");
        return 0;
    }

    printf("Enter movie title (no spaces): ");
    scanf("%s", movie);

    // build ticket using only strCopy + strConcat
    strCopy(ticket, "Name: ");
    strConcat(ticket, name);
    strConcat(ticket, " | Movie: ");
    strConcat(ticket, movie);
    strConcat(ticket, " | Time: 7PM | Seat: A12");

    // write to file
    f = fopen("ticket.txt", "w");
    fprintf(f, "%s", ticket);
    fclose(f);

    // read file
    f = fopen("ticket.txt", "r");
    fscanf(f, "%[^\n]", ticket);
    fclose(f);

    printf("\n--- FINAL TICKET ---\n%s\nEntry Granted!\n", ticket);

    return 0;
}



