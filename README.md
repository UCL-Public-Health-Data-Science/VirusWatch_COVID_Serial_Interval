# VirusWatch_COVID_Serial_Interval
<br>
R code for Virus Watch COVID-19 serial interval analysis <br>
This code generates infector - infectee pairs from illness episodes data.<br>

The illness episode dataset is structured as below:

| household_id | individual_id | illness_start_date |
|--------------|---------------|--------------------|
| xx           | xx01          | 01/01/2020         |
| xx           | xx02          | 12/01/2020         |
| xx           | xx03          | 15/01/2020         |
| xx           | xx04          | 06/02/2020         |
| yy           | yy01          | 02/01/2020         |
| yy           | yy02          | 03/01/2020         |
| yy           | yy03          | 29/01/2020         |


Plausible household infector-infectee pairs are generated based on the maximum serial interval allowed. Where there were multiple potential infectors for the same infectee, these pairs were excluded from the analysis, resulting in the table below: <br>

| infectee_id | infectee_start_date | infector_id | infector_start_date |
|-------------|---------------------|-------------|---------------------|
| xx02        | 12/01/2020          | xx01        | 01/01/2020          |
| xx04        | 06/02/2020          | xx03        | 15/01/2020          |
| yy02        | 03/01/2020          | yy01        | 02/01/2020          |



*(These tables are examples. They do not disclose any real data used for the analysis)* <br>
*We compute the serial interval using the ***difftime()*** function (https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/difftime).*
