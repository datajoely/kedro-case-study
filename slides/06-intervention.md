---
layout: two-cols-header
layoutClass: 'gap-3'
---

# Intervention

We made two key backwards compatible changes, eventually removing the Jinja2 feature after a period of clear deprecation.

::left::
### <mdi-factory/> Dataset Factories
**Pattern matching approach** 

- Addressed the key pain point of super-long YAML files
- Much easier to read than Jinja2
- Also introduced CLI command `kedro catalog resolve`

````md magic-move
```yaml
# catalog.yml - Before
csv_boats:
  type: pandas.CSVDataset
  filepath: data/01_raw/boats.csv

csv_cars:
  type: pandas.CSVDataset  
  filepath: data/01_raw/cars.csv

csv_planes:
  type: pandas.CSVDataset
  filepath: data/01_raw/planes.csv
```

```yaml {2}
# catalog.yml - After
"csv_{dataset_name}":
  type: pandas.CSVDataset
  filepath: data/01_raw/{dataset_name}.csv
```
````

::right::


### <mdi-cog-outline/> `OmegaConf` Resolvers

**Dynamic configuration** 

- Sprinkle of dynamism **without being Turing complete**
- Removed the need to use more complex extensions / overrides
- Kept the API familiar, minimal syntax introduced

````md magic-move
```yaml
# catalog.yml - Before
my_dataset:
  type: polars.CSVDataset
  filepath: data/01_raw/sales.csv
  load_args:
    dtypes:
      product_age: "Float64" 
      # native YAML provides a string, not a Python type 

database:
  host: localhost
  port: 5432
```

```yaml {7,11-12}
# catalog.yml - After  
my_dataset:
  type: polars.CSVDataset
  filepath: data/01_raw/sales.csv
  load_args:
    dtypes:
      product_age: "${polars:Float64}" 
      # Retrieve the type from the polars library

database:
  host: "${oc.env:DB_HOST,localhost}"
  port: "${oc.env:DB_PORT,5432}"
```

```python {5-7}
# settings.py - Register resolver
import polars as pl

CONFIG_LOADER_ARGS = {
    "custom_resolvers": {
        "polars": lambda x: getattr(pl, x)
    }
}
```
````
