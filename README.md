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




