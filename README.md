# Databricks Data Processing - NYC Yellow Trip

Desafio: Estruturar um pipeline de engenharia de dados no ambiente
Databricks, respeitando as boas práticas de arquitetura em camadas (Bronze, Prata e Gold), com
foco em confiabilidade, automação e análise de dados.

[Me acompanhe aqui! ](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/943498958963772?o=609239402676531)
| [Descricao colunas](descricao_colunas.md) | [Tipos de Usuario]() | 

---

## Etapas construidas

Primeiro criei um notbook Databricks para dar inicio ao processamento de dados. Aqui tem a união de todas as camadas (Bronze/Silver/Gold). Neste notbook a camada de Analise está incompleta, pois ela será continuada em outro notbook dedicado para esse fim. 

Notbooks nas diferentes camadas: [Bronze](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/2731816656921143?o=609239402676531) | [Silver](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/2731816656921142?o=609239402676531) | [Gold](https://dbc-ef780d3c-c43c.cloud.databricks.com/editor/notebooks/3327772790411468?o=609239402676531)


> Essa divisão é importante no caso de grande volume de dados! Porque facilita a manutenção, otimiza, evita repitir dados, ganha rastreabilidade maior em caso de erros e permite disponibilizar os dados para diferentes tipos de consumidores.

### Próximo passo: Criar Jobs