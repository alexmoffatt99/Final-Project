
cancelBtn.onclick=function(){
  ChangeForm(HomePage)
}

submitBtn.onclick=function(){
  let Name_Clinic = inpEnterClinic.value
  let Latitude = inptLong.value
  let Longitude = inptLat.value
  query= "INSERT INTO `clinics` (`Name_Clinic`, `Latitude`, `Longitude`) VALUES ('" + Name_Clinic + "'," + Latitude + "," + Longitude + ");"
  console.log(query)
  req1 = Ajax("https://ormond.creighton.edu/courses/375/ajax-connection.php","POST","host=ormond.creighton.edu&user=amm49490&pass=ALEXmoff99&database=amm49490&query=" + query);  
  if (req1.status == 200) { //transit worked.
                    NSB.MsgBox(Name_Clinic + " was added to the database.")
            } else
                //transit error - Handle that with an error message.
                NSB.MsgBox("Error code: " + req1.status)

}
