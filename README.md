# select-query-in-wordpress
/*custom wp query to check user login*/

global $wpdb;

if(isset($_POST['submit'])){
  $useremail=$_POST['email'];
  $password=$_POST['password'];
  $pas=md5($password);


  $select=$wpdb->get_results("SELECT * from wp_users where (user_email ='".$useremail."' AND user_pass ='".$pas."')");
foreach ($select as $selects) {
$useremailid =  $selects->user_email;
$userpassword = $selects->user_pass;

}
if ($useremail==$useremailid AND $pas==$userpassword){    ?>
<script>
window.location.href = "http://localhost/statichtml/wordpress/getstarted/" ;  

</script><?php
  }

 else {
  echo "Name or Password incorrect.";
}

}
