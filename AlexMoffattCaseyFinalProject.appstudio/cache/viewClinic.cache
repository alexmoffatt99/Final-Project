var position = ''
var items = ''


viewClinic.onshow=function(){
  var query = "SELECT Name_Clinic,Latitude,Longitude FROM clinics;"
        req1 = Ajax("https://ormond.creighton.edu/courses/375/ajax-connection.php","POST","host=ormond.creighton.edu&user=amm49490&pass=ALEXmoff99&database=amm49490&query=" + query);
        //req1 = Ajax("https://ormond.creighton.edu/courses/375/ajax-connection.php", "POST", "host=ormond.creighton.edu&user=amm49490&pass=ALEXmoff99&database=amm49490&query=SELECT * FROM clinics;");
        if (req1.status == 200) { //transit worked.
              results = JSON.parse(req1.responseText)
              if (results.length == 0)
                  NSB.MsgBox("There are no Clinics in the database.")
              else {        
                  // output the clinics in arrays
                  items = results
                  //NSB.MsgBox(items)
                  //console.log(items)
                  arrayClinics = []
                  arrayLongitude = []
                  arrayLatitude = []
                  //console.log(items[0][0])
                  //store results from call to database
                  for(i=0; i<=items.length-1;i++){
                    arrayClinics.push(items[i][0])
                    arrayLatitude.push(items[i][1])
                    arrayLongitude.push(items[i][2])
                  }
                  
                  //put the clinics on the google map
                  for (i=0;i<arrayClinics.length-1;i++) {
                    point = new google.maps.LatLng(arrayLatitude[i],arrayLongitude[i]);
                    marker = gmpClinic.setMarker({position: point});
                    infowindow = gmpClinic.setInfoWindow(arrayClinics[i], marker);
                    }
                  
                }  // end else
          } else
              //transit error - Handle that with an error message.
              NSB.MsgBox("Error code: " + req1.status)
  }
  
  
  
  navigator.geolocation.getCurrentPosition(success,error);
      function success(pos) {
          var position = pos.coords;
          //console.log(position.latitude)
          //console.log(position.longitude)
          var latlon = position.latitude + "," + position.longitude;
          //Set pin on users location
          gmpClinic.mapOptions.latitude = position.latitude;
          gmpClinic.mapOptions.longitude = position.longitude;
          gmpClinic.refresh();
          // Add marker for current location via geolocation
          point = new google.maps.LatLng(position.latitude,position.longitude);
          marker = gmpClinic.setMarker({position: point});
          infowindow = gmpClinic.setInfoWindow("You are here", marker);          
        //console.log(latlon)
          }
      function error(err) {
          console.warn(`ERROR(${err.code}): ${err.message}`);
          }


Button1.onclick=function(){
  ChangeForm(HomePage)
}
