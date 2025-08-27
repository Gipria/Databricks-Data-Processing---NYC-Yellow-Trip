Tempo/Duração: tpep_pickup_datetime, tpep_dropoff_datetime

Geolocalização: PULocationID, DOLocationID (cruzando com tabela de zonas)

Custos: fare_amount, extra, mta_tax, tip_amount, tolls_amount, improvement_surcharge, congestion_surcharge, airport_fee, total_amount

Pagamento: payment_type, tip_amount


| Nome da Coluna               | Descrição                                                                                                                              | Valores/Exemplos                                                                                                |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **`VendorID`**               | Identifica a empresa de tecnologia que forneceu o registro.                                                                            | `1` = Creative Mobile Technologies (CMT)<br>`2` = VeriFone Inc. (VTS)                                          |
| **`tpep_pickup_datetime`**   | Data e hora em que o medidor do táxi foi ativado (início da corrida).                                                                  | `2023-10-27 08:15:30`                                                                                           |
| **`tpep_dropoff_datetime`**  | Data e hora em que o medidor do táxi foi desativado (fim da corrida).                                                                  | `2023-10-27 08:45:12`                                                                                           |
| **`passenger_count`**        | Número de passageiros no veículo.                                                                                                      | `1`, `2`, `4` (Fornecido pelo motorista, pode ser impreciso)                                                   |
| **`trip_distance`**          | Distância da corrida, em **milhas**.                                                                                                   | `2.5`, `10.3`, `0.8`                                                                                            |
| **`RatecodeID`**             | Código que indica o tipo de tarifa aplicada.                                                                                           | `1` = Standard<br>`2` = JFK<br>`3` = Newark<br>`4` = Nassau/Westchester<br>`5` = Negotiated<br>`6` = Group ride |
| **`store_and_fwd_flag`**     | Indica se os dados foram armazenados na memória do veículo e transmitidos depois ("store and forward").                                 | `Y` = Sim<br>`N` = Não                                                                                          |
| **`PULocationID`**           | ID numérico da Zona de Táxis (Taxi Zone) onde a corrida começou (pickup).                                                              | `1`, `100`, `230` (Cruzar com tabela `taxi_zone_lookup`)                                                        |
| **`DOLocationID`**           | ID numérico da Zona de Táxis (Taxi Zone) onde a corrida terminou (dropoff).                                                            | `1`, `100`, `230` (Cruzar com tabela `taxi_zone_lookup`)                                                        |
| **`payment_type`**           | Código que indica como o passageiro pagou.                                                                                             | `1` = Cartão de crédito<br>`2` = Dinheiro<br>`3` = Sem custo<br>`4` = Disputa<br>`5` = Desconhecido<br>`6` = Anulada |
| **`fare_amount`**            | Valor base da tarifa da corrida, em dólares.                                                                                           | `12.50`, `27.00`, `6.00`                                                                                        |
| **`extra`**                  | Valores extras e sobretaxas (ex.: horário de pico, sobretaxa noturna).                                                                 | `1.00`, `2.50`, `0.00`                                                                                          |
| **`mta_tax`**                | Imposto de US$ 0.50 da *Metropolitan Transportation Authority* (MTA).                                                                  | `0.50`                                                                                                          |
| **`tip_amount`**             | Valor da gorjeta, em dólares.                                                                                                          | `3.25`, `0.00`, `5.80`                                                                                          |
| **`tolls_amount`**           | Valor total de pedágios pagos durante a corrida, em dólares.                                                                           | `0.00`, `6.55`, `11.80`                                                                                         |
| **`improvement_surcharge`**  | Sobretaxa de melhoria de US$ 0.30 aplicada a todas as corridas.                                                                        | `0.30`                                                                                                          |
| **`total_amount`**           | **Valor total final** pago pelo passageiro (soma de todas as taxas).                                                                   | `23.05`, `35.10`, `12.80`                                                                                       |
| **`congestion_surcharge`**   | Sobretaxa de congestionamento (US$ 2.50/2.75) para viagens na zona central de Manhattan.                                               | `0.00`, `2.50`, `2.75`                                                                                          |
| **`airport_fee`**            | Taxa de aeroporto (US$ 1.25) para viagens que terminam nos aeroportos JFK ou LaGuardia.                                                | `0.00`, `1.25`                                                                                                  |



---
# Fontes

https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf