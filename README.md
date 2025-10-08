#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char w[50];
    char word[50];
    FILE *f = fopen("data1.txt", "r");
     if (f == NULL){
        printf("error");
        exit(1);
    }
    printf("write the word that u want to count his occurrence: ");
    scanf("%s", word);
    int count = 0;
    while (fscanf(f, "%99s", w) == 1) {
        char *pos = w;

        // Find every occurrence inside the current word
        while ((pos = strstr(pos, word)) != NULL) {
            count++;
            pos++;  // move forward by 1 to catch overlapping cases too
        }
    }
    printf("The word '%s' appears %d times (including inside other words and overlaps)\n", word, count);
    fclose(f);
    return 0;

}

