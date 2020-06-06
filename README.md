<?php
 $servername='localhost';
 $username='root';
 $password='ogi123456';
 $dbname = "azurrodb";

 $link = mysqli_connect("localhost", "root", "ogi123456", "azurrodb");

 // проверка на връзката-----------------------------------------------------------------------------------------------------
 if($link === false){
                    die("ERROR: Could not connect. " . mysqli_connect_error());
                    }
                  
                $full_name = mysqli_real_escape_string($link, $_REQUEST['fullname']);
                $apartnumber = mysqli_real_escape_string($link, $_REQUEST['apartnumber']);
                $garagenumber= mysqli_real_escape_string($link, $_REQUEST['garagenumber']);


                                 $check="SELECT * FROM azurroinfo WHERE apartnumber = '$_POST[apartnumber]'";
                                 $result = mysqli_query($link,$check);
                                 $data = mysqli_fetch_array($result, MYSQLI_NUM);
                                 if($data[0] > 0) 
                                 {
                                 echo "Apartment already is exists!!!<br/>";
                                 }
                                 else
                                  {
                                   $newUser="INSERT INTO azurroinfo (id, fullname, apartnumber, garagenumber) VALUES (0,'$full_name','$apartnumber','$garagenumber')";
                                   if (mysqli_query($link,$newUser))
                                     {
                                      echo "Records added successfully.";
                                     }
                                
                                  }


?>                                      
