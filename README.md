# Databricks Data Processing - NYC Yellow Trip

Desafio: Estruturar um pipeline de engenharia de dados no ambiente
Databricks, respeitando as boas práticas de arquitetura em camadas (Bronze, Prata e Gold), com
foco em confiabilidade, automação e análise de dados.

[Me acompanhe aqui! ](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/943498958963772?o=609239402676531)
| [Descricao colunas](/notbooks/documentacao/descricao_colunas.md) | [Tipos de Usuario]() | 

---

## Etapas construidas

Primeiro criei um notbook Databricks para cada camada:

[Bronze](notbooks\Raw.ipynb) → dados brutos, sem transformação
- Aqui coleto automaticamente apenas tabelas que contem o nome **yellow_tripdata_**, então se eu inserir uma nova tabela com esse nome de um novo mes será inserido automaticamente


[Silver](notbooks\DataSource.ipynb) → limpeza, validação, padronização
- Além de armazenar dados limpos na tabela *yellow_trip_silver*, separei os dados incompletos ou invalidos na *yellow_trip_silver_invalid*.
Isso é importante pois além de rastrearmos possibilidades de performance com os dados limpos, os dados que identificamos como incorreto também pode nos trazer insights de qual é o causador.
 

Gold → tabelas analíticas e agregadas, prontas para BI, Dashboard e varias outras possibilidades
- Nessa camada é importante validar se o código dos calculos que está criando vai trazer o dado preciso. É muito fácil o dado arrendondar e perder o valor preciso.

Notbooks nas diferentes camadas no databricks: [Bronze](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/2731816656921143?o=609239402676531) | [Silver](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/2731816656921142?o=609239402676531) | [Gold](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/3327772790411468?o=609239402676531)


> Essa divisão é importante no caso de grande volume de dados! Porque facilita a manutenção, otimiza, evita repitir dados, ganha rastreabilidade maior em caso de erros e permite disponibilizar os dados para diferentes tipos de consumidores.

### Próximo passo: Criando Jobs

```mermaid
graph LR;
    Bronze-->Silver;
    Silver-->Gold;
    style Bronze stroke-width:3px,stroke:#333,fill:#c62e08,rx:15,ry:15
    style Silver stroke-width:3px,stroke:#333,fill:#dc440c,rx:15,ry:15
    style Gold stroke-width:3px,stroke:#333,fill:#f15b10,rx:15,ry:15
```

Nessa estrutura, evitamos erros e inconsistencias e possibilita reprocessamento ou paralelização de forma eficiente, o que é essencial em pipelines de larga escala.

 Silver(_Data_Cleaning_) não vai rodar se Bronze(_Raw_ingestion_) não rodar. Exemplo, se rodasse Gold, independente das camadas anteriores, em um job especifico para camadas Gold ele traria dados desatualizados e inconsistentes.

![alt text](image.png)

Nessa estrutura também temos a facilidade de debugar e monitorar erros, exemplo:

![alt text](<Screenshot 2025-08-31 204636.png>)

> Sabemos que ocorreu na primeira camada, mais facil de encontrar o erro. Nesse caso, era erro de repositório.

### Detalhes do Job
**Agendamento:** diário, às 3h da manhã<br>
**Tipo:** Notbook<br>
**Source:** Workspace <span style="color:gray;">(Existe git também)</span><br>
**Compute:** Serverless  <span style="color:gray;">(No Databricks gratuíto, até então, não tem opção de modificar o Compute)</span><br>

