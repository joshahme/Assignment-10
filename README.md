# Assignment-10
Building R package
# Load necessary libraries
> library(dplyr)
> library(ggplot2)
> # Create a fictional dataset
> sales_data <- data.frame(
+     Product = c("A", "B", "C", "A", "B", "C", "A", "B", "C"),
+     Month = rep(c("Jan", "Feb", "Mar"), times = 3),
+     Sales = c(100, 150, 80, 120, 180, 90, 110, 160, 85)
+ )
> > # Explore the dataset
> head(sales_data)
  Product Month Sales
1       A   Jan   100
2       B   Feb   150
3       C   Mar    80
4       A   Jan   120
5       B   Feb   180
6       C   Mar    90
> summary(sales_data)
   Product             Month               Sales      
 Length:9           Length:9           Min.   : 80.0  
 Class :character   Class :character   1st Qu.: 90.0  
 Mode  :character   Mode  :character   Median :110.0  
                                       Mean   :119.4  
                                       3rd Qu.:150.0  
                                       Max.   :180.0  

> # Calculate total sales for each product
> total_sales <- sales_data %>%
+     group_by(Product) %>%
+     summarise(Total_Sales = sum(Sales))

> # Visualize total sales using a bar plot
> ggplot(data = total_sales, aes(x = Product, y = Total_Sales, fill = Product)) +
+     geom_bar(stat = "identity") +
+     labs(title = "Total Sales by Product",
+          x = "Product",
+          y = "Total Sales") +
+     theme_minimal()

> # Calculate average sales per month
> average_sales <- sales_data %>%
+     group_by(Month) %>%
+     summarise(Average_Sales = mean(Sales))

> # Visualize average sales per month using a line plot
> ggplot(data = average_sales, aes(x = Month, y = Average_Sales, group = 1)) +
+     geom_line(color = "blue") +
+     geom_point(color = "blue") +
+     labs(title = "Average Sales per Month",
+          x = "Month",
+          y = "Average Sales") +
+     theme_minimal()
