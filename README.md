# SCT_ML_2
ABOUT:

This program performs customer segmentation using the K-Means clustering algorithm based on the RFM model (Recency, Frequency, Monetary).It is designed to take any Excel file containing customer transaction data.

FEATURES:

1) Loads and validates the dataset
2)Reads the file using pandas
3)Ensures required columns (CustomerID, InvoiceNo, InvoiceDate/Date, Quantity, UnitPrice) are present
4)Features engineering (RFM calculation)
5)Recency: Number of days since the customer’s last purchase
6)Frequency: Number of distinct invoices
7)Monetary: Total money spent

USER INTERFACE:

1) Select Excel File: Button through which an Excel file (.xlsx or .xls) containing customer data can be uploaded.
2) Run Clustering: Processes the uploaded file using RFM analysis and K-Means clustering to segment customers.
3) Show Graphs: Displays scatter plots of Recency vs Monetary and Frequency vs Monetary, with clusters shown in different colors.
4) Output Label: Shows whether the file was processed successfully or if an error occurred.
4) Error Handling: If the file is invalid or missing required columns, an error message is displayed in the output label.
5) Auto-save Results: Saves the clustered data as customer_segments_excel.csv in the same folder as the uploaded file.

REQUIREMENTS:

1) pandas – For reading and manipulating Excel/CSV data
2) numpy – For numerical operations
3) matplotlib – For creating scatter plots of clusters
4) scikit-learn (sklearn) – For:
5) KMeans clustering
6) StandardScaler for data normalization
7) openpyxl – For reading .xlsx Excel files
8) os – For file and path handling (built-in, no install needed)
9) datetime – For date manipulation (built-in, no install needed)

HOW THE CODDE WORKS?

1. RFM Calculation (Basic Arithmetic)
Recency = (Date of last purchase → subtracted from snapshot date) → gives number of days since last purchase.

Recency = (snapshot_date - last_purchase_date).days

Frequency = Count of unique invoice numbers per customer.
Monetary = Quantity × Unit Price, summed for each customer.

That’s simple subtraction, counting, and multiplication.

2. Data Scaling (Standardization)
You use StandardScaler, which applies:

𝑧=(𝑥−𝜇)/𝜎

Where:
x = original value
μ = mean of the column
σ = standard deviation of the column

This makes Recency, Frequency, and Monetary all have mean = 0 and standard deviation = 1, so clustering isn’t biased toward large numbers.

3. K-Means Clustering (Vector Geometry)
K-Means works by:

Choosing k random points (centroids) in the data space.

Assigning each data point to the nearest centroid (using Euclidean distance):

𝑑(𝑝,𝑞)=root(∑(p-q)^2)
 
Moving each centroid to the average position of its assigned points.
Repeating until centroids stop moving much (convergence).
This is iterative optimization and uses linear algebra + geometry.

4. Visualization (Coordinate Mapping)
Scatter plots are just mapping two numeric features to an X-Y plane with color showing the cluster label.

<img width="1920" height="1080" alt="Screenshot (39)" src="https://github.com/user-attachments/assets/c135dbd7-d19c-495d-9aac-0387f97890c3" />
<img width="1920" height="1080" alt="Screenshot (40)" src="https://github.com/user-attachments/assets/d4ed80b5-7846-43b0-9899-2954de57ec5e" />
<img width="1920" height="1080" alt="Screenshot (41)" src="https://github.com/user-attachments/assets/d893bda5-d826-44a5-a090-87ede3b9695c" />

