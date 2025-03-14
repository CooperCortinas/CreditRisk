# Data Dictionary

## payment_data.csv (Customer’s Card Payment History)

| Column Name       | Data Type  | Description |
|-------------------|-----------|-------------|
| `id`             | Integer    | Unique customer ID. |
| `OVD_t1`         | Integer    | Number of times overdue (Type 1). |
| `OVD_t2`         | Integer    | Number of times overdue (Type 2). |
| `OVD_t3`         | Integer    | Number of times overdue (Type 3). |
| `OVD_sum`        | Integer    | Total overdue days. |
| `pay_normal`     | Integer    | Number of times the customer made a normal payment. |
| `prod_code`      | String     | Code for the credit product associated with the account. |
| `prod_limit`     | Float      | Credit limit for the product. |
| `update_date`    | Date       | Last date the account was updated. |
| `new_balance`    | Float      | Current balance of the product. |
| `highest_balance`| Float      | Highest balance recorded in history. |
| `report_date`    | Date       | Date of the most recent payment report. |

## customer_data.csv (Customer’s Demographic and Encoded Category Data)

| Column Name  | Data Type   | Description |
|-------------|------------|-------------|
| `id`        | Integer    | Unique customer ID. |
| `fea_1`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_2`     | Float      | Numerical feature (demographic or financial attribute). |
| `fea_3`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_4`     | Float      | Numerical feature (demographic or financial attribute). |
| `fea_5`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_6`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_7`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_8`     | Float      | Numerical feature (demographic or financial attribute). |
| `fea_9`     | Categorical | Encoded categorical feature (category attribute). |
| `fea_10`    | Float      | Numerical feature (demographic or financial attribute). |
| `fea_11`    | Float      | Numerical feature (demographic or financial attribute). |
| `label`     | Integer (0/1) | **Target variable** - `1`: High credit risk, `0`: Low credit risk. |

## Notes
- The **`id` column** is the primary key in both datasets and can be used for merging.
- **Category features** (`fea_1`, `fea_3`, `fea_5`, `fea_6`, `fea_7`, `fea_9`) are encoded values representing categorical attributes.
- The **`label` column** in `customer_data.csv` is the **classification target** (binary: high-risk vs. low-risk).
