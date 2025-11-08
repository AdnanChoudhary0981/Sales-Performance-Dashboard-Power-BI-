
# Power BI Build Guide — Sales Performance Dashboard

## Files
- sales_data.csv
- sales_targets.csv

## Steps
1. Open Power BI Desktop.
2. Get Data -> CSV -> select `sales_data.csv` and `sales_targets.csv`.
3. In Power Query:
   - Change data types: Order Date, Ship Date -> Date; Quantity -> Whole Number; Sales & Profit -> Decimal Number; Year, Month -> Whole Number.
   - Remove duplicates if any.
   - Create a Date table: Home -> Transform data -> New table with full date range (2022-01-01 to 2024-12-31). Mark as Date table.
   - Merge sales_data to Date table on Order Date -> Date to create relationships.
   - Create relationships: sales_data[Order Date] -> Date[Date], sales_targets[MonthStart] -> Date[Date] (or use Year+Month joins).
4. Create relationships in Model view:
   - Date[Date] (1) -> sales_data[Order Date] (*)
   - Date[Year-Month] -> sales_targets[MonthStart] (use MonthStart as date)
5. Data model: keep star schema: Date, Sales, Targets (region-month level)
6. Important measures (use DAX - see DAX_Measures.txt).
7. Build visuals:
   - Page 1 (Executive): KPI cards (Total Sales, Total Profit, Profit Margin %), Sales trend (line), Top 10 products (bar), Profit by Region (map/bar).
   - Page 2 (Regional): Slicers (Region, Category, Date range), Sales by State (map), Sub-Category performance (stacked bar), Discount vs Profit (scatter).
   - Page 3 (Salesperson - simulated): If you add Salesperson column, build leaderboards and target achievement gauges.
8. Add interactivity: slicers, drill-through, tooltips, bookmarks.
9. Formatting: consistent color palette, readable fonts, icons and company logo.

## Export
- File -> Export -> PDF for handing in a report.
- Save `.pbix` for portfolio.

