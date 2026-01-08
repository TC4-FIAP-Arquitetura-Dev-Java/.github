# Tech Challenge da instituição FIAP para o curso pós-graduação em Arquitetura e Desenvolvimento Java

### 📄 [Documentação Oficial do Desafio](https://docs.google.com/document/d/1WYRWwu2LtzAQk7JSGeTKBEoJ7vOuspLfpe-7FJTxsTY/edit?usp=sharing)
### 🎥 Vídeo - [URL](https://youtu.be/WCJVxM59BmQ) 

## Arquitetura de Microsserviços - Gerenciamento de feedbacks - Plataforma de curso on-line

### 📌 Descrição da Arquitetura

Este projeto foi desenvolvido com base em três pilares arquiteturais:

- **Microsserviços**
- **Arquitetura Clean Arch**
- **API First**

A aplicação está dividida em quatro microsserviços independentes:

### 🧩 Microsserviços

#### 🔹 ms-login
Responsável pelas operações de **Criação de AccessToken**, **Criação de RefreshToken**, **Cancalmento de Token** e **Criação de Aluno**.

#### 🔹 ms-usuario
Responsável pelas operações de **cadastro**, **atualização**, **exclusão**, **consulta** de usuários.

#### 🔹 ms-feedback
Responsável pelas operações de **cadastro**, **atualização**, **exclusão**, **consulta** de gerenciamento de feedbacks e **criação de report semanal**.

Ambos os microsserviços foram implementados com a linguagem **Java 21**, utilizando o framework **Spring Boot** para desenvolvimento, injeção de dependência e exposição de endpoints REST.

### 🧩 Funções GCP

#### 🔹 notification
Responsável pela operação de **enviar e-mail** pela GCP.

#### 🔹 report
Responsável pela operação de **gerar relatório** semanal de feedbacks.

---

### ⚙️ Tecnologias Utilizadas

- **Linguagem e Frameworks**: Java 21, Spring Boot, Spring Data JPA  
- **Gerenciamento de Dependências**: Maven e Gradle  
- **Banco de Dados**:  
  - MySQL 8.3 (Docker)  
  - PostgreSQL (Docker)  
  - H2 (para testes locais)  
- **Documentação de API**: OpenAPI/Swagger (API First)  
- **MapStruct**: Mapeamento entre entidades e DTOs  
- **Lombok**: Redução de boilerplate  
- **Git**: Controle de versão  
- **Docker**: Conteinerização  
- **RabbitMQ**: Envio de eventos
- **GraphQL**: Retorno dos endpoints customizado com queries.
- **Conteinerização**: Utilização de Docker com Dockerfiles para empacotamento dos microsserviços.
- **Cloud**: GCP (Google Cloud Platform) - Google Cloud Functions, Google Cloud Run, Google Cloud SQL, Cloud Scheduler

---

### 🧪 Estratégia de Testes

- **Testes Unitários**: JUnit 5 e Mockito  
- **Testes de API**: via Postman (coleções manuais ou automatizadas)

---

### 📊 Diagrama da Arquitetura

![Diagrama da Arquitetura](../imagens/diagrama-arquitetura.svg)

---

## 🐳 Execução do Projeto com Docker Compose

## ✅ Pré-requisitos

Antes de executar os scripts, instale os seguintes softwares:

| Requisito   | Descrição                                                                 |
|-------------|---------------------------------------------------------------------------|
| [Docker](https://www.docker.com/)       | Necessário para rodar os containers dos bancos de dados.           |
| [Java JRE 21+](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) | Recomendado pelo menos JRE 21 para execução dos projetos.          |
| [Postman](https://www.postman.com/downloads/)     | Para testar as collections de API.                                 |
| [DBeaver](https://dbeaver.io/download/) | Opcional, para visualizar os bancos de dados de forma gráfica.     |
| Git         | Para clonar os repositórios automaticamente.               |

---

## 💻 Como usar

### 🐧 Linux ou macOS

1. Abra o terminal
2. Dê permissão de execução ao script:
   ```bash
   chmod +x setup.sh
   ```
3. Execute o script:
   ```bash
   ./setup.sh
   ```

---

### 🪟 Windows

1. Dê duplo clique no arquivo `setup.bat`  
   Ou abra o terminal no diretório e execute:
   ```cmd
   setup.bat
   ```

---

## 🛠️ O que o script faz?

- Clona os repositórios:
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/ms-usuario`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/ms-login`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/ms-feedback`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/notification`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/report`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/collections`
  - `https://github.com/TC4-FIAP-Arquitetura-Dev-Java/docker`

- Cria um arquivo `docker-compose.yml` com dois bancos (MySQL e PostgreSQL)
- Cria volumes dedicados para persistência de dados
- Inicia os containers com `docker compose up -d`

---

## 🔍 Observações

- Os containers de banco sobem automaticamente, mas os microsserviços precisam ser iniciados via IDE ou terminal (caso queira rodá-los manualmente).
- Você pode usar o Postman para testar endpoints com as collections fornecidas nos projetos.

---

## 📁 Estrutura esperada após execução

```
/seu-diretorio/
│
├── data/
├── ms-login/
├── ms-usuario/
├── ms-feedback/
├── docker-compose.yml
├── setup.sh
└── setup.bat
```
