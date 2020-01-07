Encadeamento de IF's  
----
A estrutura de decisão (condicional) ```IF``` permite, no máximo, duas possibilidades de execução dos comandos: uma possibilidade é a execução de comandos associados a condição <b>Verdadeira</b> e a outra possibilidade está associada a condição <b>Falsa</b>, como mostra o exemplo a seguir:
``` C
if(condição) {
  comandosA;     <----- Esses comandos só serão executados, se a condição for avaliada Verdadeira.
} 
else {
  comandosB;     <----- Esses comandos só serão executados, se a condição for avaliada Falsa.
}
```
Mas, existem situações em que temos mais de duas possibilidades (p.ex. menus com várias opções de escolha). Nesses casos nos vemos obrigados a arrumar a estrutura condicional para possibilitar a representação desses <b>"Caminhos"</b>. Estamos falando do "Encadeamento de if´s". O encadeamento de if´s possibilita uma representação da estrutura de if para tratar situações onde temos mais de 2 possibilidades.
``` C
if(condição1) {
  comandosA;       <----- Esses comandos só serão executados, se a condição1 for avaliada Verdadeira.
} 
else {
  if (condição2) { 
    comandosB;     <----- Esses comandos só serão executados, se a condição2 for avaliada Verdadeira.
  }
  else {
    if (condição3) {
      comandosC;    <----- Esses comandos só serão executados, se a condição3 for avaliada Verdadeira. 
    }  
    else{
      comandosD;    <----- Esses comandos só serão executados, se a todas as condições acima forem avaliadas Falsa.               
    }
  }      <-------- Fechamento do Segundo else   
} <-------- Fechamento do Terceiro else  
```
+ Podemos encadear quantos if´s forem necessários (no exemplo acima apresentamos apenas 3).
----
Exemplo
----
Faça um programa que calcule o desconto de uma compra efetuada obedecendo os seguintes percentuais: 
+ 10% de desconto se a compra for menor ou igual que R$2.000,00; 
+ 5% de desconto se a compra for maior que R$ 2.000,00 e menor ou igual a R$ 3.000,00;
+ 3% de desconto se for maior que R$ 3.000,00 e menor ou igual a R$ 5.000,00;
+ 2% de desconto para compras acima de R$ 5.000,00.
O programa deverá exibir o desconto e o total a pagar.
No exemplo abaixo modifique o valor da variável compra para avaliar as outras situações.
``` C runnable
#include<stdio.h>
int main() {
 float compras, desconto, taxa, totpagar;

 compras = 3000; /* Modifique o valor da variavel compras e teste outras condições*/
 
if(compras <= 2000) {
  taxa=0.1;       
} 
else {
  if (compras <= 3000) {  /* Nessa condição não é necessário por a condição de maior que 2000, pois nesse if já é maior que 2000*/
    taxa = 0.05;     
  }
  else {
    if (compras <= 5000) { /* Nessa condição não é necessário por a condição de maior que 3000, pois nesse if já é maior que 3000*/
      taxa = 0.03;    
    }  
    else{
      taxa=0.02;         /* Nessa condição não é necessário por a condição de maior que 2000, pois nesse if já é maior que 2000*/        
    }
  }     
} 
desconto = compras * taxa;
totpagar = compras - desconto;
printf("O seu desconto foi de %f e você ira pagar %f reais.", desconto, totpagar);
}
```
