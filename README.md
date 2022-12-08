
# Codigo da criação da Tabela 

 TB_ALUNO
```sql
CREATE table TB_ALUNO
(
      codigo_aluno int primary key,
      nome_aluno varchar(60) not null,
      ano_nasc int,
      email varchar(60),
      sexo varchar
);
```
 TB_CURSO
````sql
CREATE table TB_CURSO
(
       codigo_curso int primary key,
       nome_curso varchar(60) not null
);
````
 TB_MATRICULA
````sql
CREATE table TB_MATRICULA(
       codigo_curso int references tb_curso(codigo_curso),
       codigo_aluno int references tb_aluno(codigo_aluno)
)
````
# Dados inseridos nas tabelas

#TB_ALUNO
````sql
select * from tb_aluno

insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('1', 'Josiel Jardim', 1974, 'josiel@provaSQL.com.br', 'M')
values ('2', 'Ana Maria', 1980, 'ana@provaSQL.com.br', 'F')
values ('3', 'João Pedro', 1979, 'joao@provaSQL.com.br', 'M')
````
#TB_CURSO
````sql
select * from tb_curso

insert into tb_curso(codigo_curso, nome_curso)
values ('1', 'Medicina')
values ('2', 'Arquitetura')
values ('3', 'Filosofia')
values ('4', 'Informática')
values ('5', 'Jornalismo')
````
#TB_MATRICULA
````sql
select * from tb_matricula

insert into tb_matricula(codigo_curso, codigo_aluno)
values ('1', '1')
values ('1', '2')
values ('2', '3')
values ('5', '3');
````

# Resolução da Prova Prática Banco de Dados

## 1ª Questão
Faça um comando SQL para matricular o aluno “Pedro César” no curso de
Informática. Os dados devem ser inseridos na tabela TB_MATRÍCULA.

```sql
select * from tb_aluno

insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('4', 'Pedro César', '1995-06-04', 'pedro@provaSQL.com.br', 'M')

select * from tb_matricula

insert into tb_matricula(codigo_curso, codigo_aluno)
values ('4', '4')
```
## Resultado esperado

![01 1](https://user-images.githubusercontent.com/105735037/206176091-7338ef90-0c20-4b06-829f-4a67bee387dd.PNG)
<br/>
![01 3](https://user-images.githubusercontent.com/105735037/206176159-b302f3f4-775c-4a3c-910a-7e0c40d737f0.PNG)

## 2ª Questão
Escreva um comando SQL que retorne os nomes dos alunos e do(s) cursos em
que estão matriculados. Os dados deverão estar ordenados pelo nome do curso.

```sql
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_matricula
on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso
on tb_curso.codigo_curso = tb_matricula.codigo_curso
```
## Resultado esperado

![02 1](https://user-images.githubusercontent.com/105735037/206176693-7e69f727-cb83-41f3-99d7-150f24229578.PNG)


## 3ª Questão
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.
```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado esperado

![03 1](https://user-images.githubusercontent.com/105735037/206177445-77628b6b-ed61-4856-a2e0-2b5723be1998.PNG)

## 4ª Questão
Desenvolva um comando SQL que mostre o total de alunos.
```sql
select count(codigo_aluno)
from tb_aluno
```
## Resultado esperado

![04 1](https://user-images.githubusercontent.com/105735037/206177821-48dd0729-ae44-426d-b25d-f033a82caccf.PNG)

## 5ª Questão
Escreva um comando SQL para listar o total de alunos matriculador em cada curso.
```sql
alter table tb_matricula
add codigo_matricula serial primary key 

```
## Resultado esperado


## 6ª Questão
Desenvolva um comando SQL que retorne o nome de todos os alunos maiores que
18 anos.
```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado esperado

![02](https://user-images.githubusercontent.com/105735037/206178292-be49f604-890b-494c-9a4b-07f093e433c1.PNG)

## 7ª Questão

```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
## Resultado esperado

![02](https://user-images.githubusercontent.com/105735037/206178459-043f75e4-59a6-447b-a2d6-982c9e8e0cb8.PNG)

## 8ª Questão

```sql
select tb_aluno.nome_aluno as mulheres_em_medicina
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 1
and tb_aluno.sexo = 'F'
```
## Resultado esperado

![08](https://user-images.githubusercontent.com/105735037/206179572-c2658809-8900-4fe9-9d2b-10a45170ed99.PNG)

## 9ª Questão

```sql
select nome_curso
from tb_curo order by nome_curso asc
```
## Resultado esperado

![09](https://user-images.githubusercontent.com/105735037/206180248-ad1a45eb-76a7-422b-94dd-f43bdd801c8f.PNG)

## 10ª Questão

```sql
select tb_aluno.nome_aluno as homens_em_Jornalismo
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 5
and tb_aluno.sexo = 'M'
```
## Resultado esperado

![10](https://user-images.githubusercontent.com/105735037/206182690-2fae6c21-3466-4064-9c4f-7f7eec351357.PNG)




# Questoes teoricas

## 1ª Questão
SQL significa “Structured Query Language”, ou “Linguagem de Consulta Estruturada”, em português. Resumidamente, é uma linguagem de programação para lidar com banco de dados relacional (baseado em tabelas).

## 2ª Questão
Anos 70:
O SQL foi criado por pesquisadores da IBM em San Jose, dentro do projeto System R, que tinha por objetivo demonstrar a viabilidade da implementação do modelo relacional proposto por E. F. Codd. No começo a linguagem original era chamada SEQUEL, acrônimo para "Structured English Query Language" (Linguagem de Consulta Estruturada, em Inglês). Sendo uma das linguagens diferenciadas por manipular e recuperar dados do gerenciamento de banco de dados da IBM. No fina dos 70 a chamada atualmente Oracle, sendo inspirada a criar sua própria versão e introduzir a primeira implementação comercial disponível do SQL.

Anos 80:
Em meados da década de 80, foi publicada a primeira versão padronizada da linguagem SQL, dois instituos trabalharam na sua padronização, o ANSI e o ISO. A Microsoft  também lançou sua primeira versão do SQL Server. Sendo desenvolvida para a plataforma OS/2 juntamente com a Microsoft e a Sybase.

Anos 90:
Durante os anos 90 a Microsoft iniciou o desenvolvimento de uma versão para a plataforma NT. Enquanto o SQL Server estava sendo desenvolvido a Microsoft decidiu que ele deveria ser uma camada encapsulada sobre o sistema operacional NT. 
Em 1993 o Windows NT 3.1 e o SQL Server 4.2 para NT foram lançados. A filosofia da Microsoft em combinar um banco de alta performance com uma interface fácil de usar mostrou-se um sucesso. Microsoft rapidamente tornou-se o segundo mais popular vendedor de softwares de bancos de dados relacionais.

Anos 2000:
Em 2000 a Microsoft lançou o SQL Server 2000. O SQL Server 2000 é o lançamento mais importante do SQL Server até o momento. Essa versão foi construída sobre o framework do SQL Server 7.0. De acordo com o time de desenvolvimento do SQL Server essas mudanças foram desenvolvidas para tornar essa tecnologia mais nova pelos próximos 10 anos.
2005 - É lançado o SQL Server 2005 (com o codinome Yukon) com grande integração a plataforma .NET. O SQL Server dá mais um passo em direção às grandes plataformas corporativas. A Microsoft exibe alguns grandes casos de sucesso (como a Xerox que consegue realizar até 7.000.000 de transações diárias utilizando o SQL Server 2005 e a Bovespa que é a bolsa de valores do Brasil).

## 3ª Questão
Algumas das principais características do SQL	 são: sintaxe de comandos o  mais próximo possível da linguagem da língua inglesa; Trabalha com conjuntos de 
egistros, e nao com um registro por vez; Utilizada por utilizadores “normais” tanto também pelos Administradores do Banco de dados.Seus comandos permitem:             Fazer consultas aos dados; Criar, ler, atualizar e  deletar os dados em um banco de dados; Garantir a consistência de dados;  Controlar e auditar o acesso aos         objetos armazenados na base de dados;

## 4ª Questão
SELECT é lista de campos a serem selecionados e FROM seria a origem dos campos e nome da tabela
SELECT: Cláusula obrigatória em uma consulta SQL, responsável por listar todas as colunas que serão projetadas na consulta.
FROM: Nesta Cláusula informamos a fonte das informações, podendo ser
apenas um ou várias. Também é obrigatória e juntamente com a cláusula SELECT
formam a base de qualquer consulta SQL.

## 5ª Questão
O SQL Server atua com sistemas integrados de criptografia, permitindo que a visualização ou alteração das informações sejam feitas apenas pelas pessoas responsáveis, o que garante ainda mais segurança e tranquilidade para os usuários e empresários. Usando um banco de dados, todas as atividades podem ser feitas com mais 
eficiência. Assim, o usuário encontra todas as informações necessárias durante a busca. Qualquer pessoa que queria trabalhar com desenvolvimento de software
precisa aprender SQL porque a maioria dos sistemas de informação interagem com
banco de dados e é a língua universal para fazer qualquer coisa em banco de 
dados relacionais.
