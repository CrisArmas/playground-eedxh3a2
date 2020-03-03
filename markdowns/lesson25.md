# Cadeia de caracteres (ou string)

+ Uma cadeia de caracteres (string em inglês) é uma sequência de caracteres ou símbolos definida pelo código ASCII. 

+ Em linguagem C, uma cadeia de caracteres pode ser tratada como um "Vetor" do tipo char, cujo último elemento é o caractere nulo '\0', ou seja, o primeiro caractere do código ASCII (cujo valor é 0). 

+ O caractere nulo é um caractere de controle (ou seja, não exibível) que indica o fim de uma cadeia de caracteres. Assim, uma cadeia composta de n elementos será, na realidade, um vetor de n + 1 elementos do tipo char. 

+ Podemos, por exemplo, representar a string "Ola Mundo!" da seguinte maneira: 
![programa](/markdowns/olamundo.gif)

---
Declaração de Cadeias de caracteres
---
A declaração de uma string em C é semelhante a declaração de um  vetor do tipo char. O número máximo de caracteres que comportará a cadeia será igual ao número de elementos do vetor menos um (reservado para o caractere do final da cadeia), por exemplo, se definirmos uma cadeia de caracteres de tamanho 30, ela conterá 29 caracteres + '\0'. 

```
char Nome_da_tabela[Número_de_elementos]
```
---
Inicialização de cadeia de caracteres
---
+ A inicialização de uma string, ou seja, mover caracteres, pode ser feita de duas maneiras:

  + Mover manualmente os dados (célula por célula), como em um vetor ou
  + Utilizar funções de manipulação de cadeias fornecidas pela biblioteca padrão (String.h).

Exemplo de inicialização manual de cadeia de caracteres (para impressão de cadeia de caracteres com o comando <b>printf</b> devemos utilizar o caracter formatação <b>"%s"</b> : 
``` C runnable
#include <stdio.h> 
int main(){ 
 char Cadeia[12]; 
 Cadeia[0]= 'L'; 
 Cadeia[1]= 'i'; 
 Cadeia[2]= 'n'; 
 Cadeia[3]= 'g'; 
 Cadeia[4]= 'u'; 
 Cadeia[5]= 'a'; 
 Cadeia[6]= 'g'; 
 Cadeia[7]= 'e';
 Cadeia[8]= 'm';
 Cadeia[9]= ' ';
 Cadeia[10]= 'C';
 Cadeia[11]= '\0'; 
 
 printf("%s",Cadeia);
 }
```

Outra maneira (mais simples) de inicializarmos uma cadeia de caracteres é na sua declaração, como no exmplo abaixo: 
``` C runnable
#include <stdio.h> 
int main(){ 
 char Cadeia[12] = {'L', 'i', 'n', 'g', 'u', 'a', 'g', 'e', 'm', ' ', 'C', '\0'}; 
 
 printf("%s",Cadeia);
 }
```

---
ATENÇÃO
---
O comando <b>scanf</b> não lê o caracter <b>Enter('\0')</b>, portanto em variáveis do <b>tipo char</b> esse caracter é lido no comando <b>scanf</b> seguinte. Logo, em comandos de leitura de variáveis do tipo char, coloque a função <b>getchar()</b> ou <b>fflush(stdin)</b> *(biblioteca stdlib.h)* após o commando <b>scanf</b>, para solucionar o problema. A função <b>fflush(stdin)</b> limpa o buffer do teclado. Veja o exemplo abaixo:
```C
#include<stdio.h>
int main(){
char vet[10];
int i;

for (i=0; i<10;i++){
    printf("\nentra:");
    scanf("%c",&vet[i]);
    fflush(stdin); //Usar essa função ou a função getchar()
}
for (i=0; i<10;i++){
    printf("\nvet=:%c", vet[i]);

}

}

```
