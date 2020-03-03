Utilizar funções de manipulação de cadeias fornecidas na biblioteca padrão (String.h)
---
A movimentação de valores de/para as cadeias de caracteres não pode ser efetuadas diretamente pelo comando de atribuição, ou pode ser efetuada pela movimentação caracter a caracter como em vetores ou através de funções de manipulação de cadeias de caracteres. Estas funções estão no cabeçalho do arquivo <b><string.h></b>: 

<b>#include <string.h></b>

Nesse momento, apresentaremos apenas as funções mais importantes de manipulação de Strings.

+ Mover caracteres para uma variável string. 

<p>A movimentação pode ser efetuada caracter a caracter (como em um vetor) ou através da função strcpy (string copy).</p>
<p><b>char *strcpy (const char *dest,const char *src)</b> - Copia uma string de <b>src</b> para outra string <b>dest</b>.</p>
<p>Exemplo de movimentação manual e através da função strcpy.</p>


``` C runnable
#include<string.h>
#include<stdio.h>
int main() {
  char origem[16] = {'T', 'E', 'S','T','E',' ', 'D','E', ' ', 'S','T','R','I','N','G','\0'};
  char destino[16];
  int i;
  /* Movimentação Manual */
  for (i= 0; i < 16; i++) {
     destino[i] = origem[i];
  }
  printf("\nManual\nOrigem = %s\n\nDestino = %s", origem, destino);

  /*Movimentação com Strcpy*/
  strcpy(destino, origem);
   printf("\n\nCom Funcao\nOrigem = %s\n\nDestino = %s", origem, destino);
}

```
+ Comparação de Strings.
<p>A comparação pode ser efetuada caracter a caracter (como em um vetor) ou através da função strcmp (string compare).</p>

<p><b>int strcmp(const char *string1,const char *string2)</b> - Compara duas strings (string1 e string2) e determina a ordem (alfabetica) das duas.</p>

```
  Usamos os códigos dos caracteres para determinar precedência
  Retorno:
  Se s1 preceder s2 -> -1
  Se s2 preceder s1 ->  1
  Se s1 igual a s2  ->  0
```
<p>Exemplo de comparação manual e através da função strcmp.</p>


``` C runnable
#include<string.h>
#include<stdio.h>
int compara(char s1[],char s2[]) {
    int i;
 for (i=0; s1[i] != '\0' && s2[i] != '\0'; i++) { // teste do for fica falso quando uma das strings chegar ao fim, ou pelo return
     if (s1[i] < s2[i])
        return -1;
     else
       if (s1[i] > s2[i])
          return 1;
   }
 //strings iguais
return 0;

}
int main() {
  char str1[16] = {'T', 'E', 'S','T','E',' ', 'D','E', ' ', 'S','T','R','I','N','G','\0'};
  char str2[16] = {'S', 'T', 'R','I','N','G', ' ', 'D','E', ' ', 'T','E','S','T','E','\0'};
  char str3[16] = {'T', 'E', 'S','T','E',' ', 'D','E', ' ', 'S','T','R','I','N','G','\0'};
  int retorno;
  int i;
  /* Comparação Manual */
  retorno = compara(str1,str2);
  printf("\n\nretorno= %d", retorno);
  if (retorno == 1)
     printf("\nstr1 > str2");
  else
     if (retorno == -1)
       printf("\nstr1 < str2");
      else
        printf("\nstr1 = str2");

  /*Comparação com Strcmp*/
   retorno=strcmp(str1, str3);
   printf("\n\nretorno= %d", retorno);


}

```

+ Tamanho da cadeia de caracteres
<p>Informa a quantidade de caracteres (tamanho) em uma cadeia de caracteres, excetuando o caracter de fim da string('\0').</p>
   <p><b>int strlen(const char *string)</b> - Retorna o tamanho de uma string.</p>
<p>Exemplo de Tamanho de String.</p>

``` C runnable
#include<string.h>
#include<stdio.h>
int main() {
  char str1[] = {'Q', 'U', 'A','L',' ','E', 'O', ' ','M','E','U',' ','T','A','M','A','N','H','O','\0'};
  char str2[] = {'E',' ','A',' ', 'M','I','N','H','A', ' ','S', 'T', 'R','I','N','G','\0'};
  char str3[] = {'T', 'E', 'S','T','E',' ', 'D','E', ' ', 'S','T','R','I','N','G','\0'};
  int tam1, tam2, tam3;

  tam1 = strlen(str1);
  printf("\n\nTamanho da String 1= %d", tam1);
  tam2 = strlen(str2);
  printf("\n\nTamanho da String 2= %d", tam2);
  tam3 = strlen(str3);
  printf("\n\nTamanho da String 3= %d", tam3);

}

```
+ União (Concatenção) da cadeia de caracteres
<p>Concatena (une) caracteres de duas cadeias de caracteres em uma string.</p>
   <p><b>char *strcat(const char *string1, char *string2)</b> - Concatena os caracteres da string2 na string1.</p>
<p>Exemplo de Concatenação de Strings.</p>

``` C runnable
#include<string.h>
#include<stdio.h>
int main() {
  char str1[22] = {'Q', 'U', 'A', 'L',' ','E',' ','\0'};
  char str2[15] = {'A',' ', 'M','I','N','H','A', ' ','S', 'T', 'R','I','N','G','\0'};

  printf("\n\nString 1= %s\n\nString2 =%s", str1,str2);
  strcat(str1,str2);
  printf("\n\nNova String 1= %s", str1);

}

```

