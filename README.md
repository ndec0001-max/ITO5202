# ITO5202 Assessment 1: Analysing Historical Data with System Performance

| | |
|---|---|
| **Student ID** | 29701201 |
| **Unit code** | ITO5202 |
| **Teaching period / year** | Teaching Period 5 (TP5), 2026 |
| **Dataset** | Brazilian E-Commerce Public Dataset by Olist |
| **Source** | https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce |

## Project overview
This project analyses the Olist Brazilian e-commerce dataset (about 100k orders placed between 2016 and 2018) using Apache Spark.

- **Part A** answers a multi-step business question: which product categories lead revenue in each Brazilian state and quarter, whether late deliveries are associated with lower review scores, and which high-revenue category–state combinations are held back by logistics. The query is implemented in both the DataFrame API and Spark SQL, and the two implementations are validated as equivalent.
- **Part B** examines system behaviour: hash vs range partitioning on `product_id`, execution-time benchmarking, execution plan interpretation, and Spark Web UI DAG analysis.

## Repository structure
| Path | Purpose |
|---|---|
| `README.md` | This file |
| `assessment1.ipynb` | Main notebook: all code, results and analysis |
| `proposal/proposal.md` | Approved dataset proposal (Phase 1) |
| `data/README.md` | How to download the dataset into `data/` |
| `.gitignore` | Excludes the raw data, notebook checkpoints and system files |

The raw CSV files are **not** committed (see `data/README.md`).

## Environment used
| Setting | Value |
|---|---|
| Execution mode | Spark local mode (`local[*]`) inside a Docker container |
| Spark version | 4.1.1 |
| Python version | 3.13.12 |
| CPU cores available to the container | 8 |
| Spark driver memory | 4 GB |
| Shuffle partitions | 16 (2 × cores) |
| Session time zone | UTC |

Environment Setup part of the notebook prints the full environment table when it runs.

## Reproducing the results

### 1. Prerequisites
- **Docker Desktop.** Under **Settings → Resources**, allocate at least **8 CPUs** and **6 GB of memory**. The notebook requests 4 GB for the Spark driver, and the rest is needed for Python and the operating system.
- **Git.**
- A **Kaggle account**, to download the dataset.

### 2. Clone the repository
```bash
git clone https://github.com/ndec0001-max/ITO5202.git
cd ITO5202
```

### 3. Download the dataset
Download the dataset from Kaggle and unzip it into the `data/` folder, so the CSV files sit directly inside `data/`. Full instructions are in [`data/README.md`](data/README.md).


### 5. Run the notebook
1. In Jupyter, open `assessment1.ipynb`.
2. Select **Kernel → Restart & Run All**.
   - Environment Setup section must run first after a fresh kernel, because Spark's driver memory can only be set when the JVM starts.
   - The notebook stops early with a clear message if any data file is missing.

A full run takes a few minutes. Part A results are deterministic and should match the submitted notebook exactly. Part B execution times depend on the machine, so they will differ between environments.

## Notes
- Only six of the nine Olist files are used. The payments, sellers and geolocation files are not required.
- All query parameters (date range, thresholds, top-N) are set in one cell at the start of Part A (Section A.2.1).
