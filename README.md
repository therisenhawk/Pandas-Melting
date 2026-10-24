# Pandas Melt

This project contains two examples of reshaping data in pandas from a wide format to a long format. The first example does it manually, while the second one uses a function that can be reused with different datasets.

## What is Wide and Long Format?

Wide format means that different categories or time periods are stored in separate columns.

For example:

| fruit | Monday | Tuesday |
|---|---:|---:|
| Apple | 10 | 15 |
| Banana | 20 | 25 |

Long format means that those columns are combined into two columns, one for the category and one for its values.

| fruit | day | sales |
|---|---|---:|
| Apple | Monday | 10 |
| Banana | Monday | 20 |
| Apple | Tuesday | 15 |
| Banana | Tuesday | 25 |

This format is often easier to work with when analyzing data or creating visualizations.

## Files

### 1. Manual Melt

The first example shows how to reshape a DataFrame without using pandas' built-in `melt()` function.

The process is:

1. Copy the columns that need to be kept.
2. Create a new column for the day.
3. Create a sales column using the values from the corresponding day.
4. Repeat the process for the other days.
5. Combine the resulting DataFrames using `pd.concat()`.

This example helps explain what happens behind the scenes when reshaping data.

### 2. Custom Melt Function

The second example turns the same idea into a reusable function called `melt()`.

The function takes four arguments:

- `df`: the DataFrame being reshaped.
- `col_vals`: the columns that need to be converted into rows.
- `key`: the name of the new column that stores the original column names.
- `value`: the name of the new column that stores their values.

The function first identifies the columns that should stay unchanged. It then loops through the selected columns, creates a small DataFrame for each one, and combines everything using `pd.concat()`.

The example uses monthly sales data, converting the January, February, and March columns into a `Month` column and a `Sales` column.

## Requirements

- Python 3
- pandas

Install pandas if needed:

```bash
pip install pandas
```

## What I Learned

This project helped me understand how to reshape data from wide format to long format, select and copy columns, create new columns, loop through column names, and combine DataFrames.

It also helped me understand how to turn a series of repeated operations into a reusable function instead of writing the same code for every column.
