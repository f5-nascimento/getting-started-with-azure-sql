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

<img width="1511" height="343" alt="sql do azure" src="https://github.com/user-attachments/assets/b53a60b3-eaf7-4a8a-833e-18bda88a2cda" />

- No campo de busca do portal, digite **SQL do Azure**
- Clique no ícone conforme a imagem acima.
- Ao carregar a tela principal do **SQL do Azure**, clique em **Criar** conforme a imagem acima.

---

### 3. Selecionar a opção de implantação do SQL e Configurações Básicas

<img width="1633" height="758" alt="implantação sql do azure" src="https://github.com/user-attachments/assets/8984dbcf-479f-4436-8ab9-e87d7b34fc85" />

- Na tela de implantação, selecione a opção Banco de Dados SQL.
- Tipo de recurso: Banco de dados individual.
- Clique em criar.
- Na nova tela, siga as demais informações.
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1`)
- **Grupo de recursos**: Selecione um existente (ex: `lab-sql`) ou clique em **Criar novo**
- **Nome do banco de dados**: ex: `exemplo-sql`
- **Servidor**: Selecione um existente (ex: `server-sql`) ou clique em **Criar novo**

---

### 4. Criar um Novo Servidor

- **Nome do servidor:** Defina um nome exclusivo para o servidor (ex: `server-sq255`)
- **Localização**: Escolha uma região próxima ou mais barata (ex: `West US 2`)
- **Autenticação**: Selecione **Usar autenticação SQL**
- **Logon do administrador do servidor**: Insira um nome de administrador (ex: `adminsql`) 
- **Senha**: Insira a senha de administrador (ex: `SQLadmin255`) 
- **Confirmar senha**: Repita a senha informada
- Clique em OK

---

### 5. Opções Adicionais

- **Deseja usar o pool elástico SQL?** marque não
- **Ambiente de carga de trabalho**: selecione `Desenvolvimento`
- **Redundância do armazenamento de backup**: selecione `Armazenamento de backup com redundância local`
- Clique em **Revisar e criar**
- Clique em **Criar**
- Uma mensagem de "A implantação foi concluída" deve ser exibida ao final do processo. Vide exemplo abaixo. 

<img width="1532" height="585" alt="image" src="https://github.com/user-attachments/assets/9fcf7613-1d64-4da3-a614-07d240201479" />


---

### 6. Adicionar Regra de Firewall

<img width="1488" height="746" alt="server" src="https://github.com/user-attachments/assets/057df3f7-a080-4d22-8f80-4c3e33e4a684" />

Após a implantação:

- Acesse o **servidor SQL** criado (não o banco de dados) clicando no nome do servidor, (ex: `server-sq255` conforme a imagem acima).
-  No menu lateral esquerdo, clique em **Segurança**.
- Em seguida, selecione a opção **Rede**.
- Em **Acesso público**, **marque a opção Redes selecionadas**.
- Em **Regras de Firewall**, clique em **+ Adicionar o endereço IPv4 do cliente**
- Clique em **Salvar**.
> ⚠️ Se essa etapa não for feita, você não conseguirá acessar o editor de consultas nem conectar com ferramentas externas.

---

### 7. Acessando o banco de Dados

<img width="1486" height="776" alt="bda" src="https://github.com/user-attachments/assets/9192118d-e3b7-4997-8709-c04b2749dc79" />

- Após a implantação, clique em **Ir para o recurso** para abrir o banco de dados criado.
- No **menu lateral esquerdo**, clique em **Editor de consultas (visualização)**.
- Será solicitado que você faça login com as credenciais definidas durante a criação do servidor.
- **Logon**: insira o nome de usuário definido (ex: `adminsql`)
- **Senha**: insira a senha definida (ex: `SQLadmin255`)
- Clique em **OK** para acessar o editor e começar a executar comandos SQL.

<img width="963" height="601" alt="acess" src="https://github.com/user-attachments/assets/b5ce7b67-7613-4da9-8a06-8be08bd9d7cb" />


---

### 8. Executar os Primeiros Comandos SQL - Criando a tabela Cursos

<img width="1352" height="562" alt="466248360-52c2225e-305a-4b33-8dfa-43c78905fbe5" src="https://github.com/user-attachments/assets/901dab62-386d-4fb5-a9ca-5c7cfe67effe" />

- Cole o seguinte código na área de consulta:
```sql
CREATE TABLE Cursos (
  id INT PRIMARY KEY IDENTITY,
  nome VARCHAR(100) NOT NULL,
  carga_horaria INT NOT NULL
);
```
> 💡 Observação: A sintaxe do SQL do Azure segue o padrão do SQL Server.
- Clique em Executar.
- Aguarde a mensagem de confirmação da execução (ex: `Êxito na consulta: Affected rows: 0`)
- Para atualizar a visualização das tabelas, clique no ícone de atualizar 🔄.
- Verifique que, em **Tabelas**, agora aparece dbo.Cursos com os campos definidos.

### 9. Executar os Primeiros Comandos SQL - Inserindo registros em Cursos

- Cole o seguinte código na área de consulta:
```sql
insert into cursos (nome, carga_horaria) values
('Programador Back-End',150),
('Programador Front-End',120),
('Operador de Sistemas Operacionais',250);
```
- Clique em Executar.

### 10. Executar os Primeiros Comandos SQL - Consultando registros em Cursos

- Cole o seguinte código na área de consulta:
```sql
select * from cursos;
```
- Clique em Executar.

### 11. Executar os Primeiros Comandos SQL - Criando a tabela Instrutores

- Cole o seguinte código na área de consulta:
```sql
create table instrutores(
id_instrutor int primary key identity,
nome_instrutor varchar(100),
);
```
- Clique em Executar.

### 12. Executar os Primeiros Comandos SQL - Inserindo Instrutores

- Cole o seguinte código na área de consulta:
```sql
insert into instrutores (nome_instrutor) values
('Eren Yeager'),
('Mikasa Ackerman');
```
- Clique em Executar.

### 13. Executar os Primeiros Comandos SQL - Consultando Instrutores

- Cole o seguinte código na área de consulta:
```sql
select * from instrutores;
```
- Clique em Executar.

### 14. Executar os Primeiros Comandos SQL - Criando a tabela Alocação

- Cole o seguinte código na área de consulta:
```sql
create table alocacao(
id_alocacao int primary key identity,
curso int,
instrutor int,
foreign key (curso) references cursos (id),
foreign key (instrutor) references instrutores (id_instrutor),
);
```
- Clique em Executar.

### 15. Executar os Primeiros Comandos SQL - Registrando Alocações

- Cole o seguinte código na área de consulta:
```sql
insert into alocacao (curso, instrutor) values
(1,2),
(2,2),
(3,1);
```
- Clique em Executar.

### 16. Executar os Primeiros Comandos SQL - Consultando Alocações

- Cole o seguinte código na área de consulta:
```sql
select nome as 'Curso', carga_horaria as 'Carga Horária', nome_instrutor as 'Instrutor' from alocacao 
join cursos on id = curso
join instrutores on id_instrutor = instrutor;
```
- Clique em Executar.

<img width="1585" height="702" alt="image" src="https://github.com/user-attachments/assets/117d0932-4746-4b48-bf8b-bdf6f9fa7f13" />
