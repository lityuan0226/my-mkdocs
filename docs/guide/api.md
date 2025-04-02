# API
The API of the passenger flow platform is a development system for VIONVISON Technology Co., Ltd. to obtain the original data of the equipment for users. After users choose to access the cloud platform,you can get data to other platform by the API.

The API address is : [`http://api.store.keliuyun.com`][URL][^1]

*[API]: Application Programming Interface
[URL]: http://api.store.keliuyun.com
[^1]:
  This is a footnotes!

## 1. Login
You can use the user name and password to obtain the token through this interface. Other interfaces will use the token obtained here

!!! note "Notice"
    The appkey is your company name。Example：vionvision

 | ``Verb``: POST  
 | ``Path``: api/v1/user/login  
 | ``Header``: (Content-Type: application/json)  

 | Request Body

	```json
	{
		appkey:"xxxxx",                  // appkey,your company name
		username:"your username",           //username
		password:"your password"        //password
	}
	```

 | Response Body: 

	```json
	{
		atoken:"2cb4ff2f-191a-4b7f-8ef4-7e59bb3d87f4",	   //token info
		msg_code:200,                                      //request status
		msg_info:"Login Success"
	}
	```

## 2. Store Info List
You can get all stores through this interface.


 | ``Verb``: GET  
 | ``Path``: api/v1/base/plazaInfo
 | ``Header``: (authorization, {$atoken})

 | Request Params:
   - None


 | Response Body:

	```json
	{
		msg_code: 200,
		msg_info: "this is info",
		data: [{
			plaza_unid: "1231233",		//unid of store，Global unique identifier of store information
			plaza_externalid: "9876632",	//The external code of the store is generally used to keep consistent with other system codes when interfacing with other systems.
			plaza_name: "store name",		//store name
			group_id:"group id",			//id of the group to which the store belongs
			group_name:"group name",		//name of the group to which the store belongs
			time_zone: "+01:00",            // time zone
			"business_start_time": "00:00:00",  // business time
	        "business_end_time": "00:00:00"
		},
		{
			plaza_unid: "1231233",
			plaza_externalid: "9876632",
			plaza_name: "store name",
			group_id:"group id",
			group_name:"group name",
			time_zone: "+01:00",
			"business_start_time": "00:00:00",
	        "business_end_time": "00:00:00"
		},	
		{
			plaza_unid:"1231233",
			plaza_externalid: "9876632",
			plaza_name: "store name",
			group_id:"group id",
			group_name:"group name",
			time_zone: "+01:00",
			"business_start_time": "00:00:00",
	        "business_end_time": "00:00:00"
		}]
	}
	```

## 3. Store-Entrance Info List
You can get all stores-entrance through this interface.

| ``Verb``: GET  
| ``Path``: api/v1/base/gateInfo
| ``Header``: (authorization, {$atoken})
| Request Params:

   - plaza_unid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6

| Response Body:

```
{
    msg_code: 200,
    msg_info: "success",
    data: [{
        plaza_unid: "1231233",		//unid of store，Global unique identifier of store information
        gate_unid:"456456",		// unid of store-entrance. Global unique identifier of store-entrance
        is_mall_gate: 1,	//The store-entrance type, 1-Store Main Entrance
        gate_name: "store-entrance name",		//store-entrance name
        gate_status:1,			// The store-entrance status, 1-Open
    }
}
```

## 4. Store Counting Data Hourly
You can get all the  counting data from this interface.
Now only hourly data is ready.
Notice: The params startTime and endTime must be in one day,if you want more data in serval days,you should call this interface more times.

 | ``Verb``: GET
 | ``Path``: api/v1/face/storeCountingDataHourly
 | ``Header``: (authorization, {$atoken})
 | Request Params:

```
- plaza_unid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
- startTime: start time of the data you need 。Example：："2019-01-01 10:00:00"
- endTime:  end time of the data you need 。Example："2019-01-01 22:00:00"
```

 | Response Body:

```json
	{
		msg_code: 200,
		msg_info: "Success",
		data: [{
			plaza_unid: "83c2266f-a29b-478a-8a59-2ed54e144641",  // unid of store
			countdate: "2018-01-01",                             // countdate
			counttime: "2018-01-01 10:00:00",                    // counttime
			innum: 45,                                           // Total Traffic IN
			outnum: 48,                                          // Total Traffic OUT
			customer: 31,                                        // Total Customer IN
			customer_repeat: 10,                                 // Total Customer Repeats IN
			customer_out: 34,                                    // Total Customer OUT
			customer_out_repeat: 11,                             // Total Customer Repeats OUT
			staff: 4,                                            // Total Staff IN
			staff_out: 3,                                         // Total Staff OUT
			adult: 4,
			child: 3,
			male: 3,
			female: 4,
			group: 3,
            one_visitor_group: 0,
            two_visitor_group: 0,
            more_than_two_visitor_group: 0
		}]
	}
```

## 5. Store Hourly Customer Segment Data
> Two methods are available for obtaining store hourly customer segment data based on time parameters:
1.Retrieve data within a specific time frame using startTime and endTime.
2.Obtain data updated after a certain point in time using modifyTime. This data includes updates made within the last three days.

 | ``Verb``: GET  
 | ``Path``: api/v2/reid/plazaHour
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plazaUnid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- startTime: start time of the data you need.Example：："2019-01-01 10:00:00",           
	- endTime:  end time of the data you need.Example："2019-01-01 22:00:00"      
	- modifyTime: the timestamp of the most recent data modification.Example："2019-01-01 23:00:00" 
  -
 | Response Body:

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
        "plazaUnid": "83c2266f-a29b-478a-8a59-2ed54e144641",       //Store unid
        "plazaExternalid": "",                                     //Store external id
        "plazaName": "name",                                    //Store name
        "countdate": "2018-01-01",                                 //date
        "counttimeLocal": "2018-01-01 10:00:00",                   //datetime
        "customerNum": 100,                                        //Total Customer IN
        "gender": {
             "maleCount": 100,                                     //Total Male Customer IN
             "femaleCount": 100                                    //Total Female Customer IN
        },
        "age": {
            "juvenile": [100, 200],                                // age < 18 [male,female]
            "youth": [100, 200],                                   // 18 <= age < 45 [male,female]
            "middleAged": [100, 200],                              // 45 <= age < 60 [male,female]
            "elderly": [100, 200]                                  // age >= 60 [male,female]
        },
        "modifyTime": "2022-01-01 14:00:10"
    }
    ... ...
    ]
}
```

## 6. Store DwellTime
You can get Store DwellTime through this interface.

>The DwellTime will generate next day(T+1).
> For exmaple: `Today's` DwellTime data will generate `TOMORROW`.

 | ``Verb``: GET  
 | ``Path``: api/v2/reid/mallDwellTime
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plazaUnid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- countdate: date ，Example：2018-01-01
 | Response Body:
```
{
    "code": 200,
    "success": true,
    "message": "success",
    "data": [
        {
            "plazaUnid": "123123",                         // Store unid
            "plazaName": "store name",                     // Store name
            "countdate": "2018-01-01",                     // date
            "totalDewellTime": 295449,                     // The Store totaldwellTime(second)
            "dwellTime": [
                {
                    "dwellNum": 46,                       // The Customer who's dewellTime in dwellTimeGroup
                    "dwellTimeGroup": "0-15"              // The dweelTimeGroup 0-15(minute)
                },
                {
                    "dwellNum": 17,
                    "dwellTimeGroup": "15-30"
                },
                {
                    "dwellNum": 9,
                    "dwellTimeGroup": "31-45"
                },
                {
                    "dwellNum": 10,
                    "dwellTimeGroup": "46-60"
                },
                {
                    "dwellNum": 9,
                    "dwellTimeGroup": "61-90"
                },
                {
                    "dwellNum": 16,
                    "dwellTimeGroup": "91+"
                }
            ]
        }
    ]
}
```

## 7. Store DwellTime (Every Customer)
You can get Store DwellTime of `every customer` that recognised through this interface.

 | ``Verb``: GET  
 | ``Path``: api/v1/residence/plazaResidence
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plaza_unid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- countdate: date ，Example：2018-01-01
 | Response Body:

```
{
		msg_code: 200,
		msg_info: "success",
		data: [
        {
			plaza_unid: "d03ab9dc-9e78-11eb-a328-0017fa03adf3",  // unid of store，Global unique identifier of store information
			plaza_externalid:"1001001001",                      //The external code of the store is generally used to keep consistent with other system codes when interfacing with other systems.
			person_unid："98a0da78-9fcf-4126-b10f-93ed4c0d2cec", //unid of person(customer&staff)
			plaza_name: "store name",     //name of store
			intime: "2021-05-31 00:00:00",     //when entry store
			outtime: "2021-05-31 00:00:10",     //when exit store
			residence_time: "0",  //dwell time
			countdate: "2021-05-31"    //date
        },
		{
			plaza_unid: "d03ab9dc-9e78-11eb-a328-0017fa03adf3",  // unid of store，Global unique identifier of store information
			plaza_externalid:"1001001001",                      //The external code of the store is generally used to keep consistent with other system codes when interfacing with other systems.
			person_unid："98a0da78-9fcf-4126-b10f-93ed4c0d2cec", //unid of person(customer&staff)
			plaza_name: "store name",     //name of store
			intime: "2021-05-31 00:00:00",     //when entry store
			outtime: "2021-05-31 00:00:10",     //when exit store
			residence_time: "0",  //dwell time
			countdate: "2021-05-31"    //date
        }
  	]
	}
```

## 8. Store-Entrance Counting Data Hourly
You can get all the  Store-Entrance counting data from this interface.

> The params startTime and endTime must be in one day
> And if you want more data in serval days,you should call this interface more times.

| ``Verb``: GET
| ``Path``: api/v1/passenger/gateHour
| ``Header``: (authorization, {$atoken})
| Request Params: 

	- plaza_unid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- gate_unid: unid of entrance. Example: aaaaaa-bbbb-cccc-dddd-assassaas
	- startTime: start time of the data you need 。Example：："2019-01-01 10:00:00"
	- endTime:  end time of the data you need 。Example："2019-01-01 22:00:00"

| Response Body:

```
{
    msg_code: 200,
    msg_info: "success",
    data: [{
        plaza_unid: "83c2266f-a29b-478a-8a59-2ed54e144641",  // unid of store
        gate_unid: "12c2266f-a29b-478a-8a59-2ed54e176533",   // unid of store-entrance
        countdate: "2018-01-01",                             // date
        counttime: "2018-01-01 10:00:00",                    // datetime
        innum: 19,                                           // Total Traffic IN
        outnum: 20,                                          // Total Traffic OUT
        outside_innum: 50,                                   // Traffic outside
        outside_outnum: 40,                                  // Traffic outside
        customer: 16,                                        // Total Customer IN
        customer_repeat: 1,                                  // Total Customer Repeats IN
        customer_out: 18                                     // Total Customer OUT
        customer_out_repeat: 1,                              // Total Customer Repeats OUT
        staff: 2,                                            // Total Staff IN
        staff_out: 1                                         // Total Staff OUT
    },
    {
        plaza_unid: "83c2266f-a29b-478a-8a59-2ed54e144641",
        gate_unid: "12c2266f-a29b-478a-8a59-2ed54e176533",
        countdate: "2018-01-01",
        counttime: "2018-01-01 10:00:00",
        innum: 26,
        outnum: 28,
        outside_innum: 50,
        outside_outnum: 40,
        customer: 20,
        customer_repeat: 4,
        customer_out: 19,
        customer_out_repeat: 7,
        staff: 2,
        staff_out: 2
    }]
}
```
## 9. Store-Entrance Hourly Customer Segment Data
You can get all the Store-Entrance Hourly Customer data from this interface.

> The params startTime and endTime must be in one day
> And if you want more data in serval days,you should call this interface more times.

| ``Verb``: GET
| ``Path``: api/v1/face/gateHour
| ``Header``: (authorization, {$atoken})
| Request Params: 

	- plaza_unid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- gate_unid: unid of entrance. Example: aaaaaa-bbbb-cccc-dddd-assassaas
	- startTime: start time of the data you need 。Example：："2019-01-01 10:00:00"
	- endTime:  end time of the data you need 。Example："2019-01-01 22:00:00"

| Response Body:
```
{
    msg_code: 200,
    msg_info: "success",
    data: [
    {
        plaza_unid: "123123",   // unid of store
        gate_unid:"456456",       // unid of store-entrance
        countdate: "2019-01-01",     // date
        counttime:"2019-01-01 10:00:00", // datetime
        totalnum: 11,                            // total(customer & staff) number with repeat
        totalcount: 9,                           // total(customer & staff) number without repeat
        customerMantime: 9,                      // customer number with repeat
        customer: 8,                             // customer number without repeat
        maleCount: 1,                            // male customer without repeat
        femalCount: 7,                           // female customer without repeat
        maleMantime: 1,                          // male customer with repeat
        femaleMantime: 8,                        // female customer with repeat
        staffMantime: 2,                         // staff with repeat
        staffCount: 1,                           // staff without repeat
        male_stage:"0,0,0,0,0,0,0,0,12,1,2,3,2,4,0,0,1，·······",  // male age detail, first is age 0, last is age 100
        female_stage:"0,0,0,0,0,0,0,0,12,1,2,3,2,4,0,0,1，·······", // female age detail, first is age0, last is age 100
    }
}
```

## 10. Capture record

 | ``Verb``: GET  
 | ``Path``: api/v2/captureRecord
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plazaUnid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- countdate: date ，Example：2018-01-01
  -
 | Response Body:

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
         {
                "unid": "12c2266f-a29b-478a-8a59-2ed54e176533",              //unid
                "personUnid": "12c2266f-a29b-478a-8a59-2ed54e176533",    //personUnid
                "gateUnid": "aaaabbbb-cccc-ddd",        // unid of gate
                "plazaUnid": "dddeeeee-cccc-ddd",        // unid of store
                "age": 27,                            
                "gender": 1,                            //  1：male 0：female -1：unknow
                "direction": 1,                            // 1：in -1：out
                "counttimeLocal": "2022-12-31 01:00:00",        // time
                "countdate": "2022-12-31"        // date
            },
          {
                "unid": "12c2266f-a29b-478a-8a59-2ed54e176533",
                "personUnid": "12c2266f-a29b-478a-8a59-2ed54e176533",
                "gateUnid": "aaaabbbb-cccc-ddd",
                "plazaUnid": "dddeeeee-cccc-ddd",
                "age": 27,
                "gender": 1,
                "direction": 1,
                "counttimeLocal": "2022-12-31 01:00:00",
                "countdate": "2022-12-31"
            }
  ]
}
```

## 11. In-store area data

 | ``Verb``: GET  
 | ``Path``: api/v2/zoneStat
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plazaUnid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- countdate: date ，Example：2018-01-01
  -
 | Response Body:

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
          {
                "zoneUnid": "12c2266f-a29b-478a-8a59-2ed54e176533",              //unid of zone
                "zoneName": "zonename 2",                                //name of zone
                "personMantime": 62,                       //traffic passenger
                "personCount": 40,                        //visitors
                "stopPersonCount": 27,                            // long dwell visitors
                "totalResidenceTime": 1040,                //total dwell time (seconds)           
                "avgResidenceTime": 26                     //average dwell time (seconds)       
          },
          {
                "zoneUnid": "12c2266f-a29b-478a-8a59-xxxxxxxxx",
                "zoneName": "zonename 2",
                "personMantime": 62,
                "personCount": 40,
                "stopPersonCount": 27,
                "totalResidenceTime": 1040,
                "avgResidenceTime": 26
         }
  ]
}
```

## 12. Store Daily Customer Segment Data

 | ``Verb``: GET
 | ``Path``: api/v2/passenger/plazaDay
 | ``Header``: (authorization, {$atoken})
 | Request Params:  
	- plazaUnid: unid of store。Example：8734758a-e0b0-11e8-b6e8-7cd30ac4c9a6
	- startDate: date ，Example：2018-01-01
	- endDate: date ，Example：2018-01-01
 | Response Body:

```json
{
  "code": 200,
  "msg": "",
  "success": true,
  "data": [
    {
      "plazaUnid": "83c2266f-a29b-478a-8a59-2ed54e144641", //unid of store
      "plazaExternalid": "1001001001", // external id of store
      "plazaName": "testName", // name of store
      "countdate": "2018-01-01", //date
      "innum": 100, //total traffic IN
      "outnum": 100, //total traffic OUT
      "outsideNum": 2000, // total traffic outside
      "customerNum": 12313, //total customer IN
      "staffCount": 1000, // total staff IN
      "deepShoppingNum": 50, // long dwell visitors
      "deepShoppingRate": 5.4, // long dwell rate
      "residenceTimeSecond": 120, // sum of residence time
      "groupName": "test", // name of group
      "modifyTime": "2022-01-01 14:00:10", //data update time
    }
    // ... ...
  ]
}
```
## 13.Entrance Daily Demographics Data (V2)
> Can support two time parameters to obtain entrance daily data.
1. Get data within a period of time based on startDate and endDate. Based on interface performance considerations, cross-day data query is not supported for the time being.
2. Obtain data updated after a certain point in time based on modifyTime. The data date is within three days and has been updated.


**Method**：``GET``  
**Path**：``/api/v2/reid/gateDay``  
**Header**：``{Authorization：{atoken}}``
**Request**：
>Note:When querying data for a certain time period, you only need to pass the parameters startDate and endDate. Start time and end time must be on the same day.
When querying data after the data update time, you only need to pass the parameter modifyTime. modifyTime only supports queries for data updated within three days. Data three days ago needs to be obtained using startDate and endDate.

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |
| gateUnid| string | NO     |  | entrance unique code, if no this field will return all entrance   |
| startDate | string | NO       |2022-12-31  | start date |
| endDate    | string | NO       |2022-12-31  | end date |
| modifyTime | string | NO       |2022-12-31 10:00:00| last modify time |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
        "plazaUnid": "83c2266f-a29b-478a-8a59-2ed54e144641",      //mall unique code
        "gateUnid":"5632266f-a29b-478a-8a59-2ed54e13256",         //entrance unique code
        "gateExternalid":"1001001001",                           //entrance external code
        "countdate": "2018-01-01",                                 //date
        "customerNum": 100,                                      //unique visitors
        "gender": {
             "maleCount": 100,                                         //male visitors
             "femalCount": 100                                         //female visitors
        },
        "age": {
            "juvenile": [100, 200],                                    // juvenile(to 18) [male,female]
            "youth": [100, 200],                                       // youth(19-45) [male,female]
            "middleAged": [100, 200],                                  // middleAged(46-60) [male,female]
            "elderly": [100, 200]                                      // elderly(60 above) [male,female]
        },
        "modifyTime": "2022-01-01 14:00:10"                           //last modify time
    }
    ... ...
    ]
}
```

## 14.Entrance Hourly Demographics Data (V2)
> Can support two time parameters to obtain entrance hourly data.
1. Get data within a period of time based on startTime and endTime. Based on interface performance considerations, cross-day data query is not supported for the time being.
2. Obtain data updated after a certain point in time based on modifyTime. The data date is within three days and has been updated.


**Method**：``GET``  
**Path**：``/api/v2/reid/gateHour``  
**Header**：``{Authorization：{atoken}}``
**Request**：
>Note:When querying data for a certain time period, you only need to pass the parameters startTime and endTime. Start time and end time must be on the same day.
When querying data after the data update time, you only need to pass the parameter modifyTime. modifyTime only supports queries for data updated within three days. Data from three days ago needs to be obtained using startTime and endTime.

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |
| gateUnid| string | NO     |  | entrance unique code, if no this field will return all entrance   |
| startTime | string | NO       |2022-12-31 10:00:00 | start time |
| endTime    | string | NO       |2022-12-31 22:00:00 | end time |
| modifyTime | string | NO       |2022-12-31 10:00:00| last modify time |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
        "plazaUnid": "83c2266f-a29b-478a-8a59-2ed54e144641",      //mall unique code
        "gateUnid":"5632266f-a29b-478a-8a59-2ed54e13256",         //entrance unique code
        "gateExternalid":"1001001001",                           //entrance external code
        "countdate": "2018-01-01",                                 //date
        "counttimeLocal": "2018-01-01 18:00:00",                   //local time
        "customerNum": 100,                                      //unique visitors
        "gender": {
             "maleCount": 100,                                         //male visitors
             "femalCount": 100                                         //female visitors
        },
        "age": {
            "juvenile": [100, 200],                                    // juvenile(to 18) [male,female]
            "youth": [100, 200],                                       // youth(19-45) [male,female]
            "middleAged": [100, 200],                                  // middleAged(46-60) [male,female]
            "elderly": [100, 200]                                      // elderly(60 above) [male,female]
        },
        "modifyTime": "2022-01-01 14:00:10"                           //last modify time
    }
    ... ...
    ]
}
```

## 15.Heatmap
> Store Heatmap Data

**Method**：``GET``  
**Path**：``/api/v2/heatMap``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid   | string | Yes       |            | Unique store code  |
| countdate   | string | Yes       | yyyy-MM-dd | Statistical date |
| personType | array | No | 0,1,-99 | type：visitor: 0; staff:1; unknown: -99 |
| genders | array | No | 1,0 | gender：male 1 female 0 |
| ages | array | No | 0-18,19-35,36-55,56-100 | Age groups：0-18,19-35,36-55,56-100 |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
      "imgUrl": "http://xxxx.com/a.img", //layout
      "heat": [
          {
                "residenceTimeTotal": 48.2,        // total dwell time，unit:seconds
                "rx": 50.4,        // x,y coordinate
                "ry": 41.4
            },
          {
                "residenceTimeTotal": 15.36,
                "rx": 50.4,
                "ry": 41.2
            }
      ]
    }
  ]
}
```

## 16.Entrance Visitor Flow
> Visitor flow between entrances

**Method**：``GET``  
**Path**：``/api/v2/gateFlowDirection``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |
| countdate| string | YES     |2022-12-31  | Date  |

**Response**：

```json
{
    "code": 200,
    "success": true,
    "message": "success",
    "data": [
        {
            "source": "a",        // entrance name
            "target": "b",        // entrance name
            "value": 1            // counts
        },
        {
            "source": "a",
            "target": "c",
            "value": 2
        },
        {
            "source": "b",
            "target": "c",
            "value": 4
        },
        {
            "source": "c",
            "target": "a",
            "value": 3
        }
    ]
}

```

## 17.Store zone data

**Method**：``GET``  
**Path**：``/api/v2/zoneStat``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |
| countdate| string | YES     |2022-12-31  | Date  |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
        "zoneUnid": "12c2266f-a29b-478a-8a59-2ed54e176533",              //Unique zone code
        "zoneName": "test1",                                //zone name
        "personMantime": 62,                            // counts
        "customerMantime": 50,                            // traffic counts
        "personCount": 40,                            // visitor counts
        "staffMantime": 33,                            // staff counts
        "stopPersonCount": 27,                            // longdwell visitor counts
        "totalResidenceTime": 1040,                            // total dwell time
        "avgResidenceTime": 26,                            // average dwell time
        "age": {
          "juvenile": [1, 0],                    // juvenile,male/female
          "youth": [9, 6],                    // youth, male/female
          "middleAged": [0, 1],                // middleAged,male/female
          "elderly": [0, 1]                    // elderly,male/female
         },
         "gender": {
           "maleCount": 10,                    //male counts
           "femaleCount": 8                    //female counts
        }
    },
    {
        "zoneUnid": "12c2266f-a29b-478a-8a59-xxxxxxxxx",
        "zoneName": "testing2",
        "personMantime": 62,
        "personCount": 40,
        "stopPersonCount": 27,
        "totalResidenceTime": 1040,
        "avgResidenceTime": 26,
        "age": {
          "juvenile": [1, 0],
          "youth": [9, 6],
          "middleAged": [0, 1],
          "elderly": [0, 1]
        },
        "gender": {
          "maleCount": 10,
          "femaleCount": 8
       }
    }
    ]
}
```

## 18.Zone info

**Method**：``GET``  
**Path**：``/api/v2/base/zoneInfo``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
        {
            "plazaUnid": "d7c14e06-fc14-11eb-84f5-00e0533102b4", //mall unique code
            "zoneUnid": "72b3e6ce-04c8-11ec-86bf-00e0533102b4",  //Unique zone code
            "zoneName": "test",                             //zone name
            "zoneExternalid": "",                                //zone external code
            "zoneStatus": 1                                      //zone status：1-activate，2-deactivate
            "channel": [
                {
                    "rareaInfo": "coordinate json"
                }
            ]
        },
        ...
    ]
}
```

## 19.Store zone hourly data

**Method**：``GET``  
**Path**：``/api/v2/zoneHourStat``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |
| countdate| string | YES     |2022-12-31  | Date  |

**Response**：

```json
{
    "code": 200,
    "msg": "",
    "success": true,
    "data": [
    {
        "zoneUnid": "12c2266f-a29b-478a-8a59-2ed54e176533",              //Unique zone code
        "zoneName": "test1",                                //zone name
        "counttimeLocal": "2025-01-23 22:00:00",          // datetime
        "personMantime": 62,                            // counts
        "personMantimeOut": 62,                            // counts out
        "customerMantime": 50,                            // traffic counts
        "customerMantimeOut": 50,                            // traffic counts out
        "personCount": 40,                            // visitor counts
        "personCountOut": 40,                            // visitor counts out
        "staffMantime": 33,                            // staff counts
        "staffMantimeOut": 33,                            // staff counts out
        "age": {
          "juvenile": [1, 0],                    // juvenile,male/female
          "youth": [9, 6],                    // youth, male/female
          "middleAged": [0, 1],                // middleAged,male/female
          "elderly": [0, 1]                    // elderly,male/female
         },
         "gender": {
           "maleCount": 10,                    //male counts
           "femaleCount": 8                    //female counts
        }
    }
	...
    ]
}
```

## 20.Device Info

**Method**：``GET``  
**Path**：``/api/v1/base/device``  
**Header**：``{Authorization：{atoken}}``
**Request**：

| Field      | Type   | Necessary | Demo       | Remark    |
| --------- | ------ | -------- | ---------- | ------- |
| plazaUnid| string | YES       |  | mall unique code  |

**Response**：

```json
{
    "msg_code": 200,
    "msg_info": "this is info"
    "data": [
        {
            "serialnum": "1FC9-FAB4-712C-7053",             //serialnum
            "name": "192.168.5.134",                        //name
            "channel_count": 1,                             //Number of device channels
            "mac": "00-10-ff-12-43-12",                     //mac
            "status": 1,                                    //status：0-offline，1-online，3-disable
            "local_ip": "192.168.2.123",                    //ip
            "modify_time": "2018-01-01 00:00:00"            //modify time
        },
        ...
    ]
}
```
