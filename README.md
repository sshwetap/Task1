# Task1 Registration page
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css?family=Roboto:400,700" rel="stylesheet">
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script> 
<script src='https://www.google.com/recaptcha/api.js'></script>
<style>
    
	body {
		color: #fff;
		background: #3598dc;
		font-family: 'Roboto', sans-serif;
	}
    .form-control{
		height: 41px;
		background: #f2f2f2;
		box-shadow: none !important;
		border: none;

	}
	.form-control:focus{
		background: #e2e2e2;
	}
    .form-control, .btn{        
        border-radius: 3px;
        margin: auto;
        padding-right: 10px;
    }
	.signup-form{
		width: 390px;
        height: auto;
		margin: 30px auto;
	}
	.signup-form form{
		color: #999;
		border-radius: 3px;
    	margin-bottom: 15px;
        background: #fff;
        box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.3);
        padding: 30px;
    }
	.signup-form h2 {
		color: #333;
		font-weight: bold;
        margin-top: 0;
    }
    .signup-form hr {
        margin: 0 -30px 20px;
    }    
	.signup-form .form-group{
		margin-bottom: 20px;
        margin-top:20px;
	}
    .signup-form .btn{        
        font-size: 16px;
        font-weight: bold;
		background: #60b0f1;
		border: none;
		min-width: 140px;
    }
	.signup-form .btn:hover, .signup-form .btn:focus{
		background: #f1f2f3 !important;
        outline: none;
	}
    .signup-form a{
		color: #fff;
		text-decoration: underline;
	}
	.signup-form a:hover{
		text-decoration: none;
	}
	.signup-form form a{
		color: #1b699c;
		text-decoration: none;
	}	
	.signup-form form a:hover{
		text-decoration: underline;
	}
    .signup-form .hint-text {  
		padding-bottom: 15px;
		text-align: center;
    }
 
</style>
</head>
<body>
<div class="signup-form">
    <form action="connector.php" method="post">
		<h2>Registration Page</h2>
		<hr>
        <div class="form-group">
			<div class="row">
				<div class="col-xs-6"><input type="text" class="form-control" name="first_name" pattern="[A-Za-z]" placeholder="First Name" required="required"></div>
				<div class="col-xs-6"><input type="text" class="form-control" name="last_name" pattern="[A-Za-z]" placeholder="Last Name" required="required"></div>
			</div>        	
        </div>
        <div class="form-group">
        	<input type="email" class="form-control" name="email" placeholder="Email" required="required">
        </div>
        <div class="input-box">
           <input type="tel" class="form-control"name="Mobile Number" pattern="[789][0-9]{9}"placeholder="Enter your number" required>
          </div>
        <div class="form-group">
            <span class="details">Address</span>
            <div class="form-group">
                <select name="optone" class="selectDD form-group" style="width: 35%;" id="stateSel" size="1">
                    <option value="" selected="selected">Select Country</option>
                </select>
                <br>
                <br>
                <select name="opttwo" class="selectDD form-group" style="width: 35%;" id="countySel" size="1">
                    <option value="" selected="selected">Select State</option>
                </select>
                <br>
                <br>
                <select name="optthree" class="selectDD form-group" style="width: 35%;" id="citySel" size="1">
                    <option value=""  selected="selected">Select City</option>
                </select>
            </div>
            <div class="form-group">
                <div class="g-recaptcha" data-sitekey="6LfKURIUAAAAAO50vlwWZkyK_G2ywqE52NU7YO0S" data-callback="verifyRecaptchaCallback" data-expired-callback="expiredRecaptchaCallback"></div>
                <input class="form-control d-none" data-recaptcha="true" required data-error="Please complete the Captcha">
                <div class="help-block with-errors"></div>
            </div>         
           
            
		<div class="form-group btn">
            <a href="homepage.html">  
                Submit 
              </a>
        </div>
        
    </form>
    <script>
        var stateObject = 
                {
                    "India":
                    {
                        "Maharashtra": ["Pune", "Mumbai", "Nagpur"],
                        "Punjab": ["Chandighar", "Ludhiana"],
                        "Gujrat":["Surat", "Ahemdabad"]
                    },
                    "United States": 
                    {
                        "Arizona": ["Phoenix", "Tucson"],
                        "Alaska": ["Adak", "Akhiok"]
                    },
                    "United Kingdom":
                    {
                        "England": ["Cambridge.", "London", "Bristol"],
                        "Scotland": ["Glasgow", "Edinburgh"]
                    }
                }
                window.onload = function()
                {
                var stateSel = document.getElementById("stateSel"),
                countySel = document.getElementById("countySel"),
                citySel = document.getElementById("citySel");

                for (var state in stateObject)
                {
                    stateSel.options[stateSel.options.length] = new Option(state, state);
                }
            
                stateSel.onchange = function()
                {
                    countySel.length = 1;
                    citySel.length =1;
                    if(this.selectedIndes < 1) return;
                    for(var county in stateObject[this.value]){
                    countySel.options[countySel.options.length] = new Option(county, county);
                }
            }
            
            stateSel.onchange();
            
            countySel.onchange = function(){
                citySel.length = 1;
                if(this.selectedIndex < 1) return;
                
                var cities = stateObject[stateSel.value][this.value];
                for(var i = 0; i < cities.length; i++){
                    citySel.options[citySel.options.length] = new Option(cities[i], cities[i]);
                }
            }
        }
    </script>

</div>
</body>
</html>


	
	
	
#Task1 Homepage
	<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
  <style>
    /* Set height of the grid so .sidenav can be 100% (adjust if needed) */
    .row.content {
        height: 1500px}
    
    /* Set gray background color and 100% height */
    .sidenav {
      background-color: #f1f1f1;
      height: 100%;
    }
    
    /* Set black background color, white text and some padding */
    footer {
      background-color: #555;
      color: white;
      padding: 15px;
    }
    
    /* On small screens, set height to 'auto' for sidenav and grid */
    @media screen and (max-width: 767px) {
      .sidenav {
        height: auto;
        padding: 15px;
      }
      .row.content {height: auto;} 
    }
    .col-sm-9{
        height: auto;
        font-size: 45px;
    }
    .container-fluid{
        font-size: 20px;
    }
    .sidenav
    {
        font-size: 25px;
    }
    .logo{
        height: 60px;
    }
  </style>
</head>
<body>

<div class="container-fluid">
  <div class="row content">
    <div class="col-sm-3 sidenav">
        <a href=""><img class="logo"src="logo.png"</a>
      <p>Dashboard</p>
      <ul class="nav nav-pills nav-stacked">
        <li class="active"><a href="#section1">Home</a></li>
        <li><a href="#section2">Friends</a></li>
        <li><a href="#section3">Family</a></li>
        <li><a href="#section3">Photos</a></li>
      </ul><br>
    </div>

    <div class="col-sm-9">
      <p><small>Welcome</small></p>
      <hr>
      <p>Hello Fname Lname</p>
        <img src="img.jpg">
      <br><br>
      
      
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<footer class="container-fluid">
  <p>Thank You!</p>
</footer>

</body>
</html>
