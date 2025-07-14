# Criando um SQL do Azure pelo Portal
Este repositório contém um passo a passo detalhado para a criação e uso de um Banco de Dados SQL no Azure, diretamente pelo portal, sem a necessidade de ferramentas externas.

---

## ✅ Objetivo

Fornecer um tutorial prático e acessível para:

- Criar um Banco de Dados SQL no Azure
- Configurar o acesso via portal
- Executar comandos SQL diretamente no navegador

---

## 🧭 Etapas

### 1. Acesse o Portal do Azure

- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Faça login com sua conta Microsoft.

---

### 2. Criar um Banco de Dados SQL

1. No campo de busca do portal, digite **SQL Database**
2. Clique em **Criar**

---

### 3. Configuração Básica

- **Tipo de recurso**: `Banco de dados individual`
- **Assinatura**: Selecione sua assinatura ativa
- **Grupo de recursos**: Selecione um existente (ex: `lab-recursos`) ou crie um novo
- **Nome do banco de dados**: ex: `exemplo-sql`
- **Servidor**: Clique em **Criar novo**

---

### 4. Criar um Novo Servidor

- Defina um nome exclusivo para o servidor (ex: `labserver-exemplosql`)
- **Localização**: Escolha uma região próxima ou mais barata (ex: `East US 2`)
- **Método de autenticação**: Selecione **Autenticação SQL**
- Informe um nome de administrador (ex: `adminsql`) e uma senha forte

---

### 5. Opções Adicionais

- **Ambiente de carga de trabalho**: selecione `Desenvolvimento`
- **Redundância**: selecione `Local`
- Clique em **Avançar** ou vá direto para **Examinar e criar**

---

### 6. Adicionar Regra de Firewall

Após a implantação:

1. Acesse o **servidor SQL** criado (não o banco de dados).
2. Vá em **Rede** ou **Firewall e redes virtuais**.
3. Clique em **+ Adicionar o endereço IP do cliente atual**
4. Salve.

> ⚠️ Se essa etapa não for feita, você não conseguirá acessar o editor de consultas nem conectar com ferramentas externas.

---

### 7. Utilizar o Editor de Consultas no Portal

1. Acesse o seu banco de dados no portal.
2. No menu lateral, clique em **Editor de consultas (versão prévia)**
3. Faça login com o nome de usuário e senha definidos no servidor.

---

### 8. Executar os Primeiros Comandos SQL

Cole e execute o seguinte código:

```sql
CREATE TABLE Cursos (
  id INT PRIMARY KEY IDENTITY(1,1),
  nome NVARCHAR(100) NOT NULL,
  carga_horaria INT NOT NULL,
  ativo BIT DEFAULT 1
);

INSERT INTO Cursos (nome, carga_horaria) VALUES
('Back End', 80),
('Administrador de Banco de Dados', 200),
('Programação Mobile', 200);

SELECT * FROM Cursos;
