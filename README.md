# Relatório de Testes de QA - Página de Cursos

Este repositório contém a documentação completa dos testes de qualidade realizados na aplicação de gerenciamento de cursos. O foco da análise foi garantir a funcionalidade, segurança e integridade das regras de negócio.

---

## 1. Análise da Aplicação

### **Objetivo da Aplicação**
A plataforma é um sistema de gerenciamento administrativo (CRUD) simplificado para cursos. Seu objetivo é permitir que o usuário cadastre novos cursos, visualize a listagem atualizada e gerencie a base de dados (exclusão).

### **Principais Fluxos Disponíveis**
1.  **Cadastro de Cursos:** Preenchimento de formulário com nome, descrição, instrutor, datas, vagas, imagem da capa, tipo e local.
2.  **Listagem de Cursos:** Exibição dos cursos salvos na memória.
3.  **Exclusão de Registros:** Remoção de itens da lista através da interface.

### **Pontos Críticos para Teste**
* **Sanitização de Entradas:** Proteção contra ataques de injeção de código (XSS).
* **Persistência de Dados:** Validação do método de salvamento (Local Storage vs Banco de Dados).
* **Regras de Negócio de Data:** Impedir inconsistências temporais (Data fim < Data início).
* **Roteamento:** Garantir que a URL da aplicação seja acessível via refresh ou acesso direto.
* **Exclusão de registros:** Garantir que os registros sejam apagados corretamente.

---

## 2. Cenários e Casos de Teste

A estratégia de testes cobriu fluxos principais, cenários negativos e validações de campo. A documentação completa (utilizando **Gherkin** e **Passo a Passo**) está disponível na planilha abaixo dividida em duas abas ('CASOS-TESTE' e 'BUG-REPORT'):

**Link da planilha: https://docs.google.com/spreadsheets/d/1XkbZWNUmJnCPVLEBHBeTRFa2DRxRaeYqBCnpqcrGi4A/edit?usp=sharing**

---

## 3. Execução e Evidências

Todos os casos de teste foram executados manualmente. As evidências (gravações de tela) foram organizadas por ID de teste para facilitar a validação.

**Link das evidências: https://drive.google.com/drive/folders/18DA8sUTc4UCDbS0tdYawmT1A7lJg8n-x?usp=sharing**

---

## 4. Registro de Bugs

Durante o ciclo de testes, foram identificados problemas que impactam desde a usabilidade até a segurança crítica da aplicação. **Para mais detalhes sobre os bugs, consulte na página 'BUG-REPORT' no link da planilha disponibilizada no repositório**.

### **Tabela de Severidade**

| ID | Título do Bug | Severidade | Impacto |
| :--- | :--- | :--- | :--- |
| **BUG-001** | Vulnerabilidade de Cross-Site Scripting (XSS) no Cadastro | **Crítica** | Segurança |
| **BUG-002** | Falha na Exclusão de Curso (Erro 405 Method Not Allowed) | **Alta** | Funcionalidade |
| **BUG-003** | Erro de `JSON.parse` ao corromper dados no Local Storage | **Alta** | Estabilidade |
| **BUG-004** | Ausência de validação em campos obrigatórios (vazio) | **Média** | Integridade |
| **BUG-005** | Erro 404 Not Found ao atualizar página de cadastro | **Média** | UX/Navegação |
| **BUG-006** | Permite Data de Fim anterior à Data de Início | **Baixa** | Regra de Negócio |
| **BUG-007** | Aceitação de número de vagas negativo | **Baixa** | Regra de Negócio |

---
