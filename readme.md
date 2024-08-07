# TRABALHO 01:  REC
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Caio Lessa Simão: caiolessa02@gmail.com<br>
Davidson Santos: davidsonifes@gmail.com<br>
Marcos Santos: marcosviniciussouzadossantos19@gmail.com<br>
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
        
![Alt text](https://github.com/user-attachments/assets/59849f7d-7997-4f5d-9018-c5eeb7f43217 "Modelo Conceitual")

    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: Ana Júlia Caetano, Jéssica Duque, Matheus Caldas
    [Grupo02]: Alex Rossoni, João Pedro Pagotto, Sofia de Alcantara, Thiago Carvalho e Wal Candeia

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

### 6	MODELO LÓGICO<br>

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
	    descricao varchar(150),
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

[Arquivo com os inserts desenvolvidos pelo grupo](insert.sql)

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>

[Arquivo com as tabelas e consultas](Consultas.ipynb)	

### 10 RELATÓRIOS E GRÁFICOS

[Arquivo com os relatórios](Relatórios.ipynb)
    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

[link da apresentação](https://docs.google.com/presentation/d/1jLz47Qol2sznL1x41Jmib61ksxadoKCqvW2yiubm6Mk/edit?usp=sharing)

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


