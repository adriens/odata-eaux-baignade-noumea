# ❔ About

See https://www.kaggle.com/code/adriensales/la-qualit-des-eaux-de-baignade-noum-a


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
