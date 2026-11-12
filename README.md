# SGC: Sistema de Gestão de Clínica Médica

Protótipo navegável do **Sistema de Gestão de Clínica (SGC)**, desenvolvido para a AC (Exercício Integrado) da disciplina de **Projeto de Engenharia de Software**.

**Alunos:** Brenda Mendes Araujo (202209150008) e Matheus Guimarães Liporace (202302417949)

![Tela Agendar consulta](docs/img/agendar-consulta.png)

## Como abrir

O protótipo é um único arquivo, `index.html`, sem instalação nem servidor.

- **Online (GitHub Pages):** `https://<usuario>.github.io/sgc-prototipo/`
- **Local:** baixe o repositório e abra `index.html` em um navegador atual (Chrome, Edge, Firefox ou Safari).

Os dados são fictícios e ficam guardados apenas no navegador de quem abre a página. Para voltar ao estado inicial, use **Rastreabilidade → Restaurar dados de demonstração**.

## Contas de demonstração

| Usuário | Senha | Perfil | O que pode fazer |
|---|---|---|---|
| `recepcao` | `recep123` | Recepcionista | Cadastrar pacientes; agendar, remarcar e cancelar consultas |
| `admin` | `admin123` | Administrador | Tudo, mais usuários, permissões, backup e auditoria |
| `dr.ana` | `medico123` | Médico | Ver apenas a própria agenda |
| `dr.carlos` | `medico123` | Médico | Ver apenas a própria agenda |
| `maria` | `paciente123` | Paciente | Ver as próprias consultas e confirmar presença |

## Roteiro para a apresentação (cerca de 5 minutos)

1. Entre como **recepcao** e abra a aba **Agendar**.
2. **FA01, paciente não cadastrado:** busque "Zé Ninguém" e clique em *Cadastrar paciente e continuar*. Use o CPF de teste `529.982.247-25`.
3. **FA02, médico sem disponibilidade:** escolha *Dermatologia → Dra. Paula Ferreira* e clique numa segunda-feira (ela atende só às terças e quintas).
4. **FA04, campos obrigatórios:** clique em *Confirmar agendamento* sem escolher o horário.
5. **FA03 / RN01, conflito de horário:** escolha um horário, marque *Testar conflito* e confirme.
6. **Fluxo principal:** escolha outro horário e confirme. O cartão de consulta recebe o carimbo *AGENDADA* e a confirmação é enviada ao paciente.
7. **RF05:** na aba **Consultas**, remarque e cancele uma consulta.
8. **RN04:** entre como **admin**, vá em **Usuários** e desmarque *Cancelar consultas* do Recepcionista. Volte como **recepcao**: o cancelamento deixa de estar disponível.
9. **RF06 e RF07:** entre como **dr.ana** (Minha agenda) e como **maria** (Minhas consultas).

## Requisitos atendidos

| Requisito | Onde ver no protótipo |
|---|---|
| RF01 – Cadastrar e atualizar pacientes | Aba Pacientes |
| RF02 – Médicos e especialidades | Aba Médicos |
| RF03 – Horários disponíveis por médico e data | Agendar (etapa 3) e Agendas |
| RF04 – Agendar consultas | Agendar |
| RF05 – Remarcar ou cancelar | Consultas |
| RF06 – Médico vê a própria agenda | Minha agenda (perfil médico) |
| RF07 – Confirmação ao paciente | Janela de confirmação e Minhas consultas (perfil paciente) |
| RF08 – Autenticação e permissões por perfil | Login e Usuários |
| RNF01 – Navegadores Web atuais | HTML, CSS e JavaScript padrão, layout responsivo |
| RNF02 – Proteção de dados | Hash de senha, bloqueio após 5 tentativas, sessão com expiração, CPF mascarado para o médico, auditoria |
| RNF03 – Horários em até 3 s | Tempo medido e exibido na tela de agendamento |
| RNF04 – Backup e restauração | Aba Backup |
| RNF05 – Mensagens claras | Campos obrigatórios destacados e mensagens por regra |
| RN01 a RN04 | Validadas no serviço de agendamento (ver Rastreabilidade) |

A tabela completa, com o caminho de teste de cada item, está na aba **Rastreabilidade** do próprio protótipo.

## Documentação do projeto

O documento completo, [`docs/AC_SGC_Projeto_Completo.pdf`](docs/AC_SGC_Projeto_Completo.pdf), traz as sete seções da AC:

1. Fundamentação e processo (RUP)
2. Concepção e requisitos
3. Análise e projeto (UC01 e diagramas UML)
4. Construção (protótipo, modelo de dados e pseudocódigo)
5. Manual do Usuário: *Como agendar uma consulta*
6. Testes (11 casos e matriz de rastreabilidade)
7. Plano de Implantação e Aceitação

| Agenda do médico | Confirmação do agendamento |
|---|---|
| ![Agenda do médico](docs/img/agenda-medico.png) | ![Confirmação](docs/img/confirmacao.png) |

![Modelo de dados](docs/img/modelo-dados.png)

## Estrutura do repositório

```
index.html                         protótipo completo (interface, regras e dados de demonstração)
docs/AC_SGC_Projeto_Completo.pdf   documento da AC
docs/img/                          capturas de tela e modelo de dados
```

## Observações

- Trata-se de um protótipo acadêmico. Não há servidor: e-mails e SMS ao paciente são simulados dentro do sistema.
- Em produção, o projeto prevê um servidor de aplicação com banco relacional (PostgreSQL) e acesso por HTTPS (seção 4 do documento).
