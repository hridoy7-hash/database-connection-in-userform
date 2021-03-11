# database-connection-in-userform

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP LEARNING</title>
</head>
<?php

if(isset($_POST['submit'])){
    $username = $_POST['username'];
    $email = $_POST['email'];
    $password = $_POST['password'];

    $connection = mysqli_connect('localhost','root','','user_information');

    if(!$connection){
        die ("Not connected ".mysqli_error($connection));
    }
     //INSERT INTO `user_information` (`Id`, `Name`, `Email`, `Password`, `submit_date`) VALUES (NULL, 'Rakib', 'rakib@gmail.com', '12345', current_timestamp());
    $query = "INSERT INTO user_information (Name,Email,Password)";
    $query.= "VALUES ('$username','$email','$password')";
     
    $result = mysqli_query($connection,$query);
    if(!$result){
        die ("data insert unsuccessfull".mysqli_error($connection)) ;
    }
    
}
?>
<body>

        <form action="index.php" method="post">
        <input type="text" name="username" placeholder="USER NAME">
        <input type="email" name="email" placeholder="USER EMAIL">
        <input type="password" name="password" placeholder="PASSWORD">
        <input type="submit" name="submit" value="submit">

</form>
    
</body>
</html>
