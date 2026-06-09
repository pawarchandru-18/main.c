# main.c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define ROWS 30
#define COLS 60

char canvas[ROWS][COLS];

/* Function Prototypes */
void initializeCanvas();
void displayCanvas();
void setPixel(int x, int y, char ch);
void drawRectangle(int x, int y, int width, int height, char ch);
void drawLine(int x1, int y1, int x2, int y2, char ch);
void drawTriangle(int x1, int y1, int x2, int y2, int x3, int y3, char ch);
void drawCircle(int xc, int yc, int r, char ch);

int main()
{
    int choice;

    initializeCanvas();

    while (1)
    {
        printf("\n===== 2D Graphics Editor =====\n");
        printf("1. Draw Rectangle\n");
        printf("2. Draw Line\n");
        printf("3. Draw Triangle\n");
        printf("4. Draw Circle\n");
        printf("5. Delete Rectangle\n");
        printf("6. Delete Line\n");
        printf("7. Delete Triangle\n");
        printf("8. Delete Circle\n");
        printf("9. Display Canvas\n");
        printf("10. Clear Canvas\n");
        printf("0. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        int x, y, w, h;
        int x1, y1, x2, y2, x3, y3;
        int r;

        switch (choice)
        {
        case 1:
            printf("Enter x y width height: ");
            scanf("%d%d%d%d", &x, &y, &w, &h);
            drawRectangle(x, y, w, h, '*');
            break;

        case 2:
            printf("Enter x1 y1 x2 y2: ");
            scanf("%d%d%d%d", &x1, &y1, &x2, &y2);
            drawLine(x1, y1, x2, y2, '*');
            break;

        case 3:
            printf("Enter x1 y1 x2 y2 x3 y3: ");
            scanf("%d%d%d%d%d%d",
                  &x1, &y1, &x2, &y2, &x3, &y3);
            drawTriangle(x1, y1, x2, y2, x3, y3, '*');
            break;

        case 4:
            printf("Enter center x y and radius: ");
            scanf("%d%d%d", &x, &y, &r);
            drawCircle(x, y, r, '*');
            break;

        case 5:
            printf("Enter x y width height: ");
            scanf("%d%d%d%d", &x, &y, &w, &h);
            drawRectangle(x, y, w, h, '_');
            break;

        case 6:
            printf("Enter x1 y1 x2 y2: ");
            scanf("%d%d%d%d", &x1, &y1, &x2, &y2);
            drawLine(x1, y1, x2, y2, '_');
            break;

        case 7:
            printf("Enter x1 y1 x2 y2 x3 y3: ");
            scanf("%d%d%d%d%d%d",
                  &x1, &y1, &x2, &y2, &x3, &y3);
            drawTriangle(x1, y1, x2, y2, x3, y3, '_');
            break;

        case 8:
            printf("Enter center x y and radius: ");
            scanf("%d%d%d", &x, &y, &r);
            drawCircle(x, y, r, '_');
            break;

        case 9:
            displayCanvas();
            break;

        case 10:
            initializeCanvas();
            printf("Canvas Cleared!\n");
            break;

        case 0:
            exit(0);

        default:
            printf("Invalid Choice!\n");
        }
    }

    return 0;
}

/* Initialize Canvas */
void initializeCanvas()
{
    int i, j;

    for (i = 0; i < ROWS; i++)
    {
        for (j = 0; j < COLS; j++)
        {
            canvas[i][j] = '_';
        }
    }
}

/* Display Canvas */
void displayCanvas()
{
    int i, j;

    printf("\n");
    for (i = 0; i < ROWS; i++)
    {
        for (j = 0; j < COLS; j++)
        {
            printf("%c", canvas[i][j]);
        }
        printf("\n");
    }
}

/* Set Pixel */
void setPixel(int x, int y, char ch)
{
