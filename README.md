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
> 
> ---------------------------------------------------
> 
> `sinistros_base`
> 
> Based on the EDA, it is noted that the dataset contains duplicate records with different reference dates, similar to the previous dataset.
> 
> To address these records and have a single result for each of them, I took the maximum reference date for each claim record, considering all columns that characterize a claim as unique, namely: ``CODIGO DO EVENTO``,``FONTE``,``PLANO``,``TITULARIDADE``,``CODIGO DA FAMILIA``,``CODIGO ÚNICO DA PESSOA``,``DATA DO EVENTO``,``PRESTADOR``,``VALOR DO EVENTO``,``DESCRITOR DO EVENTO``, and ``INTERNACAO?``.
> 
> Furthermore, I also performed data preprocessing to ensure that date columns were in valid formats.
> 
> In the end, I generated a new dataframe called ``claims``, containing unique records from ``sinistros_base``, to use in my dashboard.

## Q&A
> `cadastro_base` / `beneficiaries`
>
> #### Questions
> 1. Does the dataframe have any beneficiary with inconsistent registration?
> 2. Does this dataframe have any beneficiaries with different ``PLANO`` over the reference months? Does the ``TITULARIDADE`` change over the months?
> 3. Any beneficiary with a different ``DATE DE NASCIMENTO``? More than one date for the same beneficiary.
> 4. How is the distribution of beneficiaries among ``SEXO``, ``PLANO``, and ``TITULARIDADE``?
> 5. Can the same beneficiary have more than one ``IDADE`` over time? Due to the base being a monthly record (position date).
> 
> #### Answers
> 1. Yes, 12 beneficiaries have an invalid date of birth, with inconsistent dates. None of them were corrected in subsequent reference months, thus maintaining only the incorrect results.
> 2. No, all beneficiaries continue with the same plan over the months. The same occurs with the titularity, remaining the same.
> 3. Yes, the `CODIGO ÚNICO DA PESSOA` = 1388 has two dates of birth: 12/04/1986 until January/2021 and 11/04/1986 from February/2021 onwards.
> 4. The male gender has the highest number of beneficiaries, as well as the Superior plan in the plan group, while Dependents are the highest number of beneficiaries among the types of titularity.
> 5. Yes, there are cases where the same beneficiary has 2 or 3 ages, for example.
> 
> --------------------------------------------------
> 
> `sinistros_base` / `claims`
> 
> #### Questions
> 1. Does this dataframe have duplicate event records?
> 2. What is the trend of events over time? Does the fluctuation mentioned in the challenge proposal really occur? Does the total number of events and the sum of the event values ​​follow the same trend over time?
> 3. What are the top 5 events in the entire dataset? Is there a variation in this top 5 between 2020 and 2021?
> 4. Is there any family that stands out in the total number of claims?
> 5. Is there any beneficiary who stands out? Does he belong to the same family that is at the top?
> 6. Who are the main ``PRESTADOR``?
> 7. How is the concentration of claims by ``PLANO`` type? And by ``FONTE``?
> 8. How do ``INTERNAÇÃO`` events behave in 2020 and 2021?
> 
> #### Answers
> 1. Yes, due to ``DATA DE REFERÊNCIA``, this dataframe also has duplicate records of the same insurance event.
> 2. The events and their values ​​grew in 2020, the year they peaked. However, in the fourth quarter of this year, there is already a slowdown in this movement, with the year 2021 recording much lower numbers than those registered in the previous year. Thus, there was a great fluctuation over time, so that both the total number of events and the total values ​​of these events followed the same trend over time.
> 3. Throughout the period, CONSULTA MEDICA EM CONSULTORIO (10101012) stands out as the main reason for claims over time, and also in the individual years of 2020 and 2021. In addition, the other two reasons in the top 3 are the same: ATENDIMENTO EM PRONTO SOCORRO(PCTE COM HM) e HEMOGRAMA COMPLETO-ERITROGRAMA LEUCOGRAMA PLAQUETA. The variation occurs only in one reason from 2020 (CREATININA) to 2021 (SESSAO DE PSICOTERAPIA INDIVIDUAL POR PSICOLOGO), with MATERIAIS closing the podium. Overall, there is no major change in procedures from one year to the next.
> 4. The main family is 108, with more than 5 thousand records throughout the period. Below it are families 133 and 429, rounding out the top 3.
> 5. The main beneficiary is 181 and he belongs to the top family, 108.
> 6. The top 5 providers are 256, 282, 465, 485, and 486. The first one stands out greatly compared to the others, with 9803 records, while the second has 2933, that is, 3 times less than the first place.
> 7. Claims are concentrated in the BÁSICO ``PLANO``, with 71% of the records over time. In addition, 95% of the events are related to the REDE ``FONTE``, with few records related to REEMBOLSO.
> 8. The proportion of hospitalization (`INTERNAÇÃO?`) events decreased from 2020 to 2021. In the first year, these represent 33% of the total events, while in 2021 this number is halved, representing 16% of the claims in that year.

## Final Dashboard
> You can view and interact with the dashboard created in Power BI from the following link, which allows you to explore the underlying factors behind cost fluctuations over time. To view the dashboard, simply click on [HealthBit_Case_Analysis](https://app.powerbi.com/view?r=eyJrIjoiZTgzYWQyNWQtMTM5OC00OTMxLTlkNzEtYjFhOWExNzI2ODM4IiwidCI6ImU1MWE0OTI5LWFmMDgtNDJkMC04MjE2LWExZjM1ZGYxNzZmNiJ9).
>
> If you prefer, you can also download the Power BI workbook to manipulate the dashboard directly on your computer. Simply download the file "HealthBit_Case_Analysis.pbix" available in this repository.
> 
> ![HealthBit_Case_Analysis](https://github.com/victor-de-paula/healthbit_data_analyst_case/assets/57963214/2ee5ff22-fb25-48c8-9e0f-f4d49b582f83)
