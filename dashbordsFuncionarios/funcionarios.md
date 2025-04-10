# Dashboard Funcionários - SQLs Documentados

---

## Título do SQL

Faixa Etária dos Funcionários

---

## Código SQL

```sql
-- Faixa Etária dos Funcionários --
SELECT 
  CASE
    WHEN AGE < 25 THEN 'Menos de 25 anos'
    WHEN AGE BETWEEN 25 AND 34 THEN '25 a 34 anos'
    WHEN AGE BETWEEN 35 AND 44 THEN '35 a 44 anos'
    WHEN AGE BETWEEN 45 AND 54 THEN '45 a 54 anos'
    ELSE '55 anos ou mais'
  END AS FAIXA_ETARIA,
  COUNT(*) AS TOTAL_FUNCIONARIOS
FROM PUBLIC.TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB
GROUP BY FAIXA_ETARIA
ORDER BY TOTAL_FUNCIONARIOS DESC;






---

## Título do SQL

Funcionários por Área de Formação e Cargo

---

## Código SQL

``sql
-- Funcionários por Área de Formação e Cargo --
SELECT 
  CASE 
    WHEN EDUCATIONFIELD = 'Life Sciences' THEN 'Ciências Biológicas'
    WHEN EDUCATIONFIELD = 'Medical' THEN 'Medicina'
    WHEN EDUCATIONFIELD = 'Marketing' THEN 'Marketing'
    WHEN EDUCATIONFIELD = 'Technical Degree' THEN 'Curso Técnico'
    WHEN EDUCATIONFIELD = 'Other' THEN 'Outro'
    WHEN EDUCATIONFIELD = 'Human Resources' THEN 'Recursos Humanos'
    WHEN EDUCATIONFIELD = 'Education' THEN 'Educação'
    ELSE EDUCATIONFIELD
  END AS AREA_FORMACAO,
  
  CASE 
    WHEN JOBROLE = 'Sales Executive' THEN 'Executivo de Vendas'
    WHEN JOBROLE = 'Research Scientist' THEN 'Cientista de Pesquisa'
    WHEN JOBROLE = 'Laboratory Technician' THEN 'Técnico de Laboratório'
    WHEN JOBROLE = 'Manufacturing Director' THEN 'Diretor de Produção'
    WHEN JOBROLE = 'Healthcare Representative' THEN 'Representante de Saúde'
    WHEN JOBROLE = 'Manager' THEN 'Gerente'
    WHEN JOBROLE = 'Sales Representative' THEN 'Representante de Vendas'
    WHEN JOBROLE = 'Research Director' THEN 'Diretor de Pesquisa'
    WHEN JOBROLE = 'Human Resources' THEN 'Recursos Humanos'
    ELSE JOBROLE
  END AS CARGO,
  
  COUNT(*) AS QUANTIDADE

FROM PUBLIC.TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB
GROUP BY AREA_FORMACAO, CARGO
ORDER BY QUANTIDADE DESC;







---

## Título do SQL

Média de Anos de Experiência dos Funcionários por Departamento

---

## Código SQL

``sql
-- Média de Anos de Experiência dos Funcionários por Departamento --
SELECT 
  CASE 
    WHEN DEPARTMENT = 'Research & Development' THEN 'Pesquisa e Desenvolvimento'
    WHEN DEPARTMENT = 'Sales' THEN 'Vendas'
    WHEN DEPARTMENT = 'Human Resources' THEN 'Recursos Humanos'
    ELSE DEPARTMENT
  END AS DEPARTAMENTO,
  
  ROUND(AVG(TOTALWORKINGYEARS), 1) AS MEDIA_ANOS_EXPERIENCIA

FROM PUBLIC.TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB
GROUP BY DEPARTAMENTO
ORDER BY MEDIA_ANOS_EXPERIENCIA DESC;






---

## Título do SQL

Quantidade de Funcionários que Realizam Hora Extra

---

## Código SQL

``sql
-- Quantidade de Funcionários que Realizam Hora Extra --
SELECT 
  OVERTIME AS HORA_EXTRA,
  COUNT(*) AS TOTAL_FUNCIONARIOS
FROM PUBLIC.TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB
GROUP BY HORA_EXTRA
ORDER BY TOTAL_FUNCIONARIOS DESC;






---

## Título do SQL

Total de Funcionários por Gênero

---

## Código SQL

``sql
-- Total de Funcionários por Gênero --
SELECT 
  GENDER AS GENERO,
  COUNT(*) AS TOTAL_FUNCIONARIOS
FROM PUBLIC.TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB
GROUP BY GENERO
ORDER BY TOTAL_FUNCIONARIOS DESC;









