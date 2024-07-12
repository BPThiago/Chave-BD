![Captura de tela 2024-07-12 232032](https://github.com/user-attachments/assets/aae241cd-b811-44db-b21b-479d41309a7f)# TRABALHO 01:  REC
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Caio Lessa Simão: caiolessa02@gmail.com<br>
Davidson Santos: email_segundo_componente@dominio.com<br>
Marcos Vinicius: email_segundo_componente@dominio.com<br>
Thiago Borges: thiagoborges980@gmail.com<br>

### 2.MINI-MUNDO<br>

O sistema proposto para a “REC” conterá as informações aqui detalhadas. Do Aluno se armazena o seu CPF, matrícula, nome, e status empregatício. De uma Empresa são coletados o CNPJ e nome. Um aluno pode estar estagiando em uma empresa, e cada empresa pode estagiar vários alunos. Os dados relativos ao Agente Integrador envolvem a presença de um CPF e nome. Um aluno pode ser assessorado por um agente, e um agente é empregado por uma empresa que pode possuir vários agentes. Um orientador é atribuído a alunos, do Orientador é registrado o CPF, matrícula e nome. O aluno possui apenas um orientador. Um aluno pode abrir chamados, de um Chamado registra-se a sua descrição e status de atendimento por um servidor. Do Servidor, armazena-se informações relativas ao seu CPF, matrícula e nome. Um servidor pode ser atribuído a vários chamados.

### 3.PERGUNTAS A SEREM RESPONDIDAS<br>
#### 3.1 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    Relatório que mostre os chamados em aberto por dado aluno;
    Relatório que apresente as empresas que mais contratam estagiários do Campus;
    Relatório relativo aos orientadores e alunos. O resultado deve exibir o nome do orientador e o nome do aluno supervisado;
    Relatório que apresente os chamados aprovados no último mês;
    Relatório relativo aos alunos e empresas. O resultado deve exibir o nome e matrícula do aluno, junto de informações relativas à empresa que o emprega (Considerar apenas alunos que 
    estão trabalhando).
    
### 5.MODELO CONCEITUAL<br>
    A) Utilizar a Notação adequada (Preferencialmente utilizar o BR Modelo 3)
    B) O mínimo de entidades do modelo conceitual pare este trabalho será igual a 3 e o Máximo 5.
        * informe quais são as 3 principais entidades do sistema em densenvolvimento<br>(se houverem mais de 3 entidades, pense na importância da entidade para o sistema)       
    C) Principais fluxos de informação/entidades do sistema (mínimo 3). <br>Dica: normalmente estes fluxos estão associados as tabelas que conterão maior quantidade de dados 
    D) Qualidade e Clareza
        Garantir que a semântica dos atributos seja clara no esquema (nomes coerentes com os dados).
        Criar o esquema de forma a garantir a redução de informação redundante, possibilidade de valores null, 
        e tuplas falsas (Aplicar os conceitos de normalização abordados).   
        
![Alt text](https://github.com/user-attachments/assets/59849f7d-7997-4f5d-9018-c5eeb7f43217 "Modelo Conceitual")

    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: Ana Júlia Caetano, Jéssica Duque, Matheus Caldas
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 
ALUNO: Tabela que armazena as informações do aluno.
	id: campo chave primária da tabela ALUNO;
	cpf: campo que armazena o Cadastro de Pessoa Física dos alunos;
	matricula: campo que armazena a matrícula dos alunos;
	nome: campo que armazena o nome completo dos alunos;
	status: campo que armazena a informação que diz se o aluno está ou não empregado;
	FK_AGENTE_id: campo que armazena a chave estrangeira do relacionamento com o agente integrador;
	FK_EMPRESA_id: campo que armazena a chave estrangeira do relacionamento com uma empresa.
	FK_ORIENTADOR_id: campo que armazena a chave estrangeira do relacionamento com um orientador;
EMPRESA: Tabela que armazena as informações das empresas.
	id: chave primária da tabela EMPRESA;
	cnpj: campo que armazena o Cadastro Nacional de Pessoa Jurídica da empresa;
	nome: campo que armazena o nome da empresa.

AGENTE: Tabela que armazena as informações dos agentes de integração.
	id: chave primária da tabela AGENTE;
	nome: campo que armazena o nome do agente de integração;
	cpf: campo que armazena o Cadastro de Pessoa Física do agente de integração;
	FK_EMPRESA_id: campo que armazena a chave estrangeira do relacionamento com uma empresa.

ORIENTADOR: Tabela que armazena as informações dos orientadores.
	id: chave primária da tabela ORIENTADOR;
	nome: campo que armazena o nome do orientador;
	cpf: campo que armazena o Cadastro de Pessoa Física do orientador;
	matrícula: campo que armazena a matrícula do orientador;

CHAMADO: tabela que armazena as informações do chamado aberto pelo aluno.
	id: chave primária da tabela CHAMADO;
	desc: campo que armazena as informações preenchidas pelo aluno;
	status: campo que armazena o estado de aprovação ou reprovação do chamado;
	FK_ALUNO_id: campo que armazena a chave estrangeira do relacionamento com o aluno;
	FK_SERVIDOR_id: campo que armazena a chave estrangeira do relacionamento com o servidor;

SERVIDOR: tabela que armazena as informações do SERVIDOR.
	id: chave primária da tabela SERVIDOR;
	cpf: campo que armazena o Cadastro de Pessoa Física do servidor;
	nome: campo que armazena o nome do servidor;
	matrícula: campo que armazena a matrícula do servidor.


># Marco de Entrega 01: Do item 1 até o item 5.2 (5 PTS) <br> 

### 6	MODELO LÓGICO<br>
        a) inclusão do esquema lógico do banco de dados
        b) verificação de correspondencia com o modelo conceitual 
        (não serão aceitos modelos que não estejam em conformidade)

![Alt text](https://github.com/user-attachments/assets/28f341e8-ab3c-4867-9ac1-0053c2a86f98 "Modelo Lógico")

### 7	MODELO FÍSICO<br>
      
DROP TABLE IF EXISTS ALUNO;
CREATE TABLE ALUNO (
    id int PRIMARY KEY,
    cpf varchar(150),
    matricula varchar(150),
    nome varchar(150),
    status varchar(150),
    FK_AGENTE_id int,
    FK_EMPRESA_id int,
    FK_ORIENTADOR_id int
);
DROP TABLE IF EXISTS EMPRESA;
CREATE TABLE EMPRESA (
    id int PRIMARY KEY,
    cnpj varchar(150),
    nome varchar(150)
);

DROP TABLE IF EXISTS AGENTE;
CREATE TABLE AGENTE (
    id int PRIMARY KEY,
    nome varchar(150),
    cpf varchar(150),
    FK_EMPRESA_id int
);

DROP TABLE IF EXISTS CHAMADO;
CREATE TABLE CHAMADO (
    id int PRIMARY KEY,
    desc varchar(150),
    status varchar(150),
    dt_abertura timestamp,
    dt_fechamento timestamp,
    FK_ALUNO_id int,
    FK_SERVIDOR_id int
);

DROP TABLE IF EXISTS SERVIDOR;
CREATE TABLE SERVIDOR (
    cpf varchar(150),
    id int PRIMARY KEY,
    nome varchar(150),
    matricula varchar(150)
);

DROP TABLE IF EXISTS ORIENTADOR;
CREATE TABLE ORIENTADOR (
    matricula varchar(150),
    cpf varchar(150),
    id int PRIMARY KEY,
    nome varchar(150)
);
 
ALTER TABLE ALUNO ADD CONSTRAINT FK_ALUNO_1
    FOREIGN KEY (FK_AGENTE_id)
    REFERENCES AGENTE (id)
    ON DELETE SET NULL;
 
ALTER TABLE ALUNO ADD CONSTRAINT FK_ALUNO_2
    FOREIGN KEY (FK_EMPRESA_id)
    REFERENCES EMPRESA (id)
    ON DELETE SET NULL;
 
ALTER TABLE ALUNO ADD CONSTRAINT FK_ALUNO_3
    FOREIGN KEY (FK_ORIENTADOR_id)
    REFERENCES ORIENTADOR (id)
    ON DELETE SET NULL;
 
ALTER TABLE AGENTE ADD CONSTRAINT FK_AGENTE_1
    FOREIGN KEY (FK_EMPRESA_id)
    REFERENCES EMPRESA (id)
    ON DELETE CASCADE;
 
ALTER TABLE CHAMADO ADD CONSTRAINT FK_CHAMADO_1
    FOREIGN KEY (FK_ALUNO_id)
    REFERENCES ALUNO (id)
    ON DELETE CASCADE;
 
ALTER TABLE CHAMADO ADD CONSTRAINT FK_CHAMADO_2
    FOREIGN KEY (FK_SERVIDOR_id)
    REFERENCES SERVIDOR (id)
    ON DELETE CASCADE;


      
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        -- Inserts para a tabela ALUNO
INSERT INTO ALUNO (id, cpf, matricula, nome, status, FK_AGENTE_id, FK_EMPRESA_id, FK_ORIENTADOR_id) VALUES (1, '123.456.789-01', '2022001', 'Ana Silva', 'Ativo', 1, 1, 1), (2, '234.567.890-02', '2022002', 'Bruno Costa', 'Ativo', 2, 2, 2), (3, '345.678.901-03', '2022003', 'Carlos Oliveira', 'Inativo', 3, 3, 3), (4, '456.789.012-04', '2022004', 'Daniela Pereira', 'Ativo', 4, 4, 4), (5, '567.890.123-05', '2022005', 'Eduardo Santos', 'Ativo', 5, 5, 5);

	-- Inserts para a tabela EMPRESA
INSERT INTO EMPRESA (id, cnpj, nome) VALUES (1, '12.345.678/0001-01', 'Empresa A'), (2, '23.456.789/0001-02', 'Empresa B'), (3, '34.567.890/0001-03', 'Empresa C'), (4, '45.678.901/0001-04', 'Empresa D'), (5, '56.789.012/0001-05', 'Empresa E');

	-- Inserts para a tabela AGENTE
INSERT INTO AGENTE (id, nome, cpf, FK_EMPRESA_id) VALUES (1, 'João Agente', '789.012.345-67', 1), (2, 'Maria Agente', '890.123.456-78', 2), (3, 'Pedro Agente', '901.234.567-89', 3), (4, 'Paula Agente', '012.345.678-90', 4), (5, 'Lucas Agente', '123.456.789-01', 5);

	-- Inserts para a tabela CHAMADO
INSERT INTO CHAMADO (id, descricao, status, dt_abertura, dt_fechamento, FK_ALUNO_id, FK_SERVIDOR_id) VALUES (1, 'Problema na matrícula', 'Aberto', '2023-07-01 10:00:00', NULL, 1, 1), (2, 'Dúvida sobre estágio', 'Fechado', '2023-07-02 11:00:00', '2023-07-03 12:00:00', 2, 2), (3, 'Solicitação de documentos', 'Aberto', '2023-07-03 12:00:00', NULL, 3, 3), (4, 'Erro no sistema', 'Fechado', '2023-07-04 13:00:00', '2023-07-05 14:00:00', 4, 4), (5, 'Atualização de dados', 'Aberto', '2023-07-05 14:00:00', NULL, 5, 5);

	-- Inserts para a tabela SERVIDOR
INSERT INTO SERVIDOR (id, cpf, nome, matricula) VALUES (1, '678.901.234-56', 'Servidor 1', 'S001'), (2, '789.012.345-67', 'Servidor 2', 'S002'), (3, '890.123.456-78', 'Servidor 3', 'S003'), (4, '901.234.567-89', 'Servidor 4', 'S004'), (5, '012.345.678-90', 'Servidor 5', 'S005');

	-- Inserts para a tabela ORIENTADOR
INSERT INTO ORIENTADOR (id, cpf, nome, matricula) VALUES (1, '456.789.012-34', 'Orientador 1', 'O001'), (2, '567.890.123-45', 'Orientador 2', 'O002'), (3, '678.901.234-56', 'Orientador 3', 'O003'), (4, '789.012.345-67', 'Orientador 4', 'O004'), (5, '890.123.456-78', 'Orientador 5', 'O005');


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    OBS: Usa template da disciplina disponibilizado no Colab.<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>

#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

># Marco de Entrega 02: Do item 6. até o item 9.1 (5 PTS) <br>

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 03: Do item 9.2 até o ítem 9.10 (10 PTS)<br>

### 10 RELATÓRIOS E GRÁFICOS

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 04: Itens 10 e 11 (20 PTS) <br>
<br>
<br>




### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


