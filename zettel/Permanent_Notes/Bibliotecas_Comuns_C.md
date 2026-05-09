Referees: #C 
# 📚 Bibliotecas Mais Comuns em C

Este material apresenta as bibliotecas padrão mais utilizadas na linguagem C, suas funcionalidades principais e exemplos práticos de uso.  

---

## 1. `<stdio.h>` - Standard Input/Output

**Funções principais:**
- `printf()` — imprime na tela
- `scanf()` — lê entrada do teclado
- `fgets()` — lê strings com segurança
- `fopen()`, `fclose()`, `fread()`, `fwrite()`, `fprintf()` — manipulação de arquivos

**Exemplo:**
```c
#include <stdio.h>

int main() {
    int idade;
    printf("Digite sua idade: ");
    scanf("%d", &idade);
    printf("Você tem %d anos.\n", idade);
    return 0;
}
```

---

## 2. `<stdlib.h>` - Standard Library

**Funções principais:**
- `malloc()`, `calloc()`, `free()` — alocação dinâmica de memória
- `atoi()`, `atof()` — conversão de strings para números
- `exit()` — encerra o programa

**Exemplo:**
```c
#include <stdlib.h>
#include <stdio.h>

int main() {
    int *vetor = (int*) malloc(5 * sizeof(int));
    if (vetor == NULL) {
        printf("Erro de alocação!\n");
        exit(1);
    }
    free(vetor);
    return 0;
}
```

---

## 3. `<string.h>` - Manipulação de Strings

**Funções principais:**
- `strlen()` — tamanho da string
- `strcpy()`, `strncpy()` — cópia de string
- `strcmp()` — comparação
- `strcat()` — concatenação

**Exemplo:**
```c
#include <string.h>
#include <stdio.h>

int main() {
    char nome[50] = "Olá, ";
    strcat(nome, "João!");
    printf("%s\n", nome);
    return 0;
}
```

---

## 4. `<math.h>` - Funções Matemáticas

**Funções principais:**
- `sqrt()` — raiz quadrada
- `pow()` — exponenciação
- `sin()`, `cos()`, `tan()` — trigonometria
- `log()`, `exp()` — logaritmos e exponenciais

**Exemplo:**
```c
#include <math.h>
#include <stdio.h>

int main() {
    double base = 2, expoente = 3;
    printf("2 elevado a 3 é %.2f\n", pow(base, expoente));
    return 0;
}
```

---

## 5. `<ctype.h>` - Manipulação de caracteres

**Funções principais:**
- `isalpha()`, `isdigit()`, `isspace()` — verificações
- `toupper()`, `tolower()` — conversão de caixa

**Exemplo:**
```c
#include <ctype.h>
#include <stdio.h>

int main() {
    char letra = 'a';
    printf("Maiúsculo: %c\n", toupper(letra));
    return 0;
}
```

---

## 6. `<time.h>` - Manipulação de tempo

**Funções principais:**
- `time()`, `localtime()`, `strftime()` — data e hora atual
- `clock()` — medir tempo de execução

**Exemplo:**
```c
#include <time.h>
#include <stdio.h>

int main() {
    time_t agora;
    time(&agora);
    printf("Data e hora atual: %s", ctime(&agora));
    return 0;
}
```

---

## 7. `<stdbool.h>` - Tipo booleano

**Introduz o tipo `bool`, com valores `true` e `false`**

**Exemplo:**
```c
#include <stdbool.h>
#include <stdio.h>

int main() {
    bool aprovado = true;
    if (aprovado) {
        printf("Aluno aprovado!\n");
    }
    return 0;
}
```

---

## 🧠 Dicas Didáticas

- Sempre explique o **porquê** da biblioteca ser usada.
- Mostre o **cabeçalho**, as funções principais e **exemplos práticos**.
- Estimule os alunos a explorar a **documentação oficial do C**.
