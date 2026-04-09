# Agendinha Java Swing

**Minha primeira agenda digital, feita com Java!**

Este projeto nasceu de uma necessidade real de todo estudante universitario: organizar aulas, provas e compromissos sem depender de papeis que se perdem ou lembretes que ficam no celular sem ninguem nunca abrir. A diferenca e que, em vez de baixar um app pronto, eu resolvi **construir o meu do zero** -- e foi assim que descobri que programar e muito mais do que escrever codigos: e resolver problemas do dia a dia com as proprias maos.

---

## O que esse programa faz?

A Agendinha tem duas telas principais que se conectam entre si:

### Tela de Horario Escolar

Uma grade semanal interativa onde voce pode:
- **Cadastrar aulas** clicando em qualquer horario da semana -- o programa pergunta o nome da disciplina, o professor e o local
- **Cadastrar compromissos semanais** que nao sao aulas (reunioes, estudos em grupo, etc.)
- **Visualizar** o que esta cadastrado em cada celula, apenas passando o mouse

Os horarios seguem o padrao universitario:
- **Manha**: M1, M2, M3, M4
- **Tarde**: T1, T2, T3, T4, T5, T6

Tudo organizado de segunda a sabado, exatamente como a grade horaria da faculdade.

### Tela de Calendario Mensal

Um calendario visual completo onde voce pode:
- **Navegar entre meses e anos** usando os seletores na parte superior
- **Cadastrar agendamentos** clicando no dia desejado -- atividades, seminarios, provas ou outros eventos
- **Visualizar agendamentos** passando o mouse sobre os dias que tem algo marcado

O calendario ja abre no mes e ano atuais, com uma saudacao mostrando o dia da semana.

As duas telas se comunicam: pelo botao "Ver Agenda" voce vai do horario para o calendario, e pelo "Ver Horario" voce volta. Tudo sem perder os dados.

---

## O que eu aprendi fazendo esse projeto

Esse projeto foi um divisor de aguas no meu aprendizado. Antes dele, eu sabia o que eram variaveis e if/else. Depois dele, eu comecei a entender como programas de verdade funcionam. Aqui vao os conceitos que ganhei vida na pratica:

### Orientacao a Objetos (nao e so teoria!)

Eu ja tinha ouvido falar de classes e objetos, mas foi aqui que isso clicou de verdade:

- **Heranca**: `Aula` herda de `CompromissoSemanal`. Isso significa que toda aula ja tem nome, local e horario automaticamente -- eu so preciso adicionar o que e especifico da aula (a disciplina). Nao repeti codigo, so estendi o que ja existia.
- **Composicao**: `Agendamento` nao herda de `Data` nem de `Disciplina` -- ele **tem** uma data e **tem** uma disciplina. E o principio de "favor composicao sobre heranca": em vez de ser algo, voce tem algo dentro de si.
- **Encapsulamento**: Os atributos sao `private` e so podem ser acessados por getters e setters. Parece burocracia, mas quando voce quer mudar como uma data funciona internamente, so precisa mexer em um lugar.

### Interfaces graficas com Swing

A primeira vez que vi uma janela abrindo com o meu codigo foi magico. O Java Swing usa o conceito de **JFrame** (a janela), **JPanel** (paineis que organizam o conteudo), **JTextField** (campos de texto), **JButton** (botoes) e **JOptionPane** (as caixinhas de dialogo). O NetBeans tem um editor visual que gera o codigo da interface automaticamente -- os arquivos `.form` guardam esse layout visual.

### Eventos e interatividade

Quando o usuario clica em um botao, o Java dispara um **evento** (`ActionEvent`, `MouseEvent`). Voce escreve o que quer que aconteca dentro de metodos como `btVerAgendaActionPerformed`. Esse e o coracao de qualquer programa interativo: **ouvir** o que o usuario faz e **responder**.

### Estruturas de dados

Em vez de criar arrays com tamanho fixo, usei `ArrayList` -- uma lista que cresce sozinha conforme voce adiciona elementos. Perfeito para armazenar aulas e agendamentos sem precisar saber quantos vao existir antes.

---

## Como os arquivos estao organizados

```
agendinha-java-swing/
├── classes/                          # A logica do programa (o "cerebro")
│   ├── CompromissoSemanal.java       # Qualquer compromisso que se repete toda semana
│   ├── Aula.java                     # Uma aula (herda de CompromissoSemanal + tem Disciplina)
│   ├── Disciplina.java              # Dados da materia: nome, professor, codigo
│   ├── Data.java                     # Manipula datas: dia, mes, ano, dia da semana
│   └── Agendamento.java             # Um evento agendado: disciplina + data + tipo
│
└── Interfaces/                       # A parte visual (o "rosto")
    ├── Horario.java                  # Tela da grade horaria semanal
    ├── Horario.form                  # Layout visual da tela de horario (NetBeans)
    ├── CalendarioMes.java            # Tela do calendario mensal
    └── CalendarioMes.form            # Layout visual do calendario (NetBeans)
```

A separacao entre `classes/` e `Interfaces/` nao e arbitraria: e a semente do padrao **MVC** (Model-View-Controller), onde a logica de negocios fica separada da interface visual. Aqui ainda nao esta perfeito, mas a intencao ja esta la.

---

## Os conceitos por tras de cada classe

| Classe | O que representa | Conceito principal |
|---|---|---|
| **CompromissoSemanal** | Algo que acontece toda semana num horario fixo | Classe base (superclasse) |
| **Aula** | Uma aula especifica, vinculada a uma disciplina | Heranca (extends CompromissoSemanal) |
| **Disciplina** | Uma materia da faculdade com nome e professor | Composicao (usada dentro de Aula e Agendamento) |
| **Data** | Uma data com dia, mes, ano e dia da semana | Uso da API `java.time.LocalDate` |
| **Agendamento** | Um evento agendado (prova, seminario, atividade) | Composicao de Disciplina + Data + tipo |

---

## Como rodar

1. Abra o projeto no **NetBeans** (ou outra IDE Java com suporte a Swing)
2. O NetBeans vai reconhecer os arquivos `.form` e montar a interface visual
3. Execute a classe `Horario.java` (ela tem o metodo `main`)
4. A janela da grade horaria vai abrir -- clique em qualquer celula para comecar a cadastrar!

---

## Requisitos

- **Java 8+** (usa switch expressions e text blocks, entao Java 14+ recomendado)
- **NetBeans IDE** (recomendado, para editar os arquivos `.form` visualmente)

---

## Sobre

Projeto academico desenvolvido durante o curso de **BCC - Bacharelado em Ciencia da Computacao**, como primeira experiencia pratica com Java, orientacao a objetos e interfaces graficas.

Esse projeto me ensinou que programar nao e memorizar sintaxe -- e transformar uma ideia em algo que funciona, que voce pode clicar, interagir e ver acontecendo na tela. E quando a janela abriu pela primeira vez com o meu codigo rodando dentro dela, eu soube que era isso que eu queria fazer.