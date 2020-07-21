<?php
include_once 'azurroheader.php';
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" type="text/css" href="azurrostyle.css" media="screen"/>
    <title>AzurrroTakeData</title>
</head>
<body>
            <div class="main">
                        <div class="text">
                           <h3>Private site for Azurro Garden owners.</h>
                           <h3>...........................................</h>
                        </div>

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


                                              //             $sql = "INSERT INTO azurroinfo (id,fullname, apartnumber, garagenumber) VALUES (0,'$full_name','$apartnumber','$garagenumber')";
                                                        
                                              //                if(mysqli_query($link, $sql)){
                                              //                  echo "Records added successfully.";
                                              //                    } 
                                              //                else{
                                              //                  echo "ERROR: Could not able to execute $sql. " . mysqli_error($link);
                                              //                    }
                                              // --------------------------------------------------------------------------------------------------------------------------------------------
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
                                                    // else
                                                    // {
                                                    //     echo "Error adding user in database<br/>";
                                                    // }
                                              }
                             ?>

</div> 
                
              
                </body>
                </html>
                <?php
                include_once 'azurrofooter.php';
                ?>
                
                      
