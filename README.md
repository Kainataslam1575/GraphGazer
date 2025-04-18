
# File: graphs/insight_grapher.py
import pandas as pd
import matplotlib.pyplot as plt

class GraphGazer:
    def __init__(self, file_path):
        self.file_path = file_path
        self.data = None

    def load_data(self):
        try:
            self.data = pd.read_csv(self.file_path)
            print("Data loaded successfully.")
        except Exception as e:
            print("Error loading data:", e)

    def sales_by_product(self):
        if self.data is not None:
            product_sales = self.data.groupby('Product')['Sales'].sum()
            product_sales.plot(kind='bar', title='Sales by Product', color='skyblue')
            plt.xlabel('Product')
            plt.ylabel('Total Sales')
            plt.tight_layout()
            plt.savefig('sales_by_product.png')
            plt.close()
            print("Bar graph saved as 'sales_by_product.png'.")

    def sales_by_region(self):
        if self.data is not None:
            region_sales = self.data.groupby('Region')['Sales'].sum()
            region_sales.plot(kind='pie', title='Sales by Region', autopct='%1.1f%%')
            plt.ylabel('')
            plt.tight_layout()
            plt.savefig('sales_by_region.png')
            plt.close()
            print("Pie chart saved as 'sales_by_region.png'.")


# File: main.py
from graphs.insight_grapher import GraphGazer

def main():
    gg = GraphGazer('data/sales_data.csv')
    gg.load_data()
    gg.sales_by_product()
    gg.sales_by_region()

if __name__ == "__main__":
    main()


# File: requirements.txt
pandas
matplotlib


# File: README.md
GraphGazer is a Python-based beginner project designed to simulate Power BI-like data insights using graphs and charts.

Features

- Load sales data from a CSV
- Analyze and visualize:
  - Sales by product (bar chart)
  - Sales by region (pie chart)

Setup

1. Install dependencies:
   pip install -r requirements.txt

2. Run the project:
   python main.py

3. Output:
   - sales_by_product.png
   - sales_by_region.png

Technologies Used

- Python
- Pandas
- Matplotlib


# File: data/sales_data.csv
Date,Product,Region,Sales
2024-01-01,Widget A,North,1000
2024-01-02,Widget B,South,850
2024-01-03,Widget A,East,920
2024-01-04,Widget B,North,1130
2024-01-05,Widget A,South,980
