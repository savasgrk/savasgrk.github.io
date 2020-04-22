<?php
$lines=array();
$myfile = fopen("https://savasgrk.github.io/Username.txt", "r") or die("Unable to open file!");
echo "File opened";
while(!feof($myfile))
{
	 $line=fgets($myfile);
    	$line=trim($line); 
   	 $lines[]=$line;
	echo $line;
}
$size= count($lines, COUNT_NORMAL);
$name1;
$password1;
fclose($myfile);
if(isset($_POST['button1'])) { 
            button1(); 
        } 
	 function button1() { 
            echo "This is Button1 that is selected"; 
			$name= htmlentities($_POST['Username']);
			$password= htmlentities($_POST['Password']);
			global $size;
			global $lines;
			echo $size;
			if($name==null || strlen($name)==0 ||!$name)
			{
					echo "problem1";
					return false;	
			}
			if($password==null || strlen(password)==0 ||!$password)
			{
					echo "problem2";
					return false;
			}					
			for($counter=0; $counter<$size; $counter++)
			{		
					if($name==$lines[$counter])
					{
							echo "problem3";
							return false;
					}
					echo "success";
			}
			echo "reached";
			$myfile1 = fopen("https://savasgrk.github.io/Username.txt", "w") or die("Unable to open file!");
			fwrite($myfile1, $name);
			fclose($myfile1);
			echo "done";
        }
?>
	<form method="post"> 
		<h1> Snake Game Login Page </h1>
		Username: <input type="text" name="Username" id="Username">
		Password: <input type="text" name="Password" id="Password">
			<input type="submit" name="button1"
                class="button" value="Button1" /> 
	</form> 
