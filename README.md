📋 Task Management System
Um sistema completo de gerenciamento de tarefas desenvolvido em Java com Spring Boot, oferecendo uma API REST robusta para criação, organização e acompanhamento de tarefas.

🚀 Funcionalidades
✅ Gerenciamento Completo de Tarefas

CRUD Completo: Criar, listar, atualizar e excluir tarefas
Sistema de Prioridades: LOW, MEDIUM, HIGH, CRITICAL
Controle de Status: TODO, IN_PROGRESS, DONE, CANCELLED
Atribuição de Responsáveis: Designar tarefas para membros da equipe
Estimativa de Tempo: Controle de horas estimadas vs. horas reais

📊 Recursos Avançados

Paginação e Ordenação: Listagem eficiente para grandes volumes
Busca por Palavras-chave: Pesquisa inteligente em títulos e descrições
Filtros Avançados: Por status, prioridade, responsável
Dashboard de Estatísticas: Resumo executivo das tarefas
Detecção de Atrasos: Identificação automática de tarefas vencidas

🔔 Sistema de Notificações

Lembretes Automáticos: Notificações 24h antes do vencimento
Monitoramento Contínuo: Verificação periódica de prazos
Alertas de Atraso: Identificação de tarefas em atraso

🛡️ Qualidade e Confiabilidade

Validação Robusta: Validação de dados com Bean Validation
Tratamento de Exceções: Gerenciamento centralizado de erros
Logs Estruturados: Rastreabilidade completa das operações
Transações Seguras: Integridade de dados garantida

🛠️ Tecnologias Utilizadas

Java 17: Linguagem de programação
Spring Boot 3.1: Framework principal
Spring Data JPA: Camada de persistência
Hibernate: ORM (Object-Relational Mapping)
H2 Database: Banco de dados em memória (desenvolvimento)
MySQL: Banco de dados (produção)
Maven: Gerenciamento de dependências
Bean Validation: Validação de dados
JUnit 5: Testes unitários
Mockito: Mock de dependências

🏗️ Arquitetura do Projeto
📦 Arquitetura em Camadas
├── 🎮 Controller Layer    → Endpoints REST
├── 🔧 Service Layer       → Lógica de negócio
├── 💾 Repository Layer    → Acesso a dados
├── 🏷️ Model Layer         → Entidades e DTOs
└── ⚠️ Exception Layer    → Tratamento de erros
Principais Componentes:

TaskController: API REST com 12 endpoints
TaskService: Lógica de negócio e regras
TaskRepository: Queries customizadas com JPA
NotificationService: Sistema de lembretes
GlobalExceptionHandler: Tratamento centralizado

🚀 Como Executar
Pré-requisitos

Java 17 ou superior
Maven 3.6+
Git

1️⃣ Clone o repositório
bashgit clone https://github.com/seu-usuario/task-management-system.git
cd task-management-system
2️⃣ Execute a aplicação
bash# Usando Maven
./mvnw spring-boot:run

# Ou compilando primeiro
./mvnw clean package
java -jar target/task-management-system-1.0.0.jar
3️⃣ Acesse a aplicação

API Base URL: http://localhost:8080/api/tasks
H2 Console: http://localhost:8080/h2-console

📖 Documentação da API
🔗 Endpoints Principais
Tarefas
MétodoEndpointDescriçãoGET/api/tasksLista todas as tarefasGET/api/tasks/paginatedLista com paginaçãoGET/api/tasks/{id}Busca por IDPOST/api/tasksCria nova tarefaPUT/api/tasks/{id}Atualiza tarefaDELETE/api/tasks/{id}Remove tarefaPATCH/api/tasks/{id}/completeMarca como concluída
Filtros e Buscas
MétodoEndpointDescriçãoGET/api/tasks/status/{status}Filtra por statusGET/api/tasks/priority/{priority}Filtra por prioridadeGET/api/tasks/overdueLista tarefas em atrasoGET/api/tasks/search?keyword=termoBusca por palavra-chaveGET/api/tasks/summaryDashboard de estatísticas
📝 Exemplo de Payload
Criar Tarefa
json{
  "title": "Implementar autenticação JWT",
  "description": "Adicionar sistema de autenticação com tokens JWT",
  "priority": "HIGH",
  "status": "TODO",
  "dueDate": "2024-12-31 23:59:59",
  "assignedTo": "dev@exemplo.com",
  "estimatedHours": 8
}
Resposta de Sucesso
json{
  "id": 1,
  "title": "Implementar autenticação JWT",
  "description": "Adicionar sistema de autenticação com tokens JWT",
  "priority": "HIGH",
  "status": "TODO",
  "dueDate": "2024-12-31 23:59:59",
  "assignedTo": "dev@exemplo.com",
  "estimatedHours": 8,
  "actualHours": null,
  "createdAt": "2024-01-15 10:30:00",
  "updatedAt": "2024-01-15 10:30:00"
}
🧪 Testes
bash# Executar todos os testes
./mvnw test

# Executar com relatório de cobertura
./mvnw test jacoco:report
Cobertura de Testes:

Service Layer: 95%+
Controller Layer: 90%+
Repository Layer: 85%+

📊 Configurações de Ambiente
Desenvolvimento (application.properties)
properties# Banco H2 em memória
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
spring.jpa.show-sql=true
Produção (application-prod.properties)
properties# MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/task_management
spring.datasource.username=${DB_USERNAME:admin}
spring.datasource.password=${DB_PASSWORD:password}
spring.jpa.hibernate.ddl-auto=validate
🐳 Docker (Opcional)
dockerfileFROM openjdk:17-jdk-alpine
VOLUME /tmp
COPY target/task-management-system-1.0.0.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
bash# Build da imagem
docker build -t task-management-system .

# Executar container
docker run -p 8080:8080 task-management-system
🔮 Próximas Funcionalidades
🚧 Em Desenvolvimento

 Autenticação JWT: Sistema de login e autorização
 Upload de Anexos: Suporte a arquivos nas tarefas
 Comentários: Sistema de discussão por tarefa
 Labels Customizadas: Tags personalizáveis

💡 Planejado

 API de Email: Notificações por email
 Dashboard Web: Interface gráfica com React
 Relatórios: Exportação em PDF/Excel
 Integrações: Slack, Teams, Trello

📈 Melhorias Técnicas Futuras

Cache Redis: Otimização de performance
Documentação Swagger: API docs interativa
Métricas Actuator: Monitoramento de saúde
CI/CD Pipeline: Automação com GitHub Actions
Logs ELK Stack: Centralizização de logs

🤝 Contribuição

Faça um fork do projeto
Crie uma branch: git checkout -b feature/nova-funcionalidade
Commit suas mudanças: git commit -m 'Adiciona nova funcionalidade'
Push para a branch: git push origin feature/nova-funcionalidade
Abra um Pull Request

📄 Licença
Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.
👨‍💻 Autor
Guilherme Kertes da Costa

GitHub: @Kertessz
LinkedIn: [Meu Perfil](https://www.linkedin.com/in/guilherme-kertes-da-costa-1483b3235/)
Email: Guilhermekertes.celular@gmail.com
