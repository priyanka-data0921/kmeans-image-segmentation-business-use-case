# K-Means Clustering: From Image Segmentation to Business Insights

## Why this project?
Businesses collect large amounts of data, but raw data alone does not reveal useful patterns. A common challenge is finding groups of similar items so teams can understand their data and decide what to do next.

This project uses **K-Means clustering** on image pixels as a visual, hands-on way to understand that idea. The same clustering concept can also be applied to customer, product, and account data.

## Business problem
Imagine a business has thousands of records but no predefined categories. It may want to discover groups with similar characteristics.

Examples:
- An online retailer groups customers by purchasing behavior.
- A customer-success team groups accounts by revenue, product adoption, and support activity.
- A retailer groups products by sales or pricing patterns.
- An image workflow simplifies an image using fewer representative colors.

K-Means can help discover groups. It does **not** decide what action the business should take; people interpret the groups and choose the next step.

## What is K-Means?
K-Means is an **unsupervised learning** algorithm. It groups data points into a chosen number of clusters, K. It assigns each point to its closest centroid, recalculates the centroids from the assigned points, and repeats until the solution stabilizes or reaches its iteration limit.

## Why image segmentation?
A digital image is numerical data. Each pixel has three color features: red, green, and blue (RGB). Here, each pixel is treated as a data point with three features.

K-Means groups pixels with similar RGB values. Each pixel is replaced by the representative color of its assigned cluster. With K = 5, the reconstructed image uses five cluster-center colors. This makes grouping visible, while some fine color variation is lost.

## What the notebook does
1. Loads a ladybug image and converts it into a NumPy array.
2. Downsamples by keeping every fourth row and column to reduce computation.
3. Reshapes the image into rows of RGB pixel values.
4. Applies K-Means with K = 5 and reconstructs the segmented image.
5. Measures clustering fit using inertia.
6. Plots inertia for K values 1–20 (elbow-style view).
7. Repeats K-Means 10 times for K = 5 and calculates mean, standard deviation, minimum, and maximum inertia.
8. Displays the best- and worst-inertia results.
9. Runs 10 trials for each K from 1–20 and plots mean inertia with a min–max ribbon.
10. Applies the same process to a flower image supplied by scikit-learn.

## Results from this run
For the ladybug image with K = 5:
- Single-run inertia (random_state = 1): **588,422,570.49**
- Mean inertia across 10 runs: **609,478,666.10**
- Standard deviation: **33,276,272.45**
- Minimum inertia: **588,407,150.42**
- Maximum inertia: **676,667,390.98**

Different initial centroid positions can lead to different outcomes. Inertia is the sum of squared distances from points to their assigned cluster center. Lower inertia indicates tighter clusters for that run, but inertia generally decreases as K increases. Therefore, inertia alone is not enough to choose K; consider visual quality, usefulness, and complexity too.

## Business applications

### Customer segmentation
A retailer could represent customers using purchase frequency, average order value, and category spend. Clustering may reveal groups such as frequent high-value shoppers or occasional shoppers. The business could investigate those groups and consider different loyalty, engagement, or retention strategies.

### Salesforce account and customer-success analysis
A team could cluster accounts using annual revenue, product adoption, opportunity pipeline, and support-case activity. The groups could help teams prioritize account reviews, identify customers who may benefit from training, spot growth opportunities, and investigate low adoption or rising support activity.

### Image and media workflows
Grouping similar pixel colors creates a reduced-color image representation. It illustrates how clustering can simplify large datasets into representative groups.

**Important:** Clustering identifies patterns; it does not automatically explain why a group exists, predict churn, or prescribe an action. Business teams must interpret and validate the groups.

## Limitations
- K must be selected in advance.
- Results can depend on initial centroid positions; repeated runs help assess variability.
- Feature selection and scaling matter because K-Means uses numerical distances.
- This notebook uses RGB values only, not pixel position or texture. Nearby pixels are therefore not guaranteed to belong to the same visual region.
- Clusters need human interpretation.

## Technology
Python · Jupyter Notebook · NumPy · Matplotlib · scikit-learn · Pillow

## Key takeaway
The purpose is not simply to reduce image colors. It is to understand a reusable ML idea: **find similarities in raw data, group related data points, evaluate the groups, and use the insight to support better decisions.** Image segmentation provides a visual example; customer and account segmentation show how the same concept can support business analysis.
