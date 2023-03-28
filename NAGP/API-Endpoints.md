## **API Endpoints:**

> ### 1. Eureka Server:

        - http://localhost:8761

> ### 2. Gateway:

        - http://localhost:9999

> ### 3. Login:

1. For SignUp:

   - URL [POST]- http://localhost:9999/user/signup
   - Request Body: User
   - Example:

   1. **Request:**
      {
      "name":"Kitika Singh",
      "email":"kritikasingh6421@gmail.com",
      "password":"12345678"
      }
      **Response:**
      kritikasingh6421@gmail.com sign Up successful.

   2. **Request:** - with same email Id:
      {
      "name":"Ritika Singh",
      "email":"kritikasingh6421@gmail.com",
      "password":"12345678"
      }
      **Response:**
      Sign Up fail.

2. For Token Generation:

   - URL [POST]- http://localhost:8088/user/token
   - Resquest Body- AuthRequest-
     {
     "email":"kritikasingh6421@gmail.com",
     "password":"12345678"
     }
   - Example:

   1. **Request:**
      -url: hhttp://localhost:8088/user/token
      {
      "email":"kritikasingh6421@gmail.com",
      "password":"12345678"
      }
      **Response:**
      eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJrcml0aWthc2luZ2g2NDIxQGdtYWlsLmNvbSIsImlhdCI6MTY3OTk3ODE4NSwiZXhwIjoxNjc5OTc5OTg1fQ.wCtsMTj-x28gcP5ZsTP2sIv2EEudqE8FwZSI-fpJCLM

   2. **Request:**- With wrong password:
      -url: http://localhost:9999/user/login/kritikasingh6421@gmail.com/123456
      -{
      "email":"kritikasingh6421@gmail.com",
      "password":"123456"
      }
      **Response:**
      {
      "timestamp": "2023-03-28T04:02:26.576+00:00",
      "status": 403,
      "error": "Forbidden",
      "path": "/user/token"
      }

3. For Token Validation:
   - URL [GET]- http://localhost:9999/user/validate?token={tokenValue}
   - Example:
   1. **Request:**
      -url: http://localhost:9999/user/validate?token=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJrcml0aWthc2luZ2g2NDIxQGdtYWlsLmNvbSIsImlhdCI6MTY3OTk3ODE4NSwiZXhwIjoxNjc5OTc5OTg1fQ.wCtsMTj-x28gcP5ZsTP2sIv2EEudqE8FwZSI-fpJCLM
      **Response:**
      Valid Token
   2. **Request:** {With invalid token}
      -url: http://localhost:9999/user/validate?token=fkse54ciOiJIUzI1NiJ9.eyJzdWIiOiJrcml0aWthc2luZ2g2NDIxQGdtYWlsLmNvbSIsImlhdCI6MTY3OTk3ODE4NSwiZXhwIjoxNjc5OTc5OTg1fQ.wCtsMTj-x28gcP5ZsTP2sIv2EEue45tFwZSI-fpJCLM
      **Response:**
      Invalid Token

> ### 4. Booking:

1.{
"order":{},
"payment":{},
"flight":{
"flightId": 1,
"serviceProviderName": "IndiGo",
"flightName": "IndiGo_123",
"departureLocation": "Lucknow",
"departureDate": "2023-03-23",
"departureTime": "06:35:00",
"arrivalLocation": "New Delhi",
"arrivalDate": "2023-03-23",
"arrivalTime": "13:20:00",
"flightClass": "economy",
"availability": 3,
"price": 2506
},
"noOfSeatBook":2
}

response:
{
"order": {
"orderId": 3,
"productId": 1,
"serviceProviderName": "IndiGo",
"orderDetails": "Flight Details:ONE WAY TRIP with flight: IndiGo_123",
"totalAmount": 2506,
"orderDate": "2023-03-24",
"orderTime": "15:02:06.3318641",
"orderStatus": "order successful"
},
"payment": {
"paymentId": 3,
"transactionId": "73f3c547-8db8-4064-81be-cd1ee7185952",
"orderId": 3,
"totalAmount": 2506,
"paymentDate": "2023-03-24",
"paymentTime": "15:02:06.3570852",
"paymentStatus": "Successful"
},
"flight": {
"flightId": 1,
"serviceProviderName": "IndiGo",
"flightName": "IndiGo_123",
"departureLocation": "Lucknow",
"departureDate": "2023-03-23",
"departureTime": "06:35:00",
"arrivalLocation": "New Delhi",
"arrivalDate": "2023-03-23",
"arrivalTime": "13:20:00",
"flightClass": "economy",
"availability": 1,
"price": 2506
},
"noOfSeatBook": 2
}

> ### 5. FlightSearch:

1.  For all flight:
    URL- [GET] http://localhost:9999/flight/

    1. **Request-** - Url -http://localhost:9999/flight/
       **Response-**
       [
       {
       "flightId": 1,
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_123",
       "departureLocation": "Lucknow",
       "departureDate": "2023-03-23",
       "departureTime": "06:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-23",
       "arrivalTime": "13:20:00",
       "flightClass": "economy",
       "availability": 3,
       "price": 2506
       },
       {
       "flightId": 2,
       "serviceProviderName": "Air India",
       "flightName": "AirIndia_423",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "departureTime": "08:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-25",
       "arrivalTime": "13:20:00",
       "flightClass": "business",
       "availability": 3,
       "price": 5500
       },
       {
       "flightId": 3,
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_333",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "departureTime": "08:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-25",
       "arrivalTime": "13:20:00",
       "flightClass": "business",
       "availability": 6,
       "price": 2506
       }
       ]

2.  For flight with id:
    URL- [GET] http://localhost:9999/flight/{id}

    1. **Request-**
       - url:http://localhost:9999/flight/1
         **Response-**
         {
         "flightId": 1,
         "serviceProviderName": "IndiGo",
         "flightName": "IndiGo_123",
         "departureLocation": "Lucknow",
         "departureDate": "2023-03-23",
         "departureTime": "06:35:00",
         "arrivalLocation": "New Delhi",
         "arrivalDate": "2023-03-23",
         "arrivalTime": "13:20:00",
         "flightClass": "economy",
         "availability": 3,
         "price": 2506
         }

3.  For flight search with {Departure Location, Arrival Location, Flight Class, Date}:
    URL- [GET] http://localhost:9999/flight/findWith?departureLocation={value}&arrivalLocation={value}&flightClass={value}&date={value}

    1. **Request-**

       - url- http://localhost:9999/flight/findWith?departureLocation=Lucknow&arrivalLocation=New Delhi&flightClass=economy&date=2023-03-23

       **Response-**[
       {
       "flightId": 1,
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_123",
       "departureLocation": "Lucknow",
       "departureDate": "2023-03-23",
       "departureTime": "06:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-23",
       "arrivalTime": "13:20:00",
       "flightClass": "economy",
       "availability": 3,
       "price": 2506
       }
       ]

4.  For adding flight:
    URL- [POST] http://localhost:9999/flight/
    Response Body- flight object

    Example:

    1. **Request-**{
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_123",
       "departureLocation": "Lucknow",
       "departureDate": "2023-03-23",
       "departureTime": "06:35",
       "arrivalLocation":"New Delhi",
       "arrivalDate":"2023-03-23",
       "arrivalTime":"13:20",
       "flightClass":"economy",
       "availability": 3,
       "price": 2506
       }
       **Response-**
       {
       "flightId": 1,
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_123",
       "departureLocation": "Lucknow",
       "departureDate": "2023-03-23",
       "departureTime": "06:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-23",
       "arrivalTime": "13:20:00",
       "flightClass": "economy",
       "availability": 3,
       "price": 2506
       }
    2. **Request-**
       {
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_423",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "departureTime": "08:35",
       "arrivalLocation":"New Delhi",
       "arrivalDate":"2023-03-25",
       "arrivalTime":"13:20",
       "flightClass":"business",
       "availability": 3,
       "price": 2506
       }
       **Response-**
       {
       "flightId": 2,
       "serviceProviderName": "IndiGo",
       "flightName": "IndiGo_423",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "departureTime": "08:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-25",
       "arrivalTime": "13:20:00",
       "flightClass": "business",
       "availability": 3,
       "price": 2506
       }

5.  For updating flight:
    URL- [PUT] http://localhost:9999/flight/{id}
    Response Body- flight object

    Example- 1.**Request-**

    - Url-http://localhost:9999/flight/2
    - {
      "flightId": 2,
      "serviceProviderName": "Air India",
      "flightName": "AirIndia_423",
      "departureLocation": "Prayagraj",
      "departureDate": "2023-03-25",
      "departureTime": "08:35",
      "arrivalLocation":"New Delhi",
      "arrivalDate":"2023-03-25",
      "arrivalTime":"13:20",
      "flightClass":"business",
      "availability": 3,
      "price": 5500
      }
      **Response-**
      {
      "flightId": 2,
      "serviceProviderName": "Air India",
      "flightName": "AirIndia_423",
      "departureLocation": "Prayagraj",
      "departureDate": "2023-03-25",
      "departureTime": "08:35:00",
      "arrivalLocation": "New Delhi",
      "arrivalDate": "2023-03-25",
      "arrivalTime": "13:20:00",
      "flightClass": "business",
      "availability": 3,
      "price": 5500
      }

6.  For deleting flight:

    - URL: [DELETE] http://localhost:9999/flight/{id}
    - Example:

    1. **Request-**
       url: http://localhost:9999/flight/3
       **Response-**
       HttpStatus- 200 Ok

7.  For Adding Service Provider:

    - URL [POST] http://localhost:9999/flight/serviceProvider
    - Request Body- Service Provider
    - Example: 1. **Request-**
      {
      "serviceProviderName": "Air India",
      "serviceProviderEmail": "airindia.com",
      "serviceProviderNumber": "123456789"
      }
      **Response-**
      {
      "serviceProviderId": 1,
      "serviceProviderName": "Air India",
      "serviceProviderEmail": "airindia.com",
      "serviceProviderNumber": 123456789
      }

8.  For Finding Service Provider Details:

    - URL [Get] http://localhost:9999/flight/serviceProvider/{service-provider-name}

    - Example:
      1. **Request-**
         -url: http://localhost:9999/flight/serviceProvider/IndiGo
         **Response-**
         {
         "serviceProviderId": 2,
         "serviceProviderName": "IndiGo",
         "serviceProviderEmail": "indigo.com",
         "serviceProviderNumber": 123456789
         }

9.  For booking one way flight:

    - URL [POST] http://localhost:9999/flight/bookingOneWayFlight
    - Request Body- BookingForOneWayFlight {
      "customerEmail": "",
      "order":{},
      "payment":{},
      "flight": {
      "flightId": ,
      "flightName": "",
      "departureLocation": "",
      "departureDate": "",
      "arrivalLocation": "",
      "arrivalDate": "",
      "flightClass": ""
      }
      "numberOfSeatBook":1
      }
    - Example:

    1. **Request-**
       {
       "customerEmail": "kritikasingh6421@gmail.com",
       "order":{},
       "payment":{},
       "flight":{
       "flightId": 2,
       "flightName": "AirIndia_423",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-25",
       "flightClass": "business"
       }
       "numberOfSeatBook":1
       }
       **Response-**
       {
       "customerEmail": "kritikasingh6421@gmail.com",
       "order": {
       "orderId": 1,
       "productId": 2,
       "serviceProviderName": "Air India",
       "customerEmail": "kritikasingh6421@gmail.com",
       "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
       "totalAmount": 5500.0,
       "orderDate": "2023-03-28",
       "orderTime": "16:08:43.6651361",
       "orderStatus": "order successful",
       "tripType": "ONE WAY TRIP",
       "noOfSeatBook": 1
       },
       "payment": {
       "paymentId": 3,
       "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
       "orderId": 1,
       "customerEmail": "kritikasingh6421@gmail.com",
       "totalAmount": 5500.0,
       "paymentDate": "2023-03-28",
       "paymentTime": "16:08:43.7203175",
       "paymentStatus": "Successful"
       },
       "flight": {
       "flightId": 2,
       "serviceProviderName": "Air India",
       "flightName": "AirIndia_423",
       "departureLocation": "Prayagraj",
       "departureDate": "2023-03-25",
       "departureTime": "08:35:00",
       "arrivalLocation": "New Delhi",
       "arrivalDate": "2023-03-25",
       "arrivalTime": "13:20:00",
       "flightClass": "business",
       "availability": 2,
       "price": 5500.0
       },
       "numberOfSeatBook": 1

    }

10. **Request-** when user sepecification did not match
    {
    "customerEmail": "kritikasingh6421@gmail.com",
    "order":{},
    "payment":{},
    "flight":{
    "flightId": 2,
    "flightName": "AirIndia_423",
    "departureLocation": "Prayagraj",
    "departureDate": "2023-03-25",
    "arrivalLocation": "New Delhi",
    "arrivalDate": "2023-03-25",
    "flightClass": "economy"
    },
    "numberOfSeatBook":1

    }

    **Response-**
    Bad Request Http status- 400

11. For cancel one way flight:

    - URL [POST] http://localhost:9999/flight/cancelOneWayFlight
    - Request Body- Order
    - Example:

    1. **Request-**
       {
       "orderId": 1,
       "productId": 2,
       "serviceProviderName": "Air India",
       "customerEmail": "kritikasingh6421@gmail.com",
       "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
       "totalAmount": 5500.0,
       "orderDate": "2023-03-28",
       "orderTime": "16:08:43.6651361",
       "orderStatus": "order successful",
       "tripType": "ONE WAY TRIP",
       "noOfSeatBook": 1
       }
       **Response-**
       {
       "orderId": 1,
       "productId": 2,
       "serviceProviderName": "Air India",
       "customerEmail": "kritikasingh6421@gmail.com",
       "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
       "totalAmount": 5500.0,
       "orderDate": "2023-03-28",
       "orderTime": "16:08:43.6651361",
       "orderStatus": "order cancel",
       "tripType": "ONE WAY TRIP",
       "noOfSeatBook": 1

    }

12. For booking two way flight:

- URL [POST] http://localhost:9999/flight/bookingTwoWayFlight
- Request Body- BookingTwoWayFlight

{
"order": {},
"payment" :{},
"flight1":{},
"flight2":{},
"noOfSeatBook": ,
"customerEmail":""
}

- Example: 1. **Request-**
  {
  "order": {},
  "payment" :{},
  "flight1":{
  "flightId": 2,
  "flightName": "AirIndia_423",
  "departureLocation": "Prayagraj",
  "departureDate": "2023-03-25",
  "arrivalLocation": "New Delhi",
  "arrivalDate": "2023-03-25",
  "flightClass": "business"
  },
  "flight2":{
  "flightId": 4,
  "flightName": "IndiGo_333",
  "departureLocation": "New Delhi",
  "departureDate": "2023-03-26",
  "arrivalLocation": "Prayagraj",
  "arrivalDate": "2023-03-27",
  "flightClass": "business"
  },
  "noOfSeatBook": 1,
  "customerEmail":"kritikasingh6421@gmail.com"
  }
  **Response-**

  {
  "order": {
  "orderId": 4,
  "product1Id": 2,
  "product2Id": 4,
  "serviceProviderName1": "Air India",
  "serviceProviderName2": "IndiGo",
  "customerEmail": "kritikasingh6421@gmail.com",
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "totalAmount": 8006.0,
  "orderDate": "2023-03-28",
  "orderTime": "16:38:14.4986568",
  "orderStatus": "order successful",
  "tripType": "TWO WAY TRIP",
  "noOfSeatBook": 1
  },
  "payment": {
  "paymentId": 4,
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 8006.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:38:14.6683601",
  "paymentStatus": "Successful"
  },
  "flight1": {
  "flightId": 2,
  "serviceProviderName": "Air India",
  "flightName": "AirIndia_423",
  "departureLocation": "Prayagraj",
  "departureDate": "2023-03-25",
  "departureTime": "08:35:00",
  "arrivalLocation": "New Delhi",
  "arrivalDate": "2023-03-25",
  "arrivalTime": "13:20:00",
  "flightClass": "business",
  "availability": 2,
  "price": 5500.0
  },
  "flight2": {
  "flightId": 4,
  "serviceProviderName": "IndiGo",
  "flightName": "IndiGo_333",
  "departureLocation": "New Delhi",
  "departureDate": "2023-03-26",
  "departureTime": "08:35:00",
  "arrivalLocation": "Prayagraj",
  "arrivalDate": "2023-03-27",
  "arrivalTime": "13:20:00",
  "flightClass": "business",
  "availability": 5,
  "price": 2506.0
  },
  "noOfSeatBook": 1,
  "customerEmail": "kritikasingh6421@gmail.com"
  }

13. For cancel one way flight:

- URL [POST] http://localhost:9999/flight/cancelTwoWayFlight
- Request Body- Order
- Example: 1. **Request-**
  {
  "orderId": 4,
  "product1Id": 2,
  "product2Id": 4,
  "serviceProviderName1": "Air India",
  "serviceProviderName2": "IndiGo",
  "customerEmail": "kritikasingh6421@gmail.com",
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "totalAmount": 8006.0,
  "orderDate": "2023-03-28",
  "orderTime": "16:38:14.4986568",
  "orderStatus": "order successful",
  "tripType": "TWO WAY TRIP",
  "noOfSeatBook": 1
  }
  **Response-**
  {
  "orderId": 4,
  "product1Id": 2,
  "product2Id": 4,
  "serviceProviderName1": "Air India",
  "serviceProviderName2": "IndiGo",
  "customerEmail": "kritikasingh6421@gmail.com",
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "totalAmount": 8006.0,
  "orderDate": "2023-03-28",
  "orderTime": "16:38:14.4986568",
  "orderStatus": "order cancel",
  "tripType": "TWO WAY TRIP",
  "noOfSeatBook": 1
  }

14. For All orders of one way trip by user:

- URL [GET] http://localhost:9999/flight/ordersForOneWayTrip/{email}
- Example:

1.  **Request-**
    url- http://localhost:9999/flight/ordersForOneWayTrip/kritikasingh6421@gmail.com
    **Response-**
    [
    {
    "orderId": 1,
    "productId": 2,
    "serviceProviderName": "Air India",
    "customerEmail": "kritikasingh6421@gmail.com",
    "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
    "totalAmount": 5500.0,
    "orderDate": "2023-03-28",
    "orderTime": "16:08:43",
    "orderStatus": "order cancel",
    "tripType": "ONE WAY TRIP",
    "noOfSeatBook": 1
    }
    ]

2.  For All orders of return trip by user:

- URL [GET] http://localhost:9999/flight/ordersForTwoWayTrip/{email}
  - Example:
  1.  **Request-**
      url: http://localhost:9999/flight/ordersForTwoWayTrip/kritikasingh6421@gmail.com
      **Response-**
      [
      {
      "orderId": 4,
      "product1Id": 2,
      "product2Id": 4,
      "serviceProviderName1": "Air India",
      "serviceProviderName2": "IndiGo",
      "customerEmail": "kritikasingh6421@gmail.com",
      "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
      "totalAmount": 8006.0,
      "orderDate": "2023-03-28",
      "orderTime": "16:38:14",
      "orderStatus": "order cancel",
      "tripType": "TWO WAY TRIP",
      "noOfSeatBook": 1
      }
      ]

> ### 6. HotelSearch:

1. For all Hotels:
   -URL [GET] http://localhost:9999/hotel/
   -Example:
   1. **Request-**
      url : http://localhost:9999/hotel
      **Response-**
      [
      {
      "hotelId": 1,
      "serviceProviderName": "Lemon Tree Hotels",
      "hotelName": "Lemon Tree Premier",
      "city": "Gurugram",
      "numberOfRoomsAvailable": 20,
      "price": 2500.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      },
      {
      "hotelId": 2,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      },
      {
      "hotelId": 4,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise 1",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-23",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
      ]
2. For Hotel Search with id:
   -URL [GET] http://localhost:9999/hotel/{id}
   -Example:

   1. **Request-**
      url : http://localhost:9999/hotel/1
      **Response-**
      {
      "hotelId": 1,
      "serviceProviderName": "Lemon Tree Hotels",
      "hotelName": "Lemon Tree Premier",
      "city": "Gurugram",
      "numberOfRoomsAvailable": 20,
      "price": 2500.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }

3. For Hotel Search with {name, city, check in date, check out date}:

   - URL: [GET] http://localhost:9999/hotel/findWith?name={value}&city={value}&checkInDate={value}&checkOutDate={value}
   - Example:

   1. **Request-**
      url: http://localhost:9999/hotel/findWith?name=Lemon Tree Premier&city=gurugram&checkInDate=2023-03-23&checkOutDate=2023-03-24
      **Response-**
      [
      {
      "hotelId": 1,
      "serviceProviderName": "Lemon Tree Hotels",
      "hotelName": "Lemon Tree Premier",
      "city": "Gurugram",
      "numberOfRoomsAvailable": 20,
      "price": 2500.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
      ]

4. For wishlised Hotels:

   - URL [GET] http://localhost:9999/hotel/wishlist
   - Example:

   1. **Request-**
      url: http://localhost:9999/hotel/wishlist
      **Response-**
      [
      {
      "hotelId": 2,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": true,
      "booked": false
      }
      ]

5. For adding Hotel to wishlist:

   - URL [PUT] http://localhost:9999/hotel/addToWishList/{id}
   - Example:

   1. **Request-**
      url: http://localhost:9999/hotel/addToWishList/2
      **Response-**
      {
      "hotelId": 2,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": true,
      "booked": false
      }

6. For adding Hotel:  
    -URL [POST] http://localhost:9999/hotel/
   -Request Body- hotel object
   -Example:

   1. **Request-**
      Request Body:
      {
      "serviceProviderName": "Lemon Tree Hotels",
      "hotelName": "Lemon Tree Premier",
      "city": "Gurugram",
      "numberOfRoomsAvailable": 20,
      "price": 2500.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
      **Response-**
      {
      "hotelId": 1,
      "serviceProviderName": "Lemon Tree Hotels",
      "hotelName": "Lemon Tree Premier",
      "city": "Gurugram",
      "numberOfRoomsAvailable": 20,
      "price": 2500.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
   2. **Request-**
      Request Body:
      {
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
      **Response-**
      {
      "hotelId": 2,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }

7. For updateing Hotel:

   - URL [PUT] http://localhost:9999/hotel/{id}
   - Request Body- hotel object
   - Example:

   1. **Request-**
      url: http://localhost:9999/hotel/2
      Request Body:
      {
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }
      **Response-**
      {
      "hotelId": 2,
      "serviceProviderName": "Paradise Hotels",
      "hotelName": "Paradise",
      "city": "New Delhi",
      "numberOfRoomsAvailable": 2,
      "price": 5600.0,
      "checkInDate": "2023-03-23",
      "checkInTime": "13:00:00",
      "checkOutDate": "2023-03-24",
      "checkOutTime": "12:00:00",
      "wishlist": false,
      "booked": false
      }

8. For deleting Hotel:
   -URL [DELETE] http://localhost:9999/hotel/{id}
   -Example:

   1. **Request-**
      url : http://localhost:9999/hotel/4
      **Response-**
      -Successfully Deleted!!,HttpStatus.OK

9. Add Hotel Service Providers:

   - URL [POST] http://localhost:9999/hotel/serviceProvider
   - Request Body - Service provider object
   - Example:

   1. **Request-**  
       url: http://localhost:9999/hotel/serviceProvider
      Request body:
      {
      "serviceProviderName": "Lemon Tree Hotels",
      "serviceProviderEmail": "lemontreehotels.com",
      "serviceProviderNumber": 6456234567
      }
      **Response-**
      {
      "serviceProviderId": 1,
      "serviceProviderName": "Lemon Tree Hotels",
      "serviceProviderEmail": "lemontreehotels.com",
      "serviceProviderNumber": "6456234567"
      }
   2. **Request-**  
      url: http://localhost:9999/hotel/serviceProvider
      Request body:
      {
      "serviceProviderName": "Paradise Hotels",
      "serviceProviderEmail": "paradisehotes.com",
      "serviceProviderNumber": "123456789"
      }
      **Response-**
      {
      "serviceProviderId": 2,
      "serviceProviderName": "Paradise Hotels",
      "serviceProviderEmail": "paradisehotes.com",
      "serviceProviderNumber": "123456789"
      }

10. List of Servide Providers By Name:

- URL [GET] http://localhost:9999/hotel/serviceProvider/{name}
- Example:

  1.  **Request-** When Service provider name exists
      url: http://localhost:9999/hotel/serviceProvider/Paradise Hotels
      **Response-**
      {
      "serviceProviderId": 2,
      "serviceProviderName": "Paradise Hotels",
      "serviceProviderEmail": "paradisehotes.com",
      "serviceProviderNumber": "123456789"
      }
      2 .**Request-** When Service provider name does not exists
      url: http://localhost:9999/hotel/serviceProvider/Hello world
      **Response-**
      Status 500

11. Booking Hotel:

        - URL [POST] http://localhost:9999/hotel/booking
        - Request Body -
        - Example:

        1.  **Request-**
             url: http://localhost:9999/hotel/booking
            **Request body:**
            {
            "customerEmail": "kritikasingh6421@gmail.com",
            "hotel": {
            "hotelId": 2,
            "hotelName": "Paradise",
            "city": "New Delhi",
            "checkInDate": "2023-03-23"
            },
            "payment": {},
            "order": {},
            "numberOfRoomBook":2
            }
            **Response-**
            {
        "customerEmail": "kritikasingh6421@gmail.com",
        "hotel": {
            "hotelId": 2,
            "serviceProviderName": "Paradise Hotels",
            "hotelName": "Paradise",
            "city": "New Delhi",
            "numberOfRoomsAvailable": 0,
            "price": 5600.0,
            "checkInDate": "2023-03-23",
            "checkInTime": "13:00:00",
            "checkOutDate": "2023-03-24",
            "checkOutTime": "12:00:00",
            "wishlist": true,
            "booked": true
        },
        "payment": {
            "paymentId": 2,
            "transactionId": "0820ba83-f2d2-4f51-91de-a9147e5da5ba",
            "orderId": 4,
            "customerEmail": "kritikasingh6421@gmail.com",
            "totalAmount": 5600.0,
            "paymentDate": "2023-03-28",
            "paymentTime": "15:28:50.2961428",
            "paymentStatus": "Successful"
        },
        "order": {
            "orderId": 4,
            "productId": 2,
            "serviceProviderName": "Paradise Hotels",
            "customerEmail": "kritikasingh6421@gmail.com",
            "transactionId": "0820ba83-f2d2-4f51-91de-a9147e5da5ba",
            "totalAmount": 5600.0,
            "orderDate": "2023-03-28",
            "orderTime": "15:28:50.2132986",
            "orderStatus": "order successful",
            "numberOfRoomBook": 2
        },
        "numberOfRoomBook": 2

    }

    2. **Request-** When data not match with user input
       {
       "customerEmail": "kritikasingh6421@gmail.com",
       "hotel": {
       "hotelId": 2,
       "hotelName": "Paradise",
       "city": "Delhi",
       "checkInDate": "2023-03-23"
       },
       "payment": {},
       "order": {},
       "numberOfRoomBook":2
       }
       **Response-**
       Bad Request Http Status-400

12. Cancel Booking:
    -URL [POST] http://localhost:9999/hotel/bookingCancel
    -Request Body : Order
    -Example-

    1.  **Request-**

    - url: http://localhost:9999/hotel/bookingCancel
    - Request Body: {
      "orderId": 3,
      "productId": 2,
      "serviceProviderName": "Paradise Hotels",
      "customerEmail": "kritikasingh6421@gmail.com",
      "transactionId": "c59444e9-34a8-40d6-b523-af071a00447a",
      "totalAmount": 5600.0,
      "orderDate": "2023-03-27",
      "orderTime": "21:08:35.5593026",
      "orderStatus": "order successful",
      "numberOfRoomBook": 2
      }
      **Response-**
      {
      "orderId": 3,
      "productId": 2,
      "serviceProviderName": "Paradise Hotels",
      "customerEmail": "kritikasingh6421@gmail.com",
      "transactionId": "c59444e9-34a8-40d6-b523-af071a00447a",
      "totalAmount": 5600.0,
      "orderDate": "2023-03-27",
      "orderTime": "21:08:35.5593026",
      "orderStatus": "order cancel",
      "numberOfRoomBook": 2
      }

13. All Orders by customer:

    - URL [GET] http://localhost:9999/hotel/order/{email}

    1.  **Request-**
        url - http://localhost:9999/hotel/order/kritikasingh6421@gmail.com

            **Response-**
            [
            {
                "orderId": 3,
                "productId": 2,
                "serviceProviderName": "Paradise Hotels",
                "customerEmail": "kritikasingh6421@gmail.com",
                "transactionId": "c59444e9-34a8-40d6-b523-af071a00447a",
                "totalAmount": 5600.0,
                "orderDate": "2023-03-27",
                "orderTime": "21:08:35",
                "orderStatus": "order successful",
                "numberOfRoomBook": 2
            }

    ]

> ### 7. Payment:

1. All Payments:

- URL [GET] http://localhost:9999/payment/
  **Response-**
  [
  {
  "paymentId": 1,
  "transactionId": "c59444e9-34a8-40d6-b523-af071a00447a",
  "orderId": 3,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5600.0,
  "paymentDate": "2023-03-27",
  "paymentTime": "21:08:35",
  "paymentStatus": "payment cancel"
  },
  {
  "paymentId": 2,
  "transactionId": "0820ba83-f2d2-4f51-91de-a9147e5da5ba",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5600.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "15:28:50",
  "paymentStatus": "Successful"
  },
  {
  "paymentId": 3,
  "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
  "orderId": 1,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5500.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:08:43",
  "paymentStatus": "payment cancel"
  },
  {
  "paymentId": 4,
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 8006.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:38:14",
  "paymentStatus": "payment cancel"
  }
  ]

2. Payment by customer email:

- URL [GET] http://localhost:9999/payment/findByCustomerEmail?customerEmail={value}
  **Request:** http://localhost:9999/payment/findByCustomerEmail?customerEmail=kritikasingh6421@gmail.com
  **Response-**
  [
  {
  "paymentId": 1,
  "transactionId": "c59444e9-34a8-40d6-b523-af071a00447a",
  "orderId": 3,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5600.0,
  "paymentDate": "2023-03-27",
  "paymentTime": "21:08:35",
  "paymentStatus": "payment cancel"
  },
  {
  "paymentId": 2,
  "transactionId": "0820ba83-f2d2-4f51-91de-a9147e5da5ba",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5600.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "15:28:50",
  "paymentStatus": "Successful"
  },
  {
  "paymentId": 3,
  "transactionId": "6539d63e-e65b-46c0-a31d-59761961c10e",
  "orderId": 1,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5500.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:08:43",
  "paymentStatus": "payment cancel"
  },
  {
  "paymentId": 4,
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 8006.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:38:14",
  "paymentStatus": "payment cancel"
  }
  ]

3. Payment with respect to order:

- URL [GET] http://localhost:9999/payment/findByOrderId?orderId={value}
  **Request:** http://localhost:9999/payment/findByOrderId?orderId=4
  **Response:**[
  {
  "paymentId": 2,
  "transactionId": "0820ba83-f2d2-4f51-91de-a9147e5da5ba",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 5600.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "15:28:50",
  "paymentStatus": "Successful"
  },
  {
  "paymentId": 4,
  "transactionId": "20de33b3-c79e-4a6f-b1df-e420c105441c",
  "orderId": 4,
  "customerEmail": "kritikasingh6421@gmail.com",
  "totalAmount": 8006.0,
  "paymentDate": "2023-03-28",
  "paymentTime": "16:38:14",
  "paymentStatus": "payment cancel"
  }
  ]
