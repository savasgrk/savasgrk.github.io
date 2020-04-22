<!DOCTYPE html>
<html>
<body>

<?php

$lines=array();
$myfile = fopen("https://github.com/savasgrk/savasgrk.github.io/blob/master/Username.txt", "r") or die("Unable to open file!");
while(!feof($myfile))
{
	 $line=fgets($myfile);

    //process line however you like
    $line=trim($line);

    //add to array
    $lines[]=$line;

}
//$data= fread($myfile,filesize("/home/sp20/355/sosa6554/public_html/cs370/Username.txt"));
$size= count($lines, COUNT_NORMAL);
$name1;
$password1;

fclose($myfile);
//$myfile1 = fopen("/home/sp20/355/sosa6554/public_html/cs370/Username.txt", "r") or die("Unable to open file!");
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
			$myfile1 = fopen("https://github.com/savasgrk/savasgrk.github.io/blob/master/Username.txt", "w+") or die("Unable to open file!");
			fwrite($myfile1, $name);
			fclose($myfile1);
			echo "done";
        }
		
	
	

?>

	<form action="#" method="post"> 
		<h1> Snake Game Login Page </h1>
		Username: <input type="text" name="Username" id="Username"></input>
		Password: <input type="text" name="Password" id="Password"></input>

			<input type="submit" name="button1"
                class="button" value="Button1" /> 
	</form> 
<script>

	var data=[];
	var size= <?php echo $size; ?>;
	var newUsername;
	var newPassword

function setUser()
{
//https://github.com/savasgrk/savasgrk.github.io/edit/master/index.md
	newUsername= document.getElementById("Username").value;
	newPassword= document.getElementById("Password").value;
	for(var i=0; i<size; i++)
	{
		if(newUsername==data[i])
		{
			document.write("exists");
	
			return false;
		}
	}
	if((!newPassword) || newPassword.length == 0 || newPassword==null)
	{
		document.write("null");
		return false;
	}
	if((!newUsername) || newUsername.length == 0 || newUsername==null)
	{
		document.write("null");
		return false;
	}
	document.write(newUsername);
	data.push(newUsername);
	document.write("\n");
	document.write(data);
	return true;
}
function main()
{
	var data=<?php echo json_encode($lines); ?>;
	var size= <?php echo $size; ?>;
	
	
	
	document.write('the');
	document.write(data);
}
main();
</script>

</body>
</html>
