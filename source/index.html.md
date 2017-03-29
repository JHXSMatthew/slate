---
title: Australian Statistics API by Teamrocket

language_tabs:
  - Code example

toc_footers:
  - <a href='home'>API by TeamRocket</a>
  - <a href='http://www.abs.gov.au/'>Data from abs.gov.com</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

nothing to say right now.


# Parameter Values Constraints

The parameter values constrain is required in our API. Whenever you pass a parameter,
it should be in one of those values, Otherwise it would simply return you an error.

## StatisticsArea

The API only provides two type of statistics area at the moment.

 Value | Description
 ----- | -----------
 Retail| Querying the	monthly	retail turnover of each region and each	category,	for	the specified period of time.
 MerchandiseExports| Querying the monthly value of each commodity listed in the categories, for each region and for defined time period.

## State

A	list of one	or more regions separated	by “,”. The API only returns data in
regions you specified.

Value | Description
----- | -----------
AUS   | Australian
NSW   | New South Wales
VIC   | Victoria
QLD   | Queensland
SA    | South Australia
WA    | Western Australia
TAS   | Tasmania
NT    | Northern Territory
ACT   | Australian Capital Territory

## Category

The category parameter indicates the categories in the specified area. Category values  are different for different areas and you can specified multiple categories separated by ",".

### Retail

Value | Description
----- | -----------
Total | All categories
Food  | Food related category
HouseholdGood | HouseholdGood category
ClothingFootwareAndPersonalAccessory  | Clothing Footware And Personal Accessory category
DepartmentStores   | Stores
CafesResturantsAndTakeawayFood   | Resturants
Other   | others

### Merchandise Exports

Value | Description
----- | -----------
Total | All categories
FoodAndLiveAnimals | Food And Live Animals
BeveragesAndTobacco | Beverages And Tobacco
CrudMaterialAndInedible | Crud Material And Inedible
MineralFuelLubricentAndRelatedMaterial | Mineral Fuel Lubricent And related material
AnimalAndVegitableOilFatAndWaxes | Animal and vegitable oil fat and waxes
ChemicalsAndRelatedProducts | Chemicals And Related Products
ManufacutedGoods | Manufacuted Goods
MachineryAndTransportEquipments | Machinery And Transport Equipments
OtherManucacturedArticles | Other Manucactured Articles
Unclassified | Unclassified

## Date

All the input date is in the format	of YYYY-MM-DD.


# Retail

##Get Retail data

```text
Example request:

http://45.76.114.158/api
        ?StatisticsArea=Retail
        &State=NSW&Category=DepartmentStores
        &startDate=2013-12-01
        &endDate=2014-01-01
```

> The example Request give JSON response like this:

```json
{  
   "header":{  
      "status":"success"
   },
   "data":{  
      "MonthlyRetailData":[  
         {  
            "RegionalData":[  
               {  
                  "State":"NSW",
                  "Data":[  
                     {  
                        "Date":"2013-12-31",
                        "Turnover":883.5
                     },
                     {  
                        "Date":"2014-01-31",
                        "Turnover":473.5
                     }
                  ]
               }
            ],
            "RetailIndustry":"DepartmentStores"
         }
      ]
   }
}
```

Retail data.

### HTTP Request

`GET http://45.76.114.158/api/`

### Required Query Parameters

Parameter | Default | Values | Description
--------- | ------- | -----------| ---------
StatisticsArea | null | Retail | must be Retail to get retail data.
State | null | State | A list of one or	more regions separated by ",".
startDate | null | Date | The starting date.
endDate | null | Date | The ending date.

### Optional Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
pretty | null | returns a Human readable pretty JSON



<aside class="success">
    Check parameter values constrain for legal values;
</aside>


# Merchandise Exports

##Get Merchandise Exports data

```text
Example request:

http://45.76.114.158/api
    ?StatisticsArea=MerchandiseExports
    &State=NSW
    &Category=CrudMaterialAndInedible
    &startDate=2013-12-01
    &endDate=2014-01-01
```

> The example Request give JSON response like this:

```json
{  
   "header":{  
      "status":"success"
   },
   "data":{  
      "MonthlyCommodityExportData":[  
         {  
            "RegionalData":[  
               {  
                  "State":"NSW",
                  "Data":[  
                     {  
                        "Date":"2013-12-31",
                        "Value":461563.709
                     },
                     {  
                        "Date":"2014-01-31",
                        "Value":317914.026
                     }
                  ]
               }
            ],
            "Commodity":"CrudMaterialAndInedible"
         }
      ]
   }
}
```

Merchandise Exports data.

### HTTP Request

`GET http://45.76.114.158/api/`

### Required Query Parameters

Parameter | Default | Values | Description
--------- | ------- | -----------| ---------
StatisticsArea | null | MerchandiseExports | must be Retail to get retail data.
State | null | State | A list of one or	more regions separated by ",".
startDate | null | Date | The starting date.
endDate | null | Date | The ending date.

### Optional Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
pretty | null | returns a Human readable pretty JSON



<aside class="success">
    Check parameter values constrain for legal values.
</aside>
