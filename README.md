# Desafio de projeto | Processando e Transformando Dados com PowerBI

### Etapas aplicadas
- Renomeei as colunas para melhor legibilidade, tanto para leitura quanto para a utilização nos elementos gráficos.

- Modifiquei os valores monetários para decimal fixo.

- Valor null da coluna super_ssn substituído por "no supervisor" pois é originado devido tal empregado ser um gerente que não possui um supervisor

	campo address dividido pelo delimitador "-" sendo necessário a correção de um registro com caso especifico que acabou gerando uma coluna a mais com um único 
	valor. Renomeado de acordo.

- Não havia departamento sem gerente

- o employee James não possui horas no projeto que esta relacionado, talvez pelo fato de ele apenas gerenciar e não participar diretamente no desenvolvimento do projeto.

- Foi feita a separação da coluna Address da tabela employee.

- query usada para recuperar encarregado e seu respectivo gerente
    ```sql
        SELECT
            concat(e.Fname, ' ', e.Minit, '. ', e.Lname) AS EmployeeName, 
            concat(m.Fname, ' ', m.Minit, '. ', m.Lname) AS MgrName 
        FROM employee e INNER JOIN employee m ON e.Super_ssn = m.Ssn;
    ```

- Ao fazer a mesclagem o powerBI funciona semelhante a um join juntando os dados em colunas com as correspondências encontradas. Ao usar o "Atribuir" ele faz a concatenação das linhas
acarretando em junção desestruturada.