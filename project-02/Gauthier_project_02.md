# Data Visualization 

> Jacqueline Gauthier. 

## Mini-Project 2

Description: 
This project investigates the relationships between the national walkability index and various predictors. The primary objective is to analyze how different factors correlate with walkability.

Motivation
Understanding the factors that contribute to walkability because I like walkability. This can lead to numerous benefits, including improved public health and reduced traffic congestion.

Summary of Findings
AvgNWI vs AvgP_Wrk and AvgP_LowW: Higher walkability tends to correlate with higher proportions of the working-age population and slightly lower proportions of low-wage workers.
AvgNWI vs AvgDisPop and TotCPop: Areas with higher walkability tend to have higher average district and total county populations.


Data Dictionary:

Term	Definition
GEOID10	Census block group 12-digit FIPS code (2010), type: string, length: 12
GEOID20	Census block group 12-digit FIPS code (2018), type: string, length: 50
STATEFP	State FIPS code, type: string, length: 2
COUNTYFP	County FIPS code, type: string, length: 3
TRACTCE	Census tract FIPS code in which CBG resides, type: string, length: 6
BLKGRPCE	Census block group FIPS code in which CBG resides, type: string, length: 1
CSA	Combined Statistical Area (CSA) Code, type: string, length: 3
CSA_Name	Name of CSA in which CBG resides, type: string, length: 100
CBSA	FIPS for Core-Based Statistical Area (CBSA) in which CBG resides, type: string, length: 5
CBSA_Name	Name of CBSA in which CBG resides, type: string, length: 100
CBSA_POP	Total population in CBSA, type: double
CBSA_EMP	Total employment in CBSA, type: double
CBSA_WRK	Total number of workers that live in CBSA, type: double
Ac_Total	Total geometric area (acres) of the CBG, type: double
Ac_Water	Total water area (acres), type: double
Ac_Land	Total land area (acres), type: double
Ac_Unpr	Total land area (acres) that is not protected from development, type: double
TotPop	Population, 2018, type: integer
CountHU	Housing units, 2018, type: integer
HH	Households (occupied housing units), 2018, type: integer
P_WrkAge	Percent of population that is working aged 18 to 64 years, 2018, type: double
AutoOwn0	Number of households in CBG that own zero automobiles, 2018, type: integer
Pct_AO0	Percent of zero-car households in CBG, 2018, type: double
AutoOwn1	Number of households in CBG that own one automobile, 2018, type: integer
Pct_AO1	Percent of one-car households in CBG, 2018, type: double
AutoOwn2p	Number of households in CBG that own two or more automobiles, 2018, type: integer
Pct_AO2p	Percent of two-plus-car households in CBG, 2018, type: double
Workers	Count of workers in CBG (home location), 2017, type: integer
R_LowWageWk	Count of workers earning $1250/month or less (home location), 2017, type: integer
R_MedWageWk	Count of workers earning more than $1250/month but less than $3333/month (home location), 2017, type: integer
R_HiWageWk	Count of workers earning $3333/month or more (home location), 2017, type: integer
R_PCTLOWWAGE	Percent of low wage workers in a CBG (home location), 2017, type: double
TotEmp	Total employment, 2017, type: integer
E5_Ret	Retail jobs within a 5-tier employment classification scheme, type: integer
E5_Off	Office jobs within a 5-tier employment classification scheme, type: integer
E5_Ind	Industrial jobs within a 5-tier employment classification scheme, type: integer
E5_Svc	Service jobs within a 5-tier employment classification scheme, type: integer
E5_Ent	Entertainment jobs within a 5-tier employment classification scheme, type: integer
E8_Ret	Retail jobs within an 8-tier employment classification scheme, type: integer
E8_off	Office jobs within an 8-tier employment classification scheme, type: integer
E8_Ind	Industrial jobs within an 8-tier employment classification scheme, type: integer
E8_Svc	Service jobs within an 8-tier employment classification scheme, type: integer
E8_Ent	Entertainment jobs within an 8-tier employment classification scheme, type: integer
E8_Ed	Education jobs within an 8-tier employment classification scheme, type: integer
E8_Hlth	Health care jobs within an 8-tier employment classification scheme, type: integer
E8_Pub	Public administration jobs within an 8-tier employment classification scheme, type: integer
E_LowWageWk	Number of workers earning $1250/month or less (work location), 2017, type: integer
E_MedWageWk	Number of workers earning more than $1250/month but less than $3333/month (work location), 2017, type: integer
E_HiWageWk	Number of workers earning $3333/month or more (work location), 2017, type: integer
E_PctLowWage	Percent LowWageWk of total workers in a CBG (work location), 2017, type: double
D1A	Gross residential density (HU/acre) on unprotected land, type: double
D1B	Gross population density (people/acre) on unprotected land, type: double
D1C	Gross employment density (jobs/acre) on unprotected land, type: double
D1C5_RET	Gross retail (5-tier) employment density (jobs/acre) on unprotected land, type: double
D1C5_OFF	Gross office (5-tier) employment density (jobs/acre) on unprotected land, type: double
D1C5_IND	Gross industrial (5-tier) employment density (jobs/acre) on unprotected land, type: double
D1C5_SVC	Gross service (5-tier) employment density (jobs/acre) on unprotected land, type: double
D1C5_ENT	Gross entertainment (5-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_RET	Gross retail (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_OFF	Gross office (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_IND	Gross industrial (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_SVC	Gross service (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_ENT	Gross entertainment (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_ED	Gross education (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_HLTH	Gross health care (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1C8_PUB	Gross retail (8-tier) employment density (jobs/acre) on unprotected land, type: double
D1D	Gross activity density (employment + HUs) on unprotected land, type: double
D1_FLAG	Flag indicating that density metrics are based on total CBG land acreage rather than unprotected acreage





V
