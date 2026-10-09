# Cifra Fibonacci + P.A. em C

Projeto de estudo em linguagem C que criptografa uma frase usando um **deslocamento (shift) variável** no alfabeto. O deslocamento de cada letra é calculado com a **Sequência de Fibonacci** somada a uma **Progressão Aritmética (P.A.)**. O usuário escolhe o shift inicial, a razão da P.A. e a direção (direita ou esquerda).

> **Aviso:** este é um projeto educacional. Cifras de deslocamento são fáceis de quebrar, então **não use para proteger dados reais**.

## Como funciona

O alfabeto é numerado de 0 a 25 (A=0, B=1, ..., Z=25). Para cada letra da frase:

1. Calcula-se o shift da posição: `shift = Fibonacci + P.A.`
2. Dependendo da direção escolhida, o shift é somado (direita) ou subtraído (esquerda) do número da letra.
3. Aplica-se o resto da divisão por 26, para o alfabeto "dar a volta".
4. O resultado é convertido de volta em letra.

**Parâmetros (todos escolhidos pelo usuário, exceto Fibonacci):**

- **Shift (chave):** primeiro termo da P.A.
- **Razão da P.A.:** valor somado à P.A. a cada letra
- **Direção:** 1 = direita, 2 = esquerda
- **Fibonacci:** 1, 1, 2, 3, 5, 8, 13...

Como o shift muda a cada letra, a mesma letra pode virar letras diferentes dentro da mesma frase.

## Regras do programa

- Letras minúsculas são convertidas para maiúsculas.
- Espaços, números, pontuação e acentos são copiados sem alteração.
- Somente letras contam para a posição usada no cálculo do shift.
- O programa valida o shift e a razão (precisam ser números inteiros) e a direção (precisa ser 1 ou 2).
- Valores negativos ou maiores que 25 são ajustados para dentro do alfabeto.

## Como compilar e executar

Com o GCC instalado:

```bash
gcc cifra.c -o cifra
./cifra
```

Exemplo de uso:

```
Qual shift voce quer usar? 6
Qual razao voce quer usar? 4
Direcao do shift (1 = direita, 2 = esquerda): 1
Oq vamos criptografar? SANTANDER
ZLDOBVUHL
```

## Exemplo passo a passo

Palavra **SANTANDER**, shift 6, razão 4, direção direita:

| Pos. | Letra | Fibonacci | P.A. | Shift | Resultado |
|---|---|---|---|---|---|
| 1 | S | 1 | 6 | 7 | Z |
| 2 | A | 1 | 10 | 11 | L |
| 3 | N | 2 | 14 | 16 | D |
| 4 | T | 3 | 18 | 21 | O |
| 5 | A | 5 | 22 | 1 | B |
| 6 | N | 8 | 0 | 8 | V |
| 7 | D | 13 | 4 | 17 | U |
| 8 | E | 21 | 8 | 3 | H |
| 9 | R | 8 | 12 | 20 | L |

**SANTANDER → ZLDOBVUHL**

Quando um valor passa de 25, aplica-se o resto por 26 (por exemplo, 27 vira 1).

## Exemplos para testar

| Entrada | Shift | Razão | Direção | Saída |
|---|---|---|---|---|
| `OI MUNDO` | 6 | 4 | Direita | `VT CPOLF` |
| `OI MUNDO` | 6 | 4 | Esquerda | `HX WZMVX` |
| `OI MUNDO` | 3 | 4 | Direita | `SQ ZMLIC` |
| `OI MUNDO` | 6 | 10 | Direita | `VZ OHMPP` |
| `SANTANDER` | 6 | 4 | Direita | `ZLDOBVUHL` |
| `SANTANDER` | 6 | 4 | Esquerda | `LPXYZFMBX` |
| `SANTANDER` | 6 | 10 | Direita | `ZRPGZZEXH` |

## Como decifrar

Use o mesmo shift, a mesma razão e a direção **oposta**. Por exemplo, `ZLDOBVUHL` com shift 6, razão 4 e direção esquerda volta para `SANTANDER`.

## Ideias para evoluir

- Tratar letras com acento.
- Adicionar uma opção separada de decifrar.
- Permitir cifrar arquivos de texto.
- Versão em C++.

## Autor

Jonathan Tiburcio da Silva
[GitHub](https://github.com/joe1801-blip) | [LinkedIn](https://linkedin.com/in/jonathan-tiburcio-96579a328)
