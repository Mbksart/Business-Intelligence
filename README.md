# Business-Intelligence
Data Analysis for business intelligence
1. Purpose
This document defines the standard approach for building a Business Intelligence solution using Power BI, Power Query, a dimensional data model, and DAX.

# The solution should support:
Executive KPI reporting
Sales and revenue analysis
Customer analysis
Product performance
Profitability analysis
Time-based trends
Budget vs. actual analysis
Year-over-year and month-over-month analysis
Interactive filtering and drill-down
*Consistent and reusable business measures*
<pre> 
  Source Systems
     |
     v
Power Query / ETL
     |
     v
Staging / Transformation
     |
     v
Star Schema
     |
     +--------------------+
     |                    |
     v                    v
Dimension Tables      Fact Tables
     |                    |
     +---------+----------+
               |
               v
        DAX Semantic Model
               |
               v
        Power BI Reports
  </pre>

<pre> 
  # The preferred model is a star schema, where fact tables contain measurable business events and dimension tables contain descriptive attributes.

3. Recommended Data Model
3.1 Fact Tables
FactSales
# Example columns:
- SalesKey
- DateKey
- CustomerKey
- ProductKey
- SalespersonKey
- LocationKey
- OrderNumber
- OrderQuantity
- UnitPrice
- DiscountAmount
- SalesAmount
- CostAmount
- TaxAmount
- ShippingAmount

FactBudget
BudgetKey
DateKey
ProductKey
LocationKey
DepartmentKey
BudgetAmount

FactInventory
InventoryKey
DateKey
ProductKey
LocationKey
OpeningStock
ReceivedQuantity
SoldQuantity
ClosingStock

Additional fact tables can be added when the business requires them.

4. Dimension Tables
DimDate
Required for all time intelligence.

#Recommended columns:

Date
DateKey
Year
Quarter
QuarterNumber
Month
MonthNumber
MonthYear
Week
WeekNumber
Day
DayOfWeek
DayOfWeekNumber
IsWeekend
FiscalYear
FiscalQuarter
FiscalMonth

DimCustomer
CustomerKey
CustomerID
CustomerName
CustomerSegment
CustomerType
Industry
Region
City
Country
AcquisitionDate

DimProduct
ProductKey
ProductID
ProductName
Category
Subcategory
Brand
Supplier
UnitCost
StandardPrice

DimLocation
LocationKey
LocationName
Region
State
Country
Territory

DimSalesperson
SalespersonKey
SalespersonID
SalespersonName
Team
Department
Manager
Region
</pre>
