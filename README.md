# 📋 Task Management System

Um sistema completo de gerenciamento de tarefas desenvolvido em Java com Spring Boot, oferecendo uma API REST robusta para criação, organização e acompanhamento de tarefas.

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1-green)
![JPA](https://img.shields.io/badge/JPA-Hibernate-blue)
![API](https://img.shields.io/badge/API-REST-red)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)

## 🚀 Funcionalidades

### ✅ Gerenciamento Completo de Tarefas
- **CRUD Completo**: Criar, listar, atualizar e excluir tarefas
- **Sistema de Prioridades**: LOW, MEDIUM, HIGH, CRITICAL
- **Controle de Status**: TODO, IN_PROGRESS, DONE, CANCELLED
- **Atribuição de Responsáveis**: Designar tarefas para membros da equipe
- **Estimativa de Tempo**: Controle de horas estimadas vs. horas reais

### 📊 Recursos Avançados
- **Paginação e Ordenação**: Listagem eficiente para grandes volumes
- **Busca por Palavras-chave**: Pesquisa inteligente em títulos e descrições
- **Filtros Avançados**: Por status, prioridade, responsável
- **Dashboard de Estatísticas**: Resumo executivo das tarefas
- **Detecção de Atrasos**: Identificação automática de tarefas vencidas

### 🔔 Sistema de Notificações
- **Lembretes Automáticos**: Notificações 24h antes do vencimento
- **Monitoramento Contínuo**: Verificação periódica de prazos
- **Alertas de Atraso**: Identificação de tarefas em atraso

### 🛡️ Qualidade e Confiabilidade
- **Validação Robusta**: Validação de dados com Bean Validation
- **Tratamento de Exceções**: Gerenciamento centralizado de erros
- **Logs Estruturados**: Rastreabilidade completa das operações
- **Transações Seguras**: Integridade de dados garantida

## 🛠️ Tecnologias Utilizadas

- **Java 17**: Linguagem de programação
- **Spring Boot 3.1**: Framework principal
- **Spring Data JPA**: Camada de persistência
- **Hibernate**: ORM (Object-Relational Mapping)
- **H2 Database**: Banco de dados em memória (desenvolvimento)
- **MySQL**: Banco de dados (produção)
- **Maven**: Gerenciamento de dependências
- **Bean Validation**: Validação de dados
- **JUnit 5**: Testes unitários
- **Mockito**: Mock de dependências

## 🏗️ Arquitetura do Projeto

```
📦 Arquitetura em Camadas
├── 🎮 Controller Layer    → Endpoints REST
├── 🔧 Service Layer       → Lógica de negócio
├── 💾 Repository Layer    → Acesso a dados
├── 🏷️ Model Layer         → Entidades e DTOs
└── ⚠️ Exception Layer    → Tratamento de erros
```

### Principais Componentes:
- **TaskController**: API REST com 12 endpoints
- **TaskService**: Lógica de negócio e regras
- **TaskRepository**: Queries customizadas com JPA
- **NotificationService**: Sistema de lembretes
- **GlobalExceptionHandler**: Tratamento centralizado

## 🚀 Como Executar

### Pré-requisitos
- Java 17 ou superior
- Maven 3.6+
- Git

### 1️⃣ Clone o repositório
```bash
git clone https://github.com/seu-usuario/task-management-system.git
cd task-management-system
```

### 2️⃣ Execute a aplicação
```bash
# Usando Maven
./mvnw spring-boot:run

# Ou compilando primeiro
./mvnw clean package
java -jar target/task-management-system-1.0.0.jar
```

### 3️⃣ Acesse a aplicação
- **API Base URL**: `http://localhost:8080/api/tasks`
- **H2 Console**: `http://localhost:8080/h2-console`

## 📖 Documentação da API

<div align="center">

### 📋 **CRUD de Tarefas**

| Método | Endpoint | Descrição | Parâmetros |
|--------|----------|-----------|------------|
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks` | Lista todas as tarefas | - |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/paginated` | Lista com paginação | `?page=0&size=10&sortBy=createdAt` |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/{id}` | Busca tarefa por ID | `{id}: Long` |
| <img src="https://img.shields.io/badge/-POST-49CC90?style=flat&logoColor=white" /> | `/api/tasks` | Cria nova tarefa | `Body: TaskDTO` |
| <img src="https://img.shields.io/badge/-PUT-FCA130?style=flat&logoColor=white" /> | `/api/tasks/{id}` | Atualiza tarefa completa | `{id}: Long` + `Body: TaskDTO` |
| <img src="https://img.shields.io/badge/-PATCH-50E3C2?style=flat&logoColor=white" /> | `/api/tasks/{id}/complete` | Marca como concluída | `{id}: Long` |
| <img src="https://img.shields.io/badge/-DELETE-F93E3E?style=flat&logoColor=white" /> | `/api/tasks/{id}` | Remove tarefa | `{id}: Long` |

### 🔍 **Filtros e Consultas Avançadas**

| Método | Endpoint | Descrição | Parâmetros |
|--------|----------|-----------|------------|
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/status/{status}` | Filtra por status | `status: TODO\|IN_PROGRESS\|DONE\|CANCELLED` |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/priority/{priority}` | Filtra por prioridade | `priority: LOW\|MEDIUM\|HIGH\|CRITICAL` |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/overdue` | Tarefas em atraso | - |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/search` | Busca por palavra-chave | `?keyword=string` |
| <img src="https://img.shields.io/badge/-GET-61AFFE?style=flat&logoColor=white" /> | `/api/tasks/summary` | Dashboard estatísticas | - |

</div>

### 📊 **Códigos de Resposta HTTP**

| Status Code | Descrição | Quando Ocorre |
|-------------|-----------|---------------|
| `200 OK` | Sucesso | GET, PUT, PATCH bem-sucedidos |
| `201 Created` | Criado | POST bem-sucedido |
| `204 No Content` | Sem conteúdo | DELETE bem-sucedido |
| `400 Bad Request` | Requisição inválida | Dados de entrada inválidos |
| `404 Not Found` | Não encontrado | Recurso não existe |
| `500 Internal Server Error` | Erro interno | Erro no servidor |

### 📝 Exemplos Práticos de Uso

#### 🟡 **Criando uma Nova Tarefa**

**Request:**
```bash
curl -X POST http://localhost:8080/api/tasks \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Implementar autenticação JWT",
    "description": "Adicionar sistema de autenticação com tokens JWT para segurança da API",
    "priority": "HIGH",
    "status": "TODO",
    "dueDate": "2024-12-31T23:59:59",
    "assignedTo": "dev@exemplo.com",
    "estimatedHours": 8
  }'
```

**Response (201 Created):**
```json
{
  "id": 1,
  "title": "Implementar autenticação JWT",
  "description": "Adicionar sistema de autenticação com tokens JWT para segurança da API",
  "priority": "HIGH",
  "status": "TODO",
  "dueDate": "2024-12-31T23:59:59",
  "assignedTo": "dev@exemplo.com",
  "estimatedHours": 8,
  "actualHours": null,
  "createdAt": "2024-01-15T10:30:00",
  "updatedAt": "2024-01-15T10:30:00"
}
```

#### 🟢 **Consultando Tarefas com Paginação**

**Request:**
```bash
curl -X GET "http://localhost:8080/api/tasks/paginated?page=0&size=5&sortBy=priority"
```

**Response (200 OK):**
```json
{
  "content": [
    {
      "id": 1,
      "title": "Bug crítico em produção",
      "priority": "CRITICAL",
      "status": "IN_PROGRESS"
    }
  ],
  "pageable": {
    "pageNumber": 0,
    "pageSize": 5,
    "sort": {
      "sorted": true,
      "by": "priority"
    }
  },
  "totalElements": 25,
  "totalPages": 5,
  "first": true,
  "last": false
}
```

#### 🔍 **Buscando Tarefas por Status**

**Request:**
```bash
curl -X GET http://localhost:8080/api/tasks/status/IN_PROGRESS
```

#### 📊 **Dashboard de Estatísticas**

**Request:**
```bash
curl -X GET http://localhost:8080/api/tasks/summary
```

**Response (200 OK):**
```json
{
  "totalTasks": 150,
  "todoTasks": 45,
  "inProgressTasks": 32,
  "doneTasks": 68,
  "overdueTasks": 5
}
```

#### ❌ **Exemplos de Erros**

**Validação de Dados (400 Bad Request):**
```json
{
  "status": 400,
  "errors": {
    "title": "Title is required",
    "priority": "Priority is required"
  },
  "timestamp": "2024-01-15T10:30:00"
}
```

**Tarefa Não Encontrada (404 Not Found):**
```json
{
  "status": 404,
  "message": "Task not found with id: 999",
  "timestamp": "2024-01-15T10:30:00"
}
```

### 🎯 **Testando a API**

#### **Opção 1: Usando cURL**
```bash
# Listar todas as tarefas
curl -X GET http://localhost:8080/api/tasks

# Criar uma tarefa simples
curl -X POST http://localhost:8080/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Minha primeira tarefa", "priority": "MEDIUM"}'
```

#### **Opção 2: Usando Postman**
1. Importe a collection: `task-management-postman-collection.json`
2. Configure a base URL: `http://localhost:8080`
3. Execute os requests de exemplo

#### **Opção 3: Usando httpie**
```bash
# Instalar httpie: pip install httpie
http GET localhost:8080/api/tasks
http POST localhost:8080/api/tasks title="Nova tarefa" priority="HIGH"
```

## 🧪 Testes

```bash
# Executar todos os testes
./mvnw test

# Executar com relatório de cobertura
./mvnw test jacoco:report
```

### Cobertura de Testes:
- **Service Layer**: 95%+
- **Controller Layer**: 90%+
- **Repository Layer**: 85%+

## 📊 Configurações de Ambiente

### Desenvolvimento (application.properties)
```properties
# Banco H2 em memória
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
spring.jpa.show-sql=true
```

### Produção (application-prod.properties)
```properties
# MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/task_management
spring.datasource.username=${DB_USERNAME:admin}
spring.datasource.password=${DB_PASSWORD:password}
spring.jpa.hibernate.ddl-auto=validate
```

## 🐳 Docker (Opcional)

```dockerfile
FROM openjdk:17-jdk-alpine
VOLUME /tmp
COPY target/task-management-system-1.0.0.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

```bash
# Build da imagem
docker build -t task-management-system .

# Executar container
docker run -p 8080:8080 task-management-system
```

## 🔮 Próximas Funcionalidades

### 🚧 Em Desenvolvimento
- [ ] **Autenticação JWT**: Sistema de login e autorização
- [ ] **Upload de Anexos**: Suporte a arquivos nas tarefas
- [ ] **Comentários**: Sistema de discussão por tarefa
- [ ] **Labels Customizadas**: Tags personalizáveis

### 💡 Planejado
- [ ] **API de Email**: Notificações por email
- [ ] **Dashboard Web**: Interface gráfica com React
- [ ] **Relatórios**: Exportação em PDF/Excel
- [ ] **Integrações**: Slack, Teams, Trello

## 📈 Melhorias Técnicas Futuras

- **Cache Redis**: Otimização de performance
- **Documentação Swagger**: API docs interativa
- **Métricas Actuator**: Monitoramento de saúde
- **CI/CD Pipeline**: Automação com GitHub Actions
- **Logs ELK Stack**: Centralizização de logs

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch: `git checkout -b feature/nova-funcionalidade`
3. Commit suas mudanças: `git commit -m 'Adiciona nova funcionalidade'`
4. Push para a branch: `git push origin feature/nova-funcionalidade`
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👨‍💻 Autor

**Seu Nome**
- GitHub: [Meu Usuario](https://github.com/Kertessz)
- LinkedIn: [Meu Perfil](https://www.linkedin.com/in/guilherme-kertes-da-costa-1483b3235/)
- Email: Guilhermekertes.celular@gmail.com


## 📊 Estatísticas do Projeto

![GitHub repo size](https://img.shields.io/github/repo-size/seu-usuario/task-management-system)
![GitHub language count](https://img.shields.io/github/languages/count/seu-usuario/task-management-system)
![GitHub top language](https://img.shields.io/github/languages/top/seu-usuario/task-management-system)
![GitHub last commit](https://img.shields.io/github/last-commit/seu-usuario/task-management-system)
