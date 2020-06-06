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


// $sql = "CREATE TABLE azurroinfo
//                             (
//                             id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY
//                             ,fullname VARCHAR(40) NOT NULL
//                             ,apartnumber VARCHAR(10) NOT NULL
//                             ,garagenumber VARCHAR(10) NOT NULL
//                              )";
                
//                       if ($link->query($sql) === TRUE) 
//                       {
//                          echo "Table carsinfo created successfully";
//                       }
//                       else 
//                       {
//                          echo "Error creating table: " . $conn->error;
//                       }
//    -----------------------------------------------------------------------------------------------------------------------------------                  
                $full_name = mysqli_real_escape_string($link, $_REQUEST['fullname']);
                $apartnumber = mysqli_real_escape_string($link, $_REQUEST['apartnumber']);
                $garagenumber= mysqli_real_escape_string($link, $_REQUEST['garagenumber']);


                $sql = "INSERT INTO azurroinfo (id,fullname, apartnumber, garagenumber) VALUES (0,'$full_name','$apartnumber','$garagenumber')";
               
                   if(mysqli_query($link, $sql)){
                     echo "Records added successfully.";
                       } 
                   else{
                     echo "ERROR: Could not able to execute $sql. " . mysqli_error($link);
                       }
// --------------------------------------------------------------------------------------------------------------------------------------------



?>                      
