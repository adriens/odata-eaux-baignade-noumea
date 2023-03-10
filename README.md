# ❔ About

See https://www.kaggle.com/code/adriensales/la-qualit-des-eaux-de-baignade-noum-a


# 🦆 `DuckDb` hacks

```sql
INSTALL httpfs;
LOAD httpfs;
select * from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/latest.csv';
```

```sql
INSTALL httpfs;
LOAD httpfs;
select * from 'https://raw.githubusercontent.com/adriens/odata-eaux-baignade-noumea/main/data/historic.csv';
```
