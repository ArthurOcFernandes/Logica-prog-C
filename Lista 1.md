# Resolução dos exercícios da lista 1:

## Qual é o tipo de variável correta para armazenar as seguintes informações:

> Para armazenar algum dado em uma variável, é necessário pensar a condição de existência dessa variável para entender qual o melhor tipo de dado de adequa para cada situação.

### a. A idade.

R: int ou unsigned int.

> No caso de uma idade, estamos falando de um número inteiro, na maioria das vezes. Esse número pode ser armazenado pelo tipo `int`, que armazena números sem casas decimais, ou `unsigned int`, que armazena números sem casas decimais, maiores ou iguais a 0. O unsigned int é a opção ideal, mas como não existem idades tão grandes, utilizar apenas int não vai fazer diferença. No caso de idade humana, podemos usar o `unsigned short` também, que vai ocupar menos memória.

### b. O número de estrelas na galáxia.

R: unsigned long long

> Nesse caso, o unsigned long é a opção ideal pois ele armazena dados sem casas decimais (não existe 1,5 estrela) e com números maiores ou iguais a 0, o que possibilita uma contagem maior; ainda assim é impossível representar com dados primitivos o número de estrelas porquê o universo está em constante expansão.

### c. A quantidade de chuva média no mês de fevereiro.

R: float

> Nesse caso, um número de ponto flutuante faz o trabalho. 

### d. A área do seu quintal.

R: float

> Novamente, uma opção de ponto flutuante é interessante, pois pode não ser um número exato.

## 2. Indique a diferença entre as seguintes atribuições:

```c
char a; // declaração da variável a do tipo caractere
a = ’6’; // atribuição do caractere 6 à variável a
a = 6; // atribuição do caractere com valor 6 na tabela ASCII à variável a
```

> Quando estamos atribuindo um valor a uma variável do tipo char, precisamos nos atentar a sempre colocar o caractere entre aspas simples, ex.: 'a'. Caso contrário, no caso de caracteres de texto, o compilador vai indicar o erro, e no caso de caracteres que são números, será usado o valor respectivo na [tabela ASCII](https://www.asciitable.com/)

## 3. Faça um programa que leia um número real x e calcule o valor de f (x) = x^1/2 + (x/2) + x ^ 2 

```c

#include <stdio.h>
#include <math.h>

int main(){

    // declação das variáveis x e calculo, ambas do tipo float, ou seja, números de ponto flutuante.
    float x, calculo; 

    // Leitura de um número de ponto flutuante a partir do teclado, denotado pela máscara "%f" e inserção do conteúdo lido na variável x.
    scanf("%f",  &x);


    // cálculo da expressão indicada no enunciado
    calculo = sqrt(x) + (x / 2) + pow(x, 2);

    return 0;
}

```

> a função `sqrt(x)` calcula a raiz quadrada de um dado número x e a função `pow(x, y)` calcula o resultado da elevação de um número x à potência y.

## 4. Faça um programa que leia dois valores inteiros nas variáveis x e y e troque o conteúdo das variáveis. Refaça este problema sem o uso de outras variáveis que não x e y.

```c
#include <stdio.h>
// Com o uso de variável auxiliar
int main(){


    int x, y, aux; // declaração das variáveis x, y e aux do tipo int


    scanf("%d %d", &x, &y); // leitura a partir do teclado de dois números inteiros e inserção destes em x e y, respectivamente

    aux = x; // insere o valor da variável x dentro da variável aux
    x = y; // insere o valor da variável y dentro da variável x. Agora o valor inicial de x está sendo guardado pela aux.
    y = aux; // insere o valor inicial de x, que está sendo guardado na variável aux, dentro da variável y e completando a troca de valores.

    printf("valor de x: %d\nvalor de y:%d", x, y);

    return 0;
}

```

> Imagem ilustrativa:
> ![](/imgs/img1.jpg)

## 5. Faça um programa que leia os valores correspondentes aos três lados a, b e c de um triângulo. O programa então determina se o triângulo é isósceles, escaleno ou equilátero, informando isto para o usuário, e em seguida imprime a área A do triângulo utilizando a fórmula de Heron:

![](/imgs/img2.png)

```c
#include <stdio.h>
#include <math.h>

int main(){

    float a, b, c, s, area; // declaração das variáveis, todas do tipo float.

    scanf("%f %f %f", %a, &b, &c); // leitura de três números de ponto flutuante e inserção destes valores nas variáveis a, b e c

    s = (a + b + c) / 2; // cálculo da variável s, definida pela fórmula de Heron.

    area = sqrt(s * (s - a) * (s - b) * (s - c)); // cálculo da area com a formula de Heron, utilizando a variável s calculada anteriormente.

    return 0;
}

```

## 6. A solução abaixo está correta para classificar um número como par e menor que 100, ou par e maior ou igual a 100, etc, como no exemplo visto em aula?

```c
#include <stdio.h>
int main(){
    int a;

    printf("Digite um número inteiro:");

    scanf("%d", &a);

    if( ( a % 2 == 0) && (a < 100) )
        printf("O número é par e menor que 100\n");
    else if( a >= 100 )
        printf("O número é par e maior ou igual a 100\n");
    if( ( a % 2 != 0) && (a < 100) )
        printf("O número é ímpar e menor que 100\n");
    else if (a >= 100)
        printf("O número é ímpar e maior que 100\n");
}

```

---

> Para entender o funcionamento desse código, e analisar se ele faz o que é proposto é necessário fazer sua leitura linha a linha e entender o que os condicionais estão selecionando, isso é, qual conjunto cabe em cada condicional.
>
> 1 - `if( ( a % 2 == 0) && (a < 100) )`
>
> Conjunto contemplado: números pares **e** menores que 100. i.e: se um número for par ( o resto da divisão inteira deste número por dois for igual a 0), ele entra nesse bloco condicional.
> 
> 2 - `else if( a >= 100 )`
>
> Caso o número não entre na condição anterior, mas for maior ou igual a 100, ele entra nessa condição **independentemente se ele for par ou ímpar**.
>
> 3 - `if( ( a % 2 != 0) && (a < 100) )`
>
> Conjunto contemplado: números ímpares **e** menores que 100. i.e: se um número for ímpar ( o resto da divisão inteira deste número por dois for igual a 1), ele entra nesse bloco condicional.
>
> 4 - `else if (a >= 100)`
>
> Similar à análise 2, caso o número não se encaixe na condição anterior, mas ele for maior ou igual a 100, ele entra nessa condição sendo **par ou ímpar**.
>
> **Sendo assim**, para o caso de números menores do que 100, a verificação é feita corretamente, bem como a indicação da classificação dos números. No entanto, para o caso de números maiores ou iguais a 100 vai acontecer o seguinte:
>
> - Verificação de que ele é maior que 100, o que faz ele falhar na condição 1.
> - Por falhar na condição 1, a condição 2 é verificada e o número vai entrar na condição, pois é maior ou igual a 100. 
> - Será impresso que o número é **par e maior que cem**
> - Verificação de que ele é maior que 100, o que faz ele falhar na condição 3.
> - Por falhar na condição 3, a condição 4 é verificada e o número vai passar nessa condição, pois ele é maior ou igual a 100.
> - Será impresso que o número é **ímpar e menor que cem**
>
> Ou seja, o programa vai imprimir que o número é par e maior ou igual a 100, e que é ímpar e maior que 100, independentemente se ele é par ou ímpar, apenas por ele ser maior ou igual a 100. 
>
> Para resolver esse bug, é necessário definir melhor os conjuntos de cada condicional, algo como:

```c
#include <stdio.h>

int main(){

    int a; // Declaração da variável a do tipo int

    printf("digite um numero inteiro:\n");

    scanf("%d", &a); // Leitura a partir do teclado de um número inteiro e inserção do seu valor na variável a.

    if( a % 2 == 0){ // Verificação se o resto da divisão inteira de a é igual a 0.
        printf("O numero é par "); // caso seja, o número é par e imprimimos na tela.
    } else{ // Caso contrário
        printf("O numero é ímpar "); // O número é impar e imprimimos na tela.
    }

    if(a < 100){ // Verificação se a é menor que 100
        printf("e menor que 100\n"); // Caso seja, imprimimos essa informação.
    } else{ // Caso contrário
        printf("e maior ou igual a 100\n"); // Imprimimos que a é maior ou igual a 100.
    }

    return 0;
}
```

> Nesse caso, dividimos melhor os conjuntos de números que a pode assumir e tomamos decisões mais assertivas para cada caso.
>
> Primeiro, verificamos se `a` é par ou ímpar, e já damos essa informação na tela. É importante não pular linha com o `\n`, pois queremos que as informações sobre o número apareçam sequencialmente, por isso há apenas um espaço em branco após a primeira frase impressa.
>
> Após isso, já classificamos o número sobre sua paridade, e podemos verificar sobre seu valor relativo a 100 e imprimir a informação devida a partir disso.
>
> Sendo assim, a divisão em conjuntos claros é muito importante para conseguirmos evitar bugs quando estamos fazendo classificações, seja de números, palavras, ou outras estruturas que vão aparecer posteriormente.

---

## 7. Escreva um programa lê três números e os imprime em ordem (ordem crescente).

```c

#include <stdio.h>

int main(){


    int a, b, c; // declaração das variáveis

    scanf("%d %d %d", &a, &b, &c); // leitura a partir do teclado e inserção nas variáveis

    if(a > b) { // se a for maior que trocamos o conteúdo das duas variáveis (ordenação entre as duas)
        int temp = a;
        a = b;
        b = temp;
    }

    // nesse ponto, a < b, ou seja, estão ordenadas 

    if(b > c) { // com a e b ordenadas, precisamos verificar a ordenação entre b e c. Caso b seja maior que c, fazemos a inversão de valores.
        int temp = b;
        b = c;
        c = temp;
    }

    // nesse ponto, b < c, no entanto, no caso de ter havido uma troca, pode ser que a e b passem a estar desornedadas entre si, o que necessita fazer mais uma verificação:

    if(a > b){ // se a for maior que trocamos o conteúdo das duas variáveis
        int temp = a;
        a = b;
        b = temp;
    }

    // Neste ponto, garantimmos que c > b > a, ou seja, que as três variáveis estão ordenadas entre si e podemos imprimí-las em ordem:

    printf("números em ordem: %d - %d - %d", a, b, c);


    return 0;
}

```
