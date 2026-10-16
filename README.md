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
histórico -- Checado para --> exame
dados -- Checado para --> exame
tratamento -- Recebe --> animal
tratamento -- Encaminha --> site
consulta -- Resulta --> pagamento
```
### Diagrama de classe

```mermaid
classDiagram
    class Veterinario {
        -CPF: String
        -nome: String
        +darCPF() String
        +atenderAnimal(animal: Animal) void
        +realizarCadastro() void
        +realizarExame() void
    }

    class Animal {
        #nome: String
        #idade: int
        #especie: String
        #peso: float
        +darNome() String
        +darIdade() int
        +darEspecie() String
        +darEspecificações(especificações: Especificações) void
    }
    class Especificações {
        -tipoSanguineo: String
        -problemaSaude: String
        -usoMedicamento: String
        -Temperamento: String
        +registrarDados() void
        +darDados() String

    }
    class Tutor {
        -nome: String
        -animais: Animal[]
        +darDados() String
    }

    class Login {
        -login: String
        -cadastro: String
        -senha: String
        +autenticar()void
        +acessoSite()void
    }

    class Site {
        -cadastroTutor: String
        -cadastroAnimal: String
        -histórico: String
        -Especificações:String 
        +exibirCadastroTutor() void
        +exibirCadastroAnimal() void
        +exibirHistorico() void
        +exibirEspecificações()void
        +exibirLogin()void
    }

    class Historico {
        -idHistorico: int
        -data: int
        -diagnostico: String
        -tratamento: String
        -observações: String
        +registrarAtendimento() void
        +consultarHistorico() String
    }

    Veterinario "1" -- "*" Animal : atende
    Veterinario "*" -- "1" Site : acessa
    Site ..> Tutor : cadastra
    Site ..> Animal : cadastra
    Site ..> Historico : consulta
    Site ..> Especificações : consulta
    Tutor "1" -- "*" Animal : possui
    Tutor ..> Site : acessa
    Veterinario "1" -- "*" Tutor : atende
    Animal "1" --> "*"Especificações : possui
    Animal "1" ..> "*" Historico : possui
    Veterinario "1" -- "*" Historico : registra
    Veterinario "1" -- "*" Especificações : registra
    Site -- Login: possui
    Login -- Site: etapa
```

16/10/26
