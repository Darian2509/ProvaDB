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
