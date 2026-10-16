# trabalho-engenharia-software-2026
Trabalho de clínica veterinária do Técnico em Informática, segundo semestre de 2026. Eduarda Aparecida

Este repositório é onde vou guardar meu trabalho da disciplina de Engenharia de Software

protótipo do site de veterinária https://www.figma.com/design/pRAxrL7OQCi1t7lscXrpr3/Sem-t%C3%ADtulo?node-id=0-1&t=PlbzRAmXWYac0Rb8-1  25/9/26

## Diagramas UML

### Diagrama de caso de uso

```mermaid
flowchart TD
    cliente["Tutor(a) 
    👤"]
    animal["Animal 
    🐾"]
    veterinario["Veterinário(a) 
    🩺"]
subgraph sistema clínica
    consulta["Consulta"]
subgraph sistema software
    login["Login/Criar conta"]
    site["Site da Clínica
    🖥️"]
    histórico["Histórico Animal
    "]
    CT["Cadastro de Tutor"]
    CA["Cadastro de Animal"]
    dados["Especificações"]
end
    exame[Exame Veterinário]
    tratamento["Tratamento"]
    pagamento["Pagamento"]
end

cliente -- Marca --> consulta
cliente -- Possui --> animal
animal -- Levado --> consulta
veterinario -- Acessa --> site
cliente -. Verifica .-> site
site -- Etapa --> login
login -- Acesso --> site
site -. Procura .-> histórico
site -- Registra --> histórico
site -. Procura .-> CT
site -. Procura .-> CA
site -- Cria --> CT
site -- Cria --> CA
CT -- Dados de --> cliente
CA -- Anotação de --> dados
dados -- Dados de --> animal
veterinario -- Realiza --> consulta
exame -- Resulta --> tratamento
consulta -- Resulta --> exame
histórico -- Checado para --> tratamento
dados -- Checado para --> tratamento
tratamento -- Recebe --> animal
tratamento -- Encaminha --> site
consulta -- Resulta --> pagamento
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
