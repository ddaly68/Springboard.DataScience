# Project: Capstone Project - Data Wrangling

## Data Overview 

There are 8 data files, 1 sample submission file and another file with column descriptions.
Here are the 8 data files:


Application train sample
Info about loan and loan applicant at application time
This is the main table, broken into two files for Train (with TARGET) 
Static data for all applications. One row represents one loan in our data sample.
This file has 307511 rows of information and 122 features.

Application test sample
Info about loan and loan applicant at application time
This is the other main table, for Test (without TARGET).
Static data for all applications. One row represents one loan in our data sample.
This file has 48744 rows and 121 features (less the TARGET column).

Credit bureau.
All client's previous credits provided by other financial institutions that were reported to Credit Bureau (for
clients who have a loan in our sample).  For every loan in our sample, there are as many rows as number of
credits the client had in Credit Bureau before the application date.

Bureau Balance
Monthly balances of previous credits in Credit Bureau.
This table has one row for each month of history of every previous credit reported to Credit Bureau – i.e the
table has (#loans in sample * # of relative previous credits * # of months where we have some history observable
for the previous credits) rows.

CC Balance
Monthly balance snapshots of previous credit cards that the applicant has with Home Credit.
This table has one row for each month of history of every previous credit in Home Credit (consumer credit and cash
loans) related to loans in our sample – i.e. the table has (#loans in sample * # of relative previous credit cards *
nbr of months where we have some history observable for the previous credit card) rows.

Installment payments
Repayment history for the previously disbursed credits in Home Credit related to the loans in our sample.
There is a) one row for every payment that was made plus b) one row each for missed payment.
One row is equivalent to one payment of one installment OR one installment corresponding to one payment of one
previous Home Credit credit related to loans in our sample.

POS CASH Balance
Monthly balance snapshots of previous POS (point of sales) and cash loans that the applicant had with Home Credit.
This table has one row for each month of history of every previous credit in Home Credit
(consumer credit and cash loans) related to loans in our sample – i.e. the table has
(#loans in sample * # of relative previous credits * # of months in which we have some history observable for
the previous credits) rows.

Previous Application
All previous applications for Home Credit loans of clients who have loans in our sample.
There is one row for each previous application related to loans in our data sample.

## Cleaning The Data

Fortunately, all data files were able to be loaded successfully via the read_csv methond.  The file with column descriptions
did not load due to an encoding issue but this is meta data and will not affect calculations, so I chose not to import it.

## Missing Values

Focusing on the main training data (application_train.csv), there are 57 out of the 122 columns that have missing data.
Here is a breakdown of the number of missing values and the overall percentage of missing values to total rows:

Column                            Missing Values  % of Total Values
COMMONAREA_MEDI                       214865               69.9
COMMONAREA_AVG                        214865               69.9
COMMONAREA_MODE                       214865               69.9
NONLIVINGAPARTMENTS_MEDI              213514               69.4
NONLIVINGAPARTMENTS_MODE              213514               69.4
NONLIVINGAPARTMENTS_AVG               213514               69.4
FONDKAPREMONT_MODE                    210295               68.4
LIVINGAPARTMENTS_MODE                 210199               68.4
LIVINGAPARTMENTS_MEDI                 210199               68.4
LIVINGAPARTMENTS_AVG                  210199               68.4
FLOORSMIN_MODE                        208642               67.8
FLOORSMIN_MEDI                        208642               67.8
FLOORSMIN_AVG                         208642               67.8
YEARS_BUILD_MODE                      204488               66.5
YEARS_BUILD_MEDI                      204488               66.5
YEARS_BUILD_AVG                       204488               66.5
OWN_CAR_AGE                           202929               66.0
LANDAREA_AVG                          182590               59.4
LANDAREA_MEDI                         182590               59.4
LANDAREA_MODE                         182590               59.4
BASEMENTAREA_MEDI                     179943               58.5
BASEMENTAREA_AVG                      179943               58.5
BASEMENTAREA_MODE                     179943               58.5
EXT_SOURCE_1                          173378               56.4
NONLIVINGAREA_MEDI                    169682               55.2
NONLIVINGAREA_MODE                    169682               55.2
NONLIVINGAREA_AVG                     169682               55.2
ELEVATORS_MEDI                        163891               53.3
ELEVATORS_MODE                        163891               53.3
ELEVATORS_AVG                         163891               53.3
WALLSMATERIAL_MODE                    156341               50.8
APARTMENTS_MODE                       156061               50.7
APARTMENTS_MEDI                       156061               50.7
APARTMENTS_AVG                        156061               50.7
ENTRANCES_MODE                        154828               50.3
ENTRANCES_AVG                         154828               50.3
ENTRANCES_MEDI                        154828               50.3
LIVINGAREA_MEDI                       154350               50.2
LIVINGAREA_MODE                       154350               50.2
LIVINGAREA_AVG                        154350               50.2
HOUSETYPE_MODE                        154297               50.2
FLOORSMAX_MEDI                        153020               49.8
FLOORSMAX_AVG                         153020               49.8
FLOORSMAX_MODE                        153020               49.8
YEARS_BEGINEXPLUATATION_AVG           150007               48.8
YEARS_BEGINEXPLUATATION_MEDI          150007               48.8
YEARS_BEGINEXPLUATATION_MODE          150007               48.8
TOTALAREA_MODE                        148431               48.3
EMERGENCYSTATE_MODE                   145755               47.4
OCCUPATION_TYPE                        96391               31.3
EXT_SOURCE_3                           60965               19.8
AMT_REQ_CREDIT_BUREAU_WEEK             41519               13.5
AMT_REQ_CREDIT_BUREAU_DAY              41519               13.5
AMT_REQ_CREDIT_BUREAU_MON              41519               13.5
AMT_REQ_CREDIT_BUREAU_QRT              41519               13.5
AMT_REQ_CREDIT_BUREAU_HOUR             41519               13.5
AMT_REQ_CREDIT_BUREAU_YEAR             41519               13.5
NAME_TYPE_SUITE                         1292                0.4
DEF_30_CNT_SOCIAL_CIRCLE                1021                0.3
OBS_60_CNT_SOCIAL_CIRCLE                1021                0.3
DEF_60_CNT_SOCIAL_CIRCLE                1021                0.3
OBS_30_CNT_SOCIAL_CIRCLE                1021                0.3
EXT_SOURCE_2                             660                0.2
AMT_GOODS_PRICE                          278                0.1
AMT_ANNUITY                               12                0.0
CNT_FAM_MEMBERS                            2                0.0
DAYS_LAST_PHONE_CHANGE                     1                0.0