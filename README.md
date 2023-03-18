# ❔ About

See https://www.kaggle.com/code/adriensales/la-qualit-des-eaux-de-baignade-noum-a

# ⚡ For impatients

Just run the following script in any shell and enjoy:

```shell
#!/bin/sh
# Diplay latest flags
sh <(curl https://tea.xyz) +duckdb.org \
duckdb << EOF
INSTALL httpfs;
LOAD httpfs;
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


# 🦆 `DuckDb` hacks

First, install duckdb (`brew install duckdb`) or [`install_duckdb.sh`](https://gist.github.com/adriens/74a2fd8adc6fd508d970bc1cb2419395)

```sql
INSTALL httpfs;
LOAD httpfs;
.prompt "🦆 🏖️  > "
select * 
from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/latest.csv';
```

```sql
INSTALL httpfs;
LOAD httpfs;
.prompt "🦆 🏖️  > "
select *
from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/historic.csv';
```

You can also use (nicer) short urls : 

```shell
duckdb << EOF
-- historic
INSTALL httpfs;
LOAD httpfs;
select *
from
read_csv_auto('https://bit.ly/3mAUIPr') as historic;
EOF
```

```shell
duckdb << EOF
-- historic
INSTALL httpfs;
LOAD httpfs;
select *
from read_csv_auto('https://bit.ly/3ZCJ1X5') as latest;
EOF
```
## Tasks

Below some [`xc`](https://xcfile.dev/) ready tasks. 
Just type `xc`.

### latest
Print the latest status of all beaches

```shell
#!/bin/sh
# Diplay latest flags
sh <(curl https://tea.xyz) +duckdb.org \
duckdb << EOF
INSTALL httpfs;
LOAD httpfs;
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
### top-10

```shell
duckdb << EOF
-- historic
INSTALL httpfs;
LOAD httpfs;
select *
from read_csv_auto('https://bit.ly/3ZCJ1X5') as latest limit 10;
EOF
```

### last-20

```shell
#!/bin/sh
# Diplay latest flags
sh <(curl https://tea.xyz) +duckdb.org \
duckdb << EOF
INSTALL httpfs;
LOAD httpfs;
select date, plage,
    case 
        when (flag_color = 'BLUE')      THEN '🟦'
        when (flag_color = 'YELLOW')    THEN '🟨'
        when (flag_color = 'RED')       THEN '🟥'
    end as flag
from
read_csv_auto('https://bit.ly/3mAUIPr')
order by date desc
limit 10;
EOF
