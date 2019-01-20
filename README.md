# **ETL Project  -  Scapping Car information**
## Group 4: Luciana, Tim, Tao and Max


##  Data Source
- Scraped:   Kijiji.ca (GTA Data)
- Scraped:   Autolist.com (U.S. Data)
- API:          http://www.carqueryapi.com/  (use the json files)
- CSV:        Automobile_data.csv
- CSV:        https://www.kaggle.com/toramky/automobile-dataset/kernels?sortBy=hotness&group=everyone&pageSize=20&datasetId=1291&language=Python




# 1. Extraction 

## Extract all listing car information in GTA area from kijiji webite www.kijiji.ca

### Key Car information is as below:

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


# 2. Transformation

- Clean the dirty data
- merge the api date to get the MPG and displacement information
- plot the data
- [Kijiji Data Transformation and Plot - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_Data_Trans_Plot.ipynb)




# 3. Load

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
 

