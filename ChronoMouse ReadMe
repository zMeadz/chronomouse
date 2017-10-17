ChronoMouse.js

Intro

A library to look up time and location data for area and country calling codes.

Supports US Area Codes and Country Codes.


Setup

Download chronomouse.min.js (55 KB) and refer:

<script type="text/javascript" src="chronomouse.min.js"></script>


Examples

console.log( getLocalInfo('615').time.display ); // "8:45 AM"

--

getLocalInfo("(615) 555-5555",{

    military: false,
    zone_display: "area"

},function(object){

	var phoneInfo = object.time.display +" "+ object.location;

    console.log( phoneInfo ); // "8:45 PM Nashville, TN"

});

--

getLocalInfo("+49",{

    zone_display: "offset"

},function(object){

	var phoneInfo = object.time.display +" "+ object.time.zone;

    console.log( phoneInfo ); // "17:00 GMT+3"

});

--

getLocalInfo("+34",{

    zone_display: "offset"

},function(object){

	var phoneInfo = object.time.display + 

    console.log(object.time.display); // "15:30"

});

--

var phoneNumber = document.getElementsById('phone');

var currentTime = getLocalInfo(phoneNumber,{military:false}]).time.display;

phoneNumber.appendChild( currentTime );

--

Area Code and Country Code Input Formats 


Area Codes

555 (555) 1-555 1.555 +1-555, or entire phone number, in which case it will take the first 5 numbers.

Country Codes
Must start with "+" or "00" to trigger country code search.
+55 0055



Properties

var object = getLocalInfo('615');

	getLocalInfo(str [area code] OR str [country code], options, func callback (optional) )


object.text - str. The input text for the area or country code.

object.location - str. For area codes, the name of the major city for that area. Country codes, name of the country.

object.valid - boolean. True, if a matching code was found in the time info arrarys. If false, other properties will may falsy (undefined or false).

object.dst - boolean. If country has Daylight Savings laws. NOT an indication of Daylight Savings being currently active.

object.offset - number. Offset of the zone without calculating daylight savings. 

object.type - str. Distinguishes area from country code. Will return either "area" or "country".


object.country_info - object. Contains info about the country. See further properties below. If US/Canada Country Code, returns info for US. 

	object.country_info.code - str. Country calling code, i.e. "55".

	object.country_info.capital - str. Capital city.

	object.country_info.dst - boolean. Same as object.dst.

	object.country_info.offset - number. GMT Offset.


object.options - object. Received input options. More on passing options below.

	object.options.military - boolean. If 24-hour time is set. Default true.
	object.options.zone_display - str. "name" or "offset". Default "name".


object.time - object. Contains info about the current time.

	object.time.display - str. Current time in hh:mm format. If miltary time is set to false, then this will include the meridian (AM/PM).

		ex.
		console.log( getLocalInfo('615').time.display ); // "8:45 AM"

	object.time.hour - str. Current hour.

	object.time.mins - str. Current minutes.

	object.time.meridian - str. Current meridian (AM/PM).

	object.time.zone - str. Time Zone, displayed as the name of the time zone, or as the GMT offset depending on the options. If zone_display is set to offset, then daylight savings will be calculated for the offset.

		ex. 
		console.log( getLocalInfo('615').time.zone ); // "CST"
		console.log( getLocalInfo('615',{zone_display: "offset"}).time.zone ); // "GMT-5"



Setting Options

military - boolean. Sets time to 24-hour format. Default "true".

	ex.
	console.log( getLocalInfo('615').time.display ); // "19:00"
	console.log( getLocalInfo('615',{military: false}).time.display ); // "7:00 PM"


zone_display - str. "name" OR "offset". Displays zone by name or GMT offset. Default "name".

	ex. 
	console.log( getLocalInfo('615',{zone_display: "offset"}).time.zone ); // "GMT-5"

Changing defaults
Default options can be changed in setOptions().






