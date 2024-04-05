// acp-code
//Number system converter : convert between binary ,decimal,hexadecimal
#include <stdio.h>

int main() {
    int choice;

    printf("Number System Converter\n");
    printf("1. Decimal to Binary\n");
    printf("2. Binary to Decimal\n");
    printf("3. Decimal to Hexadecimal\n");
    printf("4. Hexadecimal to Decimal\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    switch (choice) {
        case 1: {
            int decimal;
            long long binary = 0;
            int remainder, i = 1;

            printf("Enter a decimal number: ");
            scanf("%d", &decimal);

            printf("Binary: ");
            while (decimal != 0) {
                remainder = decimal % 2;
                decimal /= 2;
                binary += remainder * i;
                i *= 10;
            }
            printf("%lld\n", binary);
            break;
        }
        case 2: {
            long long binary;
            int decimal = 0, i = 0, remainder;

            printf("Enter a binary number: ");
            scanf("%lld", &binary);

            while (binary != 0) {
                remainder = binary % 10;
                binary /= 10;
                decimal += remainder * (1 << i);
                ++i;
            }

            printf("Decimal: %d\n", decimal);
            break;
        }
        case 3: {
            int decimal;
            char hexadecimal[20];
            int i = 0, remainder;

            printf("Enter a decimal number: ");
            scanf("%d", &decimal);

            printf("Hexadecimal: ");
            while (decimal != 0) {
                remainder = decimal % 16;
                if (remainder < 10)
                    hexadecimal[i++] = remainder + 48;
                else
                    hexadecimal[i++] = remainder + 55;
                decimal /= 16;
            }
            for (int j = i - 1; j >= 0; --j)
                printf("%c", hexadecimal[j]);
            printf("\n");
            break;
        }
        case 4: {
            char hexadecimal[20];
            int decimal = 0, i = 0, val, len;

            printf("Enter a hexadecimal number: ");
            scanf("%s", hexadecimal);

            while (hexadecimal[i] != '\0')
                ++i;
            len = i;

            for (i = 0; hexadecimal[i] != '\0'; ++i) {
                if (hexadecimal[i] >= '0' && hexadecimal[i] <= '9')
                    val = hexadecimal[i] - 48;
                else if (hexadecimal[i] >= 'A' && hexadecimal[i] <= 'F')
                    val = hexadecimal[i] - 55;
                else if (hexadecimal[i] >= 'a' && hexadecimal[i] <= 'f')
                    val = hexadecimal[i] - 87;
                decimal += val * (1 << (4 * (len - 1 - i)));
            }

            printf("Decimal: %d\n", decimal);
            break;
        }
        default:
            printf("Invalid choice\n");
    }

    return 0;
}

