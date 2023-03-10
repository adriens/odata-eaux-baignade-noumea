# ❔ About

See https://www.kaggle.com/code/adriensales/la-qualit-des-eaux-de-baignade-noum-a


# 🦆 `DuckDb` hacks

```sql
INSTALL httpfs;
LOAD httpfs;
select * 
from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/latest.csv';
```

```sql
INSTALL httpfs;
LOAD httpfs;
select *
from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/historic.csv';
```

You can also use (nicer) short urls : 

```shell
duckdb << EOF
-- historic
INSTALL httpfs;
LOAD httpfs;
.prompt "🦆 🏖️  > "
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
.prompt "🦆 🏖️  > "
select *
from read_csv_auto('https://bit.ly/3ZCJ1X5') as latest;
EOF
```
