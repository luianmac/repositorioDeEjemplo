# repositorioDeEjemplo
es solo un repsitorio de prueba.
#include <stdio.h>
#define MAXLINE 1000 /* maximum input line length */
int getline2(char line[], int maxline);
void copy(char to[], char from[]);
int cuenta(char cadena[]);
int cuenta_digitos(char cadena[]);
/* print the longest input line */
int main()
{
    int len; /* current line length */
    int max; /* maximum length seen so far */
    char line[MAXLINE]; /* current input line */
    char longest[MAXLINE]; /* longest line saved here */
    char opcion;
    int n;

    max = 0;
    while ((len = getline2(line, MAXLINE)) > 0)
        if (len > max) {
            max = len;
            copy(longest, line);
        }

    /*menu*/
    do
    {
        printf( "\n   1. Contar caracteres" );
        printf( "\n   2. Contar digitos    ");
        printf( "\n   3. Salir."            );

        do
        {
            printf( "\n   Introduzca opcion (1-3): ");//borre 162
            fflush( stdin );
            scanf( "%c", &opcion );

        } while ( opcion < '1' || opcion > '3' );

        switch ( opcion )
        {
            case '1': if (max > 0) /* there was a line */
                      printf("La cadena mas larga es: %s", longest);
                      printf("La cadena tiene %d caracteres\n", cuenta(longest)-1);
                      break;

            case '2': if (max > 0) /* there was a line */
                      printf("La cadena mas larga es: %s", longest);
                      printf("La cadena tiene %d dígitos\n", cuenta_digitos(longest));
                      break;
         }

    } while ( opcion != '3' );

    return 0;
}

/* getline2: read a line into s, return length */
int getline2(char s[],int lim)
{
    int c, i;
    for (i=0; i < lim-1 && (c=getchar())!=EOF && c!='\n'; ++i)
        s[i] = c;
    if (c == '\n') {
        s[i] = c;
        ++i;
    }
    s[i] = '\0';
    return i;
}

/* copy: copy 'from' into 'to'; assume to is big enough */
void copy(char to[], char from[])
{
    int i;
    i = 0;
    while ((to[i] = from[i]) != '\0')
        ++i;
}

/* cuenta: cuenta los caracteres de la cadena seleccionada */
int cuenta(char cadena[])
{
    int i;
    i = 0;
    while (cadena[i] != '\0')
        ++i;
    return i;
}

/* cuenta_digitos: cuenta los digitos de la cadena seleccionada */
int cuenta_digitos(char cadena[])
{
    int i, digitos;
    i = 0;
    digitos = 0;
    while (cadena[i] != '\0')
    {
        if (cadena[i] >= '0' && cadena[i] <= '9')
            ++digitos;
        ++i;
    }
    return digitos;
}
