# ⚡ For impatients

```shell
#!/bin/sh
# Diplay latest flags
sh <(curl https://tea.xyz) +duckdb.org \
duckdb << EOF
INSTALL httpfs;
LOAD httpfs;
.mode duckbox
select plage,
    flag_color,
    case 
        when (flag_color = 'BLUE')      THEN '🟦'
        when (flag_color = 'YELLOW')    THEN '🟨'
        when (flag_color = 'RED')       THEN '🟥'
    end as flag_color
from read_csv_auto('https://bit.ly/3ZCJ1X5') as latest;
EOF

```
