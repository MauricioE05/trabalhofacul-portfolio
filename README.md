# trabalhofacul-portfolio
Portfólio - Criando uma Base de Dados para um Sistema de Faculdade


1.	Projeto


Os proprietários de uma faculdade precisam de um sistema que viabilize o armazenamento de informações sobre seus alunos, cursos, matérias e professores para que seja possível realizar controles básicos como montar turmas e realizar o armazenamento de notas dos alunos.
Com base no que foi apresentado acima, o aluno deve criar um banco de dados que ofereça suporte para que um sistema possa armazenar informações que atendam a necessidade do cliente. Para facilitar o desenvolvimento do projeto, identifique respostas para as seguintes questões:
-	Quais são as principais necessidades dos clientes?

-	Quais informações precisam ser armazenadas?

-	Quais os dados precisam ser guardados?

-	O que será feito com os dados posteriormente?

-	Quais tabelas precisam ser criadas para que todas as informações sejam armazenadas?

-	Quais atributos cada tabela deve ter?

-	Qual o tipo de dados de cada atributo definido?

-	Quais são os relacionamentos a serem criados entre as tabelas?



2.	Objetivos


3.1	OBJETIVOS DE APRENDIZAGEM (PLANO DE APRENDIZAGEM):

-	Análise de requisitos

-	Modelagem conceitual

-	Modelagem lógica

-	Modelagem física
 
3.	Tabelas e Relacionamentos


Tabelas principais:

1.	Aluno

2.	Curso

3.	Matéria

4.	Professor

5.	Matrícula

6.	Nota



Relacionamentos:

-	Aluno se inscreve em Matrícula (1:N)

-	Matrícula pertence a um Curso (N:1)

-	Matéria pertence a um Curso (N:1)

-	Professor leciona uma ou mais Matérias (1:N)

-	Aluno recebe uma ou mais Notas (1:N)



Atributos das tabelas:

-	Aluno: ID_aluno, nome, CPF, data_nascimento, endereço, telefone

-	Curso: ID_curso, nome, duração

-	Matéria: ID_materia, nome, ID_curso

-	Professor: ID_professor, nome, CPF, área_ensino

-	Matrícula: ID_matricula, ID_aluno, ID_curso

-	Nota: ID_nota, ID_matricula, valor, data



Tipos de dados definidos:

-	ID: INTEGER (auto_increment)
 
-	Nome: VARCHAR(100)

-	CPF: VARCHAR(14)

-	Data: DATE

-	Valor: DECIMAL(5,2)



4.	Modelo Conceitual


Entidades principais:

1.	Aluno

2.	Curso

3.	Matéria

4.	Professor

5.	Matrícula

6.	Nota



Relacionamentos:

-	Aluno se inscreve em Matrícula (1:N)

-	Matrícula pertence a um Curso (N:1)

-	Matéria pertence a um Curso (N:1)

-	Professor leciona uma ou mais Matérias (1:N)

-	Aluno recebe uma ou mais Notas (1:N)



5.	Modelo Lógico


Tabelas e comandos SQL:



1.	tbl_alunos
 
CREATE TABLE tbl_alunos (

ID_aluno INT AUTO_INCREMENT PRIMARY KEY, nome VARCHAR(100),
CPF VARCHAR(14) UNIQUE,

data_nascimento DATE, endereco VARCHAR(255), telefone VARCHAR(15)
);



2.	tbl_cursos

CREATE TABLE tbl_cursos (

ID_curso INT AUTO_INCREMENT PRIMARY KEY, nome VARCHAR(100),
duracao INT

);



3.	tbl_materias

CREATE TABLE tbl_materias (

ID_materia INT AUTO_INCREMENT PRIMARY KEY, nome VARCHAR(100),
ID_curso INT,

FOREIGN KEY (ID_curso) REFERENCES tbl_cursos(ID_curso)

);



4.	tbl_professores

CREATE TABLE tbl_professores (

ID_professor INT AUTO_INCREMENT PRIMARY KEY,
 
nome VARCHAR(100),

CPF VARCHAR(14) UNIQUE,

area_ensino VARCHAR(50)

);



5.	tbl_matriculas

CREATE TABLE tbl_matriculas (

ID_matricula INT AUTO_INCREMENT PRIMARY KEY,

ID_aluno INT, ID_curso INT,
FOREIGN KEY (ID_aluno) REFERENCES tbl_alunos(ID_aluno), FOREIGN KEY (ID_curso) REFERENCES tbl_cursos(ID_curso)
);



6.	tbl_notas

CREATE TABLE tbl_notas (

ID_nota INT AUTO_INCREMENT PRIMARY KEY,

ID_matricula INT, valor DECIMAL(5, 2),
data DATE,

FOREIGN KEY (ID_matricula) REFERENCES tbl_matriculas(ID_matricula)

);



6.	Modelo Físico (Código SQL)


O código SQL foi preparado para criar as tabelas mencionadas acima. A relação entre as tabelas foi bem definida através das chaves estrangeiras e suas respectivas
 
chaves primárias.
