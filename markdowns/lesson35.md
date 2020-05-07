# Praticando Ponteiros e Funções
---
?[Assinale a alternativa correta com relação ao estudo de Ponteiros?] [single]
-[ ] Ponteiro é o valor de uma variável 
-[ ] Ponteiro é o indicador da próxima variável a ser passada
-[x] Ponteiro é uma variável que armazena endereço
-[ ] Ponteiro é o endereço que aponta para uma variável

?[Quais das seguintes instruções declaram um ponteiro para uma variável float?]
-[x] float *p; 
-[ ] float p;
-[ ] *float p;
-[ ] float p*;

```C
int x, y, *p;
y = 0;
p = &y;
x = *p;
x = 4;
(*p)++;
--x;
(*p) += x;
printf("x=%d  y=%d *p=%d", x, y, *p);
```
?[Seja o trecho de código acima, quais serão os valores de x, y e *p no comando printf?]
-[ ] x = 4  y = 0 *p = 4
-[ ] x = 3  y = 3 *p = 3
-[ ] x = -1 y = 0 *p = 0
-[x] x = 3  y = 4 *p = 4

```C
int a=5, b=12, c;
int *p;
int *q;
p = &a;
q = &b;
c = *p + *q;
printf("c = %d", c);
```
?[Seja o trecho de código acima, que valor de c será impresso no comando printf?]
-[ ] c = 5  
-[x] c = 17  
-[ ] c = 12 
-[ ] c = 7

---
Exercício 1
---
Faça um programa que modifique as vogais de uma frase. O programa deve ler uma frase (max. 100 caracteres) e armazeá-la num vetor. Imprimir a frase lida trocando as vogais, isto é, trocar 'a' pelo 'u',  'e' pelo 'o', 'i' pelo 'u', 'o' pelo 'a' e o 'u' pelo 'e'. Usar uma função void (procedimento) para realizar a troca e uma função para realizar a impressão da frase trocada. A função deve ter como parâmetro um ponteiro char referente ao vetor. Dica: Use a função <b>gets()</b> da biblioteca string.h para realizar a leitura da frase. use o switch para realizar as trocas. Só considere as letras minúsculas.


@[IDE]({"stubs": ["./www/exercicio"],"command": "sh /project/target/www/exercicio1.sh"
})


::: Solução

``` C
#include<stdio.h>
#include<string.h>
void troca(char *vet) {
int i, tam;
 
tam = strlen(vet);
for (i=0; i < tam; i++) {
 switch(*vet) {
    case 'a':
    *vet = 'u';
     break;
    case 'e':
     *vet='o';
      break;
    case 'i':
      *vet='u';
      break;
    case 'o':
      *vet='a';
      break;
    case 'u':
      *vet='e';
      break;
 }
vet++;
}

}
void imprime(char *vet) {
int i;
char *ptr;
ptr = vet;
printf("\n\n");
for (i=0; i < strlen(vet); i++) {
 printf("%c", *ptr);
 ptr++;
}
}
int main(){
char vet[100];

printf("\n\nDigite uma frase: ");
gets(vet);
troca(vet);
imprime(vet);
}

```
:::
---
Exercício 2
---

Escreva um programa que declare uma matriz 10x10 de inteiros. Você criar uma função void (procedimento) para inicializar a matriz com zeros usando um ponteiro para a matriz. Faça outra função void para preencher depois a matriz com os números de 99 a 0, também usando ponteiro para matriz como parâmetro. Por fim, o programa deve imprimir a matriz.

@[IDE]({"stubs": ["./www/exercicio"],"command": "sh /project/target/www/exercicio1.sh"
})


::: Solução

``` C
#include<stdio.h>
#include<string.h>
void inicializa(int *mat) {
int i;

for(i=0; i < 100; i++) {
  *mat=0;
  mat++;
}
}
void preenche(int *mat) {
int i;

for(i=0; i < 100; i++) {
  *mat=99 - i;
  mat++;
}
}
int main() {
int matriz[10][10];
int i, j;

inicializa(matriz);
preenche(matriz);
for(i=0; i< 10; i++){
 printf("\n");
 for (j=0; j < 10; j++)
   printf("mat[%d][%d]= %d ", i,j,matriz[i][j]);
}
}

```
:::
---
Exercício 3
---

Faça um programa para calcular a área e o perímetro de um hexágono. O programa deve implementar uma função chamada calc_hexa que calcula a área e o perímetro de um hexágono regular de lado L. O program deve solicitar ao usuário o lado do polígono, calcular e imprimir a área e o perímetro do polígono. O programa termina quando for digitado um valor negativo qualquer para o lado. A função deve obedecer o seguinte protótipo:
<p><b>void calc_hexa(float l, floar *area, float *perimetro);</b></p>
Lembrando que a área e o perímetro de um hexágono regular são dados por:

 $`area=\frac{3×L^2×\sqrt{3}}{2}`$     </br></br>                $`perimetro = {6×L}`$ 

Para os cálculos, obrigatoriamente você deve utilizar as funções <b>sqrt</b> e <b>pow</b> da biblioteca <b>math.h</b>.


@[IDE]({"stubs": ["./www/exercicio"],"command": "sh /project/target/www/exercicio1.sh"
})


::: Solução

``` C
#include<stdio.h>
#include<math.h>
void calc_hexa(float l, float *area, float *per) {

*per = 6 * l;
*area = (3 * pow(l,2) * sqrt(3))/2;
}

int main(){
 float lado, area, perimetro;

 printf("\n\nDigite o lado do hexagono:");
 scanf("%f", &lado);
 while (lado > 0) {
  calc_hexa(lado, &area, &perimetro);
  printf("\n\na area e o perímetro do hexagono regular de lado %f e igual a %f  e  %f", lado, area, perimetro);

  printf("\n\nDigite o lado do hexagono:");
  scanf("%f", &lado);

 }
}
```
:::
---
