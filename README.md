<p align="center">
  <a href="#questão-1">1</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-2">2</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-3">3</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-41">4.1</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-42">4.2</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-51">5.1</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-52">5.2</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-6">6</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-7">7</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-81">8.1</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-82">8.2</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-9">9</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#questão-10">10</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
</p>

# 📚 Lista 03 - Programação em C
Lista de exercícios submetida na cadeira de Laboratório de Programação.

## Questão 1:
Faça um programa em C que leia um vetor do tipo float com 15 elementos e apresente a soma do
menor e maior elemento do vetor fornecido.
``` c
#include <stdio.h>
#define TAM 15

int main() {
  float v[TAM], maior=0, menor=0, soma;
  for (int i = 0; i < TAM; i++){
    printf("Número %d: ", i);
    scanf("%f",&v[i]);
  }
  for (int i = 0; i < TAM; i++){
    if(i == 0){maior=v[i]; menor=v[i];}
      if(v[i] > maior){
        maior = v[i];
      }
      else{
        if(v[i]<menor){
            menor=v[i];
        }
      } 
 }
soma = menor + maior;
printf("Maior número: %0.1f. Menor número: %0.1f. --> Soma = %0.1f",maior, menor,soma);
return 0;
}
```
## Questão 2:
Faça um programa em C que leia uma string e um caractere do usuario e informe se a string de entrada contem o caracter fornecido.
``` c
#include <stdio.h>
#include <string.h>

#define TAM 10
char keyboard[BUFSIZ];

void setbuf();
void getinput(char *buff, int size);

int main() {
  char caracter, string[TAM];
  getinput(string, 10);
  string[strcspn(string, "\n")] = 0;
  
  setbuf(stdin, keyboard);
  scanf("%c",&caracter);
  
  for (int i = 0; i < TAM; i++){
    if (caracter == string[i]){
      printf("Tem %c na palavra %s",caracter, string);
      break;
    } 
  }
  return 0;
  }

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```

## Questão 3:
Faça um programa em C que leia uma string do usuario e informe a quantidade de caracteres da string fornecida. 
- Obs: não use a funçao strlen().
``` c
#include <stdio.h>
#include <string.h>
#define TAM 100
char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);

int main() {
  char string[TAM];
  int cout = 0, i = 0;
  getinput(string, TAM);
  string[strcspn(string, "\n")] = 0;
  
  while(string[i] != '\0')
  {
    i++;
    cout++;
    }
    printf("%s possui %d caracteres",string, cout);
    return 0;
}
void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```

## Questão 4.1:
Faça um programa em C que leia duas strings do usuario e informe se elas sao iguais. 
- sem strcmp()
``` c
#include <stdio.h>
#include <string.h>

char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);
#define TAM 10

int main() {
  char s1[TAM],s2[TAM], ig=0, dif=0;
  getinput(s1, TAM);
  getinput(s2, TAM);
  s1[strcspn(s1, "\n")] = 0;
  s2[strcspn(s2, "\n")] = 0;

  for (int i = 0; i < TAM; i++){
    s1[i] == s2[i]? ig++: dif++;    
}
 if (dif == 0){
   printf("\n%s == %s",s1,s2);
 } else{
   printf("\n%s != %s",s1,s2);
 }
 return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```
## Questão 4.2:
Faça um programa em C que leia duas strings do usuario e informe se elas sao iguais. 
- com strcmp()
``` c
#include <stdio.h>
#include <string.h>
#define TAM 10
char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);

int main() {
  char s1[TAM],s2[TAM];

  getinput(s1, TAM);
  getinput(s2, TAM);
  s1[strcspn(s1, "\n")] = 0;
  s2[strcspn(s2, "\n")] = 0;

  if (strcmp(s1,s2) == 0){
    printf("%s == %s",s1,s2);
  } else {
    printf("%s != %s",s1,s2);
  }
  return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```


## Questão 5.1:
Faça um programa em C que concatene duas strings recebidas pelo usuario. 
- sem strcat()
``` c
#include <stdio.h>

#include <string.h>
#define TAM 100
char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);
char* conc(char *a, char *b);

int main() {
  char s1[TAM],s2[TAM];

  getinput(s1, TAM);
  getinput(s2, TAM);
  s1[strcspn(s1, "\n")] = 0;
  s2[strcspn(s2, "\n")] = 0;

  puts(conc(s1,s2)); //funçao manual
  return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
char* conc(char *a, char *b){
  int i = 0, j = 0;
  while(a[i]!='\0') {++i;}
  while(b[j]!='\0') {
    a[i]=b[j];
    j++; i++;
  }
    a[i]='\0';
    return a;
}
```

## Questão 5.2:
Faça um programa em C que concatene duas strings recebidas pelo usuario. 
- com strcat()
``` c
#include <stdio.h>
#include <string.h>
#define TAM 100
char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);

int main() {
  char s1[TAM],s2[TAM];

  getinput(s1, TAM);
  getinput(s2, TAM);
  s1[strcspn(s1, "\n")] = 0;
  s2[strcspn(s2, "\n")] = 0;

  puts(strcat(s1,s2));
  return 0;
}

void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```

## Questão 6:
Faça um programa em C que leia uma string do usuário e a apresente na forma inversa.
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define TAM 10
char keyboard[BUFSIZ];
void setbuf();
void getinput(char *buff, int size);

int main() {
  char word[TAM];
  char auxiliar[TAM];
  int i,qnt;
  
  getinput(word, TAM);
  qnt = strlen(word)-1;
  
  for(i = 0; word[i]!='\0'; i++){ 
    auxiliar[qnt] = word[i];
    qnt--;     
}
  
auxiliar[i]='\0';
strcpy(word, auxiliar);  
printf("\nFrase inversa: %s",word);

return 0;
  }
  
void getinput(char *buff, int size){
    setbuf(stdin, keyboard);
    fgets(buff, size, stdin);
}
```

## Questão 7:
Faça um programa em C que gere um vetor com 3 numeros inteiros pseudoaleatorios no intervalo [0, 19] e apresente a sua media aritmetica e geometrica.
``` c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <math.h>
#define TAM 3

int main() {
  int v[TAM], i, j, soma=0, mult=1;
  float arit, geo;
  
  srand(time(NULL));
  for (i = 0; i<TAM; i++){
    v[i] = rand() % 20;
    soma += v[i];
    mult *= v[i];
    printf("%2d ",v[i]);
  }
  
  printf("\n\nSoma = %d\nMult = %d\n",soma, mult);
  arit = (float)soma / TAM;
  geo = pow((mult),(float)1/TAM);
  printf("Média Ari: %0.2f || Média Geo: %0.2f", arit,geo);
  return 0;
}
```

## Questão 8.1:
Faça um programa em C que gere um vetor com 100 numeros inteiros pseudoaleatorios no intervalo definido pelo usuario e apresente esse vetor ordenado (crescente). 
- metodo de ordenacao por seleção
``` c
#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#define TAM 100
  
int main() {
  int x,y,i,inter;
  int v[TAM], maior, menor;
  
  printf("Qual o número inicial do intervalo?\n");
  scanf("%d",&x);
  printf("Qual o número final do intervalo?\n");
  scanf("%d",&y);
  printf("\n\n");

	srand(time(0));
	
  for (i = 0; i<TAM; i++){
    v[i] = x + rand() % y+1;
    printf("%d ",v[i]);
  }
  
printf("\n\n");
  
for(i = 0; i < TAM - 1; i++){
  int posic = i;
  
  for(int j = i + 1; j < TAM; j++){
  if(v[posic] > v[j])
  posic  =j;
  }
  
  if(posic != i){
    int troca = v[i];
    v[i] = v[posic];
    v[posic] = troca;
  }
}
  
printf("Vetor ordenado:\n\n");
for(i = 0; i < TAM; i++)
printf("%d ", v[i]);
  
return 0;
}
```

## Questão 8.2:
Faça um programa em C que gere um vetor com 100 numeros inteiros pseudoaleatorios no intervalo definido pelo usuario e apresente esse vetor ordenado (crescente). 
- metodo bolha (bubble sort).
``` c
#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#define TAM 100
void bubbleSort(int array[], int size);

int main() {
  int x,y,i,inter;
  int v[TAM], maior, menor;
  
  printf("Qual o número inicial do intervalo?\n");
  scanf("%d",&x);
  printf("Qual o número final do intervalo?\n");
  scanf("%d",&y);
  printf("\n\n");

	srand(time(0));
	
  for (i = 0; i<TAM; i++){
    v[i] = x + rand() % y+1;
    printf("%d ",v[i]);
  } 
  
printf("\n\n");
bubbleSort(v, TAM);
return 0;
}

void bubbleSort(int array[], int size) {

  for (int step = 0; step < size - 1; ++step) {
    for (int i = 0; i < size - step - 1; ++i) {
      if (array[i] > array[i + 1]) {
        int temp = array[i];
        array[i] = array[i + 1];
        array[i + 1] = temp;
      }
    }
  }
  for (int i = 0; i < size; ++i) {
    printf("%d ", array[i]);
  }
  printf("\n");
}
```

## Questão 9:
Faça um programa que leia uma matriz bidimensional do usuario, de dimensao 3x3, e apresente os elementos da diagonal principal.
``` c
#include <stdio.h>
#define TAM 3

int main() {
  int matriz[TAM] [TAM],j,i;
  
  for(i = 0; i < TAM; i++){
    for (j = 0; j < TAM; j++){
      printf("[%d] [%d]:\n", i, j);
      scanf ("%d", &matriz [i] [j]);
    }
  } 
  printf("Diagonal principal:\n");
  for(i = 0; i < TAM; i++){
    for (j = 0; j < TAM; j++){
      if (matriz[i] == matriz [j]){
        printf("%d ",matriz[i] [j]);
      }
  }
    }
  return 0;
}
```

## Questão 10:
Faça um programa que gere uma matriz bidimensional com elementos aleatorios e receba do usuario um valor inteiro x. O programa deve informar quantas vezes x aparece na matriz gerada.
``` c
#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#define LINHA 5
#define COLUNA 5
#define TAM 100

int main() {
  int matriz[LINHA] [COLUNA], num, count=0;
  
  printf("Digite um número: ");
  scanf("%d",&num);
  
  srand(time(NULL));
  
    for(int i = 0; i < LINHA; i++){
      for(int j = 0; j < COLUNA; j++){
        matriz[i] [j] = rand() % TAM;
        printf("%3d",matriz[i][j]);
        if (matriz[i][j] == num){
        count++;
      }
    }
      printf("\n");
      }
 printf("n° --> %d\naparece --> %dx",num,count);
 return 0;
  }
```
