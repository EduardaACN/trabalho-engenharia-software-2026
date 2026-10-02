# trabalho-engenharia-software-2026
Trabalho de clínica veterinária do Técnico em Informática, segundo semestre de 2026. Eduarda Aparecida

Este repositório é onde vou guardar meu trabalho da disciplina de Engenharia de Software

protótipo do site de veterinária https://www.figma.com/design/pRAxrL7OQCi1t7lscXrpr3/Sem-t%C3%ADtulo?node-id=0-1&t=PlbzRAmXWYac0Rb8-1  25/9/26

## Diagramas UML

### Diagrama de caso de uso

```mermaid
flowchart TD
    %% atores
    cliente["cliente"]
    garçom["garçom"]

    %%ações
    subgraph sistema
        comida["pedir comida"]
        vinho["pedir vinho"]
    end

    %% relacionamentos
    cliente -- "faz pedido" --- comida
    garçom -- "recebe pedido" --- comida

    vinho -. "estende" .-> comida
```
### Diagrama de classe

```mermaid
classDiagram
    class Veterinário {
        %% atributos: características que serão armazenadas no sistema
        -CPF: string
        %% métodos: ações que serão desempenhadas por essa entidade no sistema
        +darCPF() string
        +atender Animal(animal: Amimal) void
    }

    Veterinário -- Animal
    Animal -- Cliente

    class Animal {
        -dono: Cliente
        -nome: string
        -idade: string
        -espécie: string
        +darNome(): string
        +darIdade(): string
        +darEspécie(): string
    }

    class Cliente{
        -animais: Lista de Animal[]

    }
```

2/10/26
