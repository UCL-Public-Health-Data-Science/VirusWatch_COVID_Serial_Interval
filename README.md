# VirusWatch_COVID_Serial_Interval
R code for Virus Watch COVID-19 serial interval analysis <br>
This code generates infector - infectee pairs from illness episodes data.<br>

The illness episode dataset will look like the below:

| household_id  | individual_id |start_date|
| ------------- |:-------------:| -----:|
|xx      | x01 | 02/10/2020 |
| xx     | x02      |   13/10/2020 |
| xx | x03      |   21/10/2020 |
|yy	|y01	|05/10/2020|
|yy	|y02	|10/10/2020|
|yy	|y01	|22/10/2020|
|cc|	c04|	20/11/2020|
|cc|	c02|	20/11/2020|
|cc	|c01|	02/12/2020|


We then generate plausible household infector-infectee pairs based on the maximum serial interval allowed.

This will output all possible transmission pairs: 

| infectee_ID | infectee_start_date | infector_ID | infector_start_date |
|------------|---------------------|-------------|---------------------|
| a04        | 2020-10-20          | a01         | 2020-10-11          |
| a04        | 2020-10-20          | a03         | 2020-10-11          |
| a02        | 2020-11-04          | a04         | 2020-10-20          |
| a06        | 2020-11-21          | a02         | 2020-11-04          |
| c01        | 2020-12-02          | c04         | 2020-11-20          |
| c01        | 2020-12-02          | c02         | 2020-11-20          |
| x02        | 2020-10-13          | x01         | 2020-10-02          |
| x03        | 2020-10-21          | x02         | 2020-10-13          |
| y02        | 2020-10-10          | y01         | 2020-10-05          |
| y01        | 2020-10-22          | y02         | 2020-10-10          |


Where there were multiple potential infectors for the same infectee, these pairs were excluded from the analysis. <br>
*(These tables are examples. They do not disclose any real data used for the analysis and are not related to one another)* <br>
*We compute the serial interval using the ***difftime()*** function (https://www.rdocumentation.org/packages/base/versions/3.6.2/topics/difftime).*
