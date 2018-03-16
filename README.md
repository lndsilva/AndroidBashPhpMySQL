# AndroidBashPhpMySQL
Webservice com PHP e MySQL


<?php 

	$con = mysqli_connect("localhost:3306","root","","androidbash_movies2017_db");

	if (mysqli_connect_errno())
    {
       echo "Falha de conexão com o MySQL: " . mysqli_connect_error();
    }
	
	$id = $_GET["id"];
	
	$sql= "Select * from movies_table where id between ($id+1) and ($id+10)";
	
	$result = mysqli_query($con ,$sql);
	
	while ($row = mysqli_fetch_assoc($result)) {
		
		$array[] = $row;
		
	}
	header('Content-Type:Application/json');
	
	echo json_encode($array);
 
    mysqli_free_result($result);
 
    mysqli_close($con);
  
 ?>
