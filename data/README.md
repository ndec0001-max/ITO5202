# Data

The dataset is not committed to this repository. Download it and place the CSV files directly in this `data/` folder.

**Dataset:** Brazilian E-Commerce Public Dataset by Olist
**Source:** https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

## Download steps
1. Sign in to Kaggle and open the dataset page above.
2. Click **Download** to get the zip file and unzip
3. Check that the CSV files are directly inside `data/`, not in a subfolder:


## Files used by the notebook
| File | Used for |
|---|---|
| `olist_order_items_dataset.csv` | Revenue (`price`) and `product_id` |
| `olist_orders_dataset.csv` | Order status, purchase and delivery timestamps |
| `olist_customers_dataset.csv` | Customer state |
| `olist_products_dataset.csv` | Product category |
| `product_category_name_translation.csv` | English category names |
| `olist_order_reviews_dataset.csv` | Review scores |

The other three files (payments, sellers, geolocation) can stay in the folder but are not used.
