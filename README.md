Weather Forecast using React Redux Thunk

use openweathermap.org/forecast:5  
Api to fetch weather data for city for 5 days
signup 
https://openweathermap.org/current

redux-promise  middleware for ajax request
redux promise is an interceptor for action and action can be manipulate

For ajax request used axios
Redux Promise Flow--
--------
payload of action which is promise and by middlewaare it  resolve promise after that got data in reducer

So before going to reducer promise of axios changed to data so promise manipulated to data by middleware

The searchBar onFormSubmit function calls the fetchWeather action which is available as a prop due to the mapDispatchToProps function. Inside the fetchWeather action we are logging the request ( which at this point is a promise ), then we see the actual response logged in the reducer_weather.js reducer.
 So all the reducers are sent actions when they are triggered, and in this case because we only have one and we didn't check the type, logging it just worked. 
 =====================
Question why to use Redux-promise instead Promise
Answer The thing about PROMISE.then() is that it does not execute immediately. It only executes after the promise "resolves".  Calling .then() just saves the "then" function away until later.

So:

1. You call axios.get() with a chained .then() and maybe a chained .catch().  The .then() and .catch() functions you declare are not executed now; they're just saved away.

2. You exit from your action creator.

3. axios fires off the request asynchronously while React and Redux are doing something else.

4. The Redux Promise middleware intercepts your event, and waits until the request either completes or fails.  THIS IS WHEN YOUR .then() CODE ACTUALLY EXECUTES.

5. When that happens, the middleware dispatches a new event to your reducers.
----------------------------------------------
Payload in reducer with promise resolved
=======================
in Redux we never manipulate state instead crete new array .

wrong to use state.push ---changes state array , its mutating state 

 so use  concat  which gives new array 
 or use rest ....  [action.payload.data, ...state
 ====]

 ======================WeatherList===
 enter city that will display in list and new one will add too

 mapStateToProps will get data which is in store from reducer key weather

react-sparklines@1.6 is for chart of temp humidity and pressure

There are other very popular libraries like d3 or fusionchart

======================GoogleMap
>google.maps in console 

here we are creating our map component but we can use 3rd party component
react-google-maps