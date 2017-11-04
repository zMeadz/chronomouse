# ChronoMouse.js 

ChronoMouse.js is a compact Javascript library that helps to get current time and location data for any phone number, area code, or country code.

Get information such as the current time, GMT offset, time zone name, location, capital city, daylight savings laws, or daylight savings status.

Currently supports US & Canada Area Codes and all Country Codes.

## Getting Started
Download chronomouse.2.4.0.min.js (55 KB) and refer: 

```
<script type='text/javascript' src='chronomouse.2.4.0.min.js'></script >
```

## Examples

```
console.log ( getLocalInfo('615').time.display );

// 8:45 AM 

```

```
getLocalInfo('(615) 555-5555',{ 
	military: false, 
	zone_display: 'area' 
}, 
	function(object){ 
		var phoneInfo = object.time.display +' '+ object.location; 
		console.log ( phoneInfo ); 

		// 8:45 PM Nashville, TN 

}); 
```

```
getLocalInfo('+49',{ zone_display: 'offset' }, function(object){ 
	var phoneInfo = object.time.display +' '+ object.time.zone; 
	console.log ( phoneInfo ); 

	// 17:00 GMT+3 
});
```

```
var phoneDiv = document.getElementsById('phone'); 
var phoneNumber = phoneDiv.textContent; 
var currentTime = getLocalInfo(phoneNumber,{military:false}).time.display; 
phoneDiv.textContent = phoneNumber+' | '+currentTime ; 

// (720) 555-5555 | 3:20 PM 
```

## Properties

```
getLocalInfo( string area/country code, options, function callback )
```

getLocalInfo( ) accepts the first 6 numberical and '+' characters of any string. 

Input text must start with '+' or '00' to trigger country code search. 

```
var object = getLocalInfo('615'); 
```

**object.text** - string. The input text for the area or country code.

**object.location** - string. For area codes, the name of the major city for that area followed by state abbreviation. Country codes, the name of the country. 

```
console.log( getLocalInfo('415').location ); 
// San Francisco, CA 

console.log( getLocalInfo('+55').location ); 
// Brazil 
```

**object.valid** - boolean. True, if a matching code was found in the time info arrarys. If false, other properties will may falsy (undefined or false). 

**object.dst** - boolean. If country has Daylight Savings laws. NOT an indication of Daylight Savings being currently active.

**object.dstnow** - boolean. If Daylight Savings is currently in effect.

**object.offset** - number. Offset of the zone without calculating daylight savings.

**object.type** - string. Distinguishes area from country code. Will return either 'area' or 'country'.

**object.country_info** - object. Contains info about the country. See further properties below. If US/Canada Country Code, returns info for US.

     -**object.country_info.code** - string. Country calling code, i.e. '55'.

     -**object.country_info.capital** - string. Capital city.

     -**object.country_info.dst** - boolean. If country has Daylight Savings laws. NOT an indication of Daylight Savings being currently active.

     -**object.country_info.offset** - number. GMT Offset.

**object.options** - object. Received input options. More on passing options below.

     -**object.options.military** - boolean. If 24-hour time is set. Default true.

     -**object.options.zone_display** - string. 'name' or 'offset'. Default 'name'.

**object.time** - object. Contains info about the current time.

     -**object.time.display** - string. Current time in hh:mm format. If miltary time is set to false, then this will include the meridian (AM/PM).

```
     console.log ( getLocalInfo('615').time.display ); 
     // 8:45 AM 
```

     -**object.time.hour** - string. Current hour.

     -**object.time.hour2** - string. For split US/Canada time zones - the current hour of the time zone immediately east.

     -**object.time.mins** - string. Current minutes.

     -**object.time.meridian** - string. Current meridian (AM/PM).

     -**object.time.meridian2** - string. For split time zones - the other meridian for hour2.

     -**object.time.zone** - string. Time zone, displayed as the name of the time zone, or as the GMT offset, depending on the options. The default is 'offset' and is displayed in format "GMT+/-[offset]".


```
     console.log ( getLocalInfo('615').time.zone ); 
     // GMT-5 

     console.log ( getLocalInfo('615',{zone_display: 'area'}).time.zone ); 
     // CST 
```

## Setting Options 

**military** - boolean. Sets time to 24-hour format. Default 'true'. 
```
console.log ( getLocalInfo('615').time.display ); 
// 19:00 

console.log ( getLocalInfo('615',{military: false}).time.display ); 
// 7:00 PM 
```
**zone_display** - string. Sets object.zone_display. Can be 'name' OR 'offset'. Displays zone by zone name or GMT offset. Default 'offset'. 
```
console.log ( getLocalInfo('615',{zone_display: 'area'}).time.zone ); 
// CST 

console.log ( getLocalInfo('615',{zone_display: 'offset'}).time.zone ); 
// GMT-5
```

