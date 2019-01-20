# **ETL Project  -  Scapping Car information**
## Group 4: Luciana, Tim, Tao and Max


##  Data Source
- Scraped:   [Kijiji Car Website (GTA Data)](https://www.kijiji.ca/b-cars-vehicles/city-of-toronto/c27l1700273)
- Scraped:   <https://www.autolist.com> (U.S. Data)
- API:       [Car Query API](http://www.carqueryapi.com/) (use the [json files](data/carquery.json))
- CSV:       [Fuel Economy Web Service](https://www.fueleconomy.gov/feg/ws/index.shtml#fuelType1) offers the fuel economy database [csv data](data/vehicles.csv)
- CSV:        <https://www.kaggle.com/toramky/automobile-dataset/kernels?sortBy=hotness&group=everyone&pageSize=20&datasetId=1291&language=Python>




# 1. Extraction 

## 1.1. Extract all listing car information in GTA area from [kijiji website](www.kijiji.ca)

[A. Kijiji Scaper (raw data)  - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/kijii_car_scaper.ipynb)

[B. Kijiji Scaper (clean data with vin number and image link)  - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/kijiji_car_scaper_fullset.ipynb)
#### Key Car information is as below:

- 'brand'
- 'model'
- 'model_year' : Type: int
- 'list_price' : Type: int
- 'color'
- 'configration'
- 'condition'
- 'body_type'
- 'wheel_config'
- 'transmission'
- 'fuel_type'
- 'mileage'  : Type: int
- 'carfax_link'
- 'vin_number'
- 'image_link'
- 'dealer_address'

### Examples:

#### Car Information link: https://www.kijiji.ca/v-cars-trucks/city-of-toronto/2009-ford-f-150-xlt-super-crew-4x4/1385290163

- brand: 'Ford'
- model: 'F-150'
- model_year:'2009'
- list_price:'11999'
- color: 'Blue'
- configration: 'XLT'
- condition: 'Used'
- body_type: 'Pickup Truck'
- wheel_config: '4 x 4'
- transmission: 'Automatic'
- fuel_type:  'Gasoline'
- mileage: '204000'
- carfax_link: 'https://www.carproof.com/order?ref=kijiji&vin=1FTRW14819FB42024'
- vin_number: '1FTRW14819FB42024'
- image_link: 'https://i.ebayimg.com/00/s/NDgwWDY0MA==/z/c9AAAOSwDkBbpAaq/$_59.JPG'
- dealer_address: '2 Castleton Ave unit 3, York, ON, M6N 3Z5'

## 1.2. Extract all listing car information from [autolist website](https://www.autolist.com)
[Autolist.com scaper - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/mlouisju/ETL%20Project%20-%20Autolist.ipynb)

# 2. Transformation

- Clean the dirty data
- merge the api date to get the MPG and displacement information
- plot the data
- [Kijiji Data Transformation and Plot - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_Data_Trans_Plot.ipynb)
- [Kijiji Data merge with MPG/Displacement- Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_mpgdata_merge.ipynb)
- [Autolist Data merge with Fuel Economy Database - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Auto_trader_merge.ipynb)



# 3. Data Plotting

### 3.1 Kijiji Data Plot
 - **Total car sales on kijiji website in GTA area**
 ![Total car sales on kijiji website in GTA area](plot_image/kijiji_average_mileage.png)
 
 - **Brand Numbers on kijiji website in GTA area**
 ![Brand Numbers on kijiji website in GTA area](plot_image/kijiji_brand_count.png)
 
 - **Average price of vehicles by vehicle type and brand**
 ![Average price of vehicles by vehicle type and brand](plot_image/kijiji_type_price.png)
 
 - **Average mileage of vehicles by vehicle type and brand**
 ![Average mileage of vehicles by vehicle type and brand](plot_image/kijiji_type_mileage.png)
 
 - **Average Mileages based on Brands on Kijiji website**
 ![Average Mileages based on Brands on Kijiji website](plot_image/kijiji_average_mileage.png)
 
 - **Average Price based on Brands on Kijiji website**
 ![Average Price based on Brands on Kijiji website](plot_image/kijiji_average_price.png)
 
 
### 3.2 Autolist Data Plot

- **Price vs. Miles per Galon - cars made in 2015 (USA)**
![Price vs. Miles per Galon - cars made in 2015 (USA)](plot_image/auto_trader_price2015_MPG.png)

- **Displacement vs. Miles per Galon (USA data)**
![Displacement vs. Miles per Galon (USA data)](plot_image/auto_trader_displacement_MPG.png)

- **Price vs. Displacement - cars made in 2015 (USA)**
![Price vs. Displacement - cars made in 2015 (USA)](plot_image/auto_trader_price2015_displacement.png)

- **[MPG by make (USA data)]**
![MPG by make (USA data)](plot_image/auto_trader_make_MPG.png)

- **[Displacement by make (USA data)]**
![plot_image/auto_trader_make_displacement.png]

- **[]**



# 4. Load

- put all data into MySql server via pymysql 
- load code :
 ```
   import pandas as pd`
   import pymysql
   pymysql.install_as_MySQLdb()
   from sqlalchemy import create_engine
   conn = create_engine('mysql://root:password@127.0.0.1/favorite_db')
   kijiji_full_df = pd.read_csv('kijiji_car.csv')
   kijiji_full_df.to_sql('kijiji_origin', con=conn)
 
 
 

