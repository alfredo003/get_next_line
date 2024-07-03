# Get Next Line

Ler uma linha de um descritor de arquivo é muito tedioso. Este projeto visa facilitar essa tarefa através da implementação de uma função que retorna uma linha lida de um descritor de arquivo.

## Objetivos

Este projeto não só permitirá adicionar uma função muito conveniente à sua coleção, mas também fará você aprender um novo conceito altamente interessante na programação em C: variáveis estáticas.

## Parte Obrigatória

- **Nome da função:** `get_next_line`
- **Protótipo:** `char *get_next_line(int fd);`
- **Arquivos a serem entregues:** `get_next_line.c`, `get_next_line_utils.c`, `get_next_line.h`
- **Parâmetros:** `fd` - O descritor de arquivo do qual ler
- **Valor de retorno:** Linha lida (comportamento correto), `NULL` se não houver mais nada para ler ou ocorrer um erro.
- **Funções externas:** `read`, `malloc`, `free`
- **Descrição:** Escreva uma função que retorna uma linha lida de um descritor de arquivo.

### Detalhes

- Chamadas repetidas (por exemplo, usando um loop) para sua função `get_next_line()` devem permitir que você leia o arquivo de texto apontado pelo descritor de arquivo, uma linha de cada vez.
- Sua função deve retornar a linha que foi lida. Se não houver mais nada para ler ou se ocorrer um erro, ela deve retornar `NULL`.
- Certifique-se de que sua função funcione conforme o esperado tanto ao ler um arquivo quanto ao ler da entrada padrão.
- Observe que a linha retornada deve incluir o caractere `\n` de terminação, exceto se o final do arquivo for alcançado e não terminar com um caractere `\n`.
- Seu arquivo de cabeçalho `get_next_line.h` deve conter pelo menos o protótipo da função `get_next_line()`.
- Adicione todas as funções auxiliares necessárias no arquivo `get_next_line_utils.c`.
- Como você terá que ler arquivos no `get_next_line()`, adicione esta opção à chamada do seu compilador: `-D BUFFER_SIZE=n`. Isso definirá o tamanho do buffer para `read()`. O valor do tamanho do buffer será modificado pelos seus avaliadores e pelo Moulinette para testar seu código.
- Devemos ser capazes de compilar este projeto com e sem a flag `-D BUFFER_SIZE`, além das flags usuais. Você pode escolher o valor padrão de sua escolha.

### Compilação

Você compilará seu código da seguinte forma (um tamanho de buffer de 42 é usado como exemplo):
```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 <files>.c
```

### Restrições

- Consideramos que `get_next_line()` tem um comportamento indefinido se o arquivo apontado pelo descritor de arquivo mudou desde a última chamada, enquanto `read()` não alcançou o final do arquivo.
- Também consideramos que `get_next_line()` tem um comportamento indefinido ao ler um arquivo binário. No entanto, você pode implementar uma maneira lógica de lidar com esse comportamento, se desejar.
- A função ainda funciona se o valor de `BUFFER_SIZE` for 9999? Se for 1? 10000000? Você sabe por quê?
- Tente ler o mínimo possível a cada vez que `get_next_line()` for chamado. Se encontrar uma nova linha, você deve retornar a linha atual.
- Não leia o arquivo inteiro e depois processe cada linha.

### Proibições

- Você não pode usar sua `libft` neste projeto.
- `lseek()` é proibido.
- Variáveis globais são proibidas.

## Parte Bônus

Este projeto é direto e não permite bônus complexos. No entanto, confiamos em sua criatividade. Se você completou a parte obrigatória, tente a parte bônus.

### Requisitos

- Desenvolva `get_next_line()` usando apenas uma variável estática.
- Sua `get_next_line()` deve gerenciar múltiplos descritores de arquivos ao mesmo tempo. Por exemplo, se você pode ler dos descritores de arquivos 3, 4 e 5, você deve ser capaz de ler de um descritor diferente por chamada, sem perder o fio de leitura de cada descritor ou retornar uma linha de outro descritor.

Isso significa que você deve ser capaz de chamar `get_next_line()` para ler do descritor 3, depois 4, depois 5, depois novamente 3, novamente 4, e assim por diante.

### Arquivos para a Parte Bônus

- `get_next_line_bonus.c`
- `get_next_line_bonus.h`
- `get_next_line_utils_bonus.c`

### Avaliação da Parte Bônus

A parte bônus só será avaliada se a parte obrigatória estiver PERFEITA. Perfeita significa que a parte obrigatória foi integralmente feita e funciona sem falhas. Se você não passou em TODOS os requisitos obrigatórios, sua parte bônus não será avaliada.

## Submissão e Avaliação por Pares

Envie sua tarefa para o seu repositório Git conforme de costume. Apenas o trabalho dentro do seu repositório será avaliado durante a defesa. Não hesite em verificar novamente os nomes dos seus arquivos para garantir que estão corretos.

### Dicas para Testes

- Ao escrever seus testes, lembre-se que tanto o tamanho do buffer quanto o tamanho da linha podem ter valores muito diferentes.
- Um descritor de arquivo não aponta apenas para arquivos regulares.

Seja inteligente e verifique com seus colegas. Prepare um conjunto completo de testes diversos para a defesa.

Após passar, não hesite em adicionar seu `get_next_line()` à sua `libft`.
