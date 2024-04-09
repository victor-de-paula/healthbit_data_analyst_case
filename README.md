# HealthBit Data Analyst Case 

**Author**: Victor de Paula Silva

**Location**: Monte Mor, São Paulo, Brazil

**Start**: 2024-04-08

**End**: 2024-04-10

**Version**: 1.0

**Contact:** [Github](https://github.com/victor-de-paula) - [LinkedIn](https://www.linkedin.com/in/victor-de-paula-silva/) - [Outlook](victor.depaula@live.com) - [Gmail](victordepaula24@gmail.com)

## Introduction
> This repository contains the solution to the technical challenge for the position of Data Analyst at Healthbit.
>
> This is a **private repository**, where only people from HealthBit itself, apart from me, the author, will be able to access the content provided here.
>
> I conducted an **Exploratory Data Analysis (EDA)** on two datasets (*cadastro_base* and *sinistros_base*), cross-referencing the data to identify patterns and pinpoint the reasons behind the cost fluctuations over the 12-month period of analysis, as requested in the challenge.
> 
> **Technologies used**:
> - [Python](https://www.python.org/)
> - [Notebooke Jupyter](https://jupyter.org/)
> - [Power BI](https://www.microsoft.com/pt-br/power-platform/products/power-bi)

## Data Preparation & Cleaning
> `cadastro_base`
> 
> Based on the EDA conducted, it was noted that some treatments were necessary in the `cadastro_base` dataframe, as it is a base with the position date of the registration updates for each client.
> 
> To have unique results for each client (`CODIGO ÚNICO DA PESSOA`), I chose to bring the last record for each client, avoiding problems with duplicate *dates* and *ages*, as was the case before. Additionally, I treated the `DATA DE NASCIMENTO` column to correct the issue found with the 12 invalid records.
> 
> As a result, I generated a new treated dataframe named `beneficiaries`, with these unique results coming from `cadastro_base`.