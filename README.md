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
select tb_curso.nome_curso,
codigo_curso + codigo_aluno as numero_alunos
from tb_curso
inner join tb_aluno
on tb_aluno.codigo_aluno = tb_curso.codigo_curso
```
## Resultado esperado

![02](https://user-images.githubusercontent.com/105735037/206178109-5af9d43b-94d3-4dfa-ad20-9260bbc439bd.PNG)

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

