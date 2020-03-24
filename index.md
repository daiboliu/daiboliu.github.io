
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta content="IE=edge" http-equiv="X-UA-Compatible">
	<meta content="initial-scale=1.0, maximum-scale=1.0, user-scalable=no, width=device-width" name="viewport">
	<meta name="theme-color" content="#3f51b5">
	<title>MySSR</title>

	<!-- css -->
	<!--<link href="/theme/material/css/base.css" rel="stylesheet">
	<link href="/theme/material/css/project.css" rel="stylesheet">
	<link href="https://fonts.loli.net/css?family=Material+Icons" rel="stylesheet">
     -->
      <link href="/assets/css/bootstrap.min.css" rel="stylesheet">
  	<link href="/assets/css/material-dash.css" rel="stylesheet">
   <link rel="stylesheet" href="/assets/css/animate.min.css">
  
    <link href="/assets/css/sweetalert.css" rel="stylesheet">
    <script type="text/javascript" src="/assets/js/sweetalert.min.js"></script>
    <script src="/assets/js/fuck.js"></script>
   <link href="https://fonts.loli.net/css?family=Material+Icons" rel="stylesheet">
	
	<!-- favicon -->
  	<link rel="shortcut icon" href="/theme/material/images/users/favicon.png" type="image/x-icon" />
	<!-- ... -->
</head>

 <style>
  @import url(/assets/css/font-awesome.min.css);
 
.input-group {
     padding-top: 10px;
     padding-bottom: 10px;
}
   
@font-face { 
	font-family: title-speed;
	src: url('/fonts/LobsterTwo-Regular.otf');
} 

.navbar-brand{
  font-family: title-speed;
  font-size: 1.2rem;
  font-weight: 500;
  
 }
   
      
    #forgotPwd span:hover {
    text-shadow:0 0 5px #fff;
   }
   
  #forgotPwd span {
    display:block; overflow: hidden;
   }
   
   #forgotPwd {
     height:36px; margin-bottom: 8px; text-align: right; cursor: pointer; 
   }
   #forgotPwd span {
     font-size: 11px;
     padding-right: 15px;
   }
 
 </style>
  
<body class="off-canvas-sidebar">
  
    <nav class="navbar navbar-primary navbar-transparent navbar-absolute">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#navigation-example-2">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a class="navbar-brand animated swing" href="/">MySSR</a>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav navbar-right">
                   <!-- <li>
                        <a href="/">
                            <i class="material-icons">dashboard</i> Home
                        </a>
                    </li>-->
                    <li class="">
                        <a href="/auth/register">
                            <i class="material-icons">person_add</i> Register
                        </a>
                    </li>
                    <li class="active">
                        <a href="/auth/login">
                            <i class="material-icons">fingerprint</i> Login
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
  
    
 <div class="wrapper wrapper-full-page">
  
  <div class="full-page login-page" data-image="/img/random.jpeg" filter-color="black"> 
    <!--   you can change the color of the filter page using: data-color="blue | purple | green | orange | red | rose " -->
    <div class="content">
      <div class="container">
        <div class="row">
          <div class="col-md-4 col-sm-6 col-md-offset-4 col-sm-offset-3">
            <form method="#" action="#" _lpchecked="1">
              <div class="card card-login animated flipInX">
                <div class="card-header text-center" data-background-color="rose">
                  <h4 class="card-title">Login</h4>
                  <div class="social-line">
                    <a href="#tg" class="btn btn-just-icon btn-simple">
                      <i class="fa fa-telegram"></i>
                    </a>
                    <a href="#pablo" class="btn btn-just-icon btn-simple">
                      <i class="fa fa-twitter"></i>
                    </a>
                    <a href="#eugen" class="btn btn-just-icon btn-simple">
                      <i class="fa fa-facebook-square"></i>
                    </a>
                  </div>
                </div>
                <p class="category text-center" style="font-family:title-speed; font-size:1.1rem; font-weight: 400">
                  MySSR
                </p>
                <div class="card-content">
                  <div class="input-group">
                    <span class="input-group-addon">
                      <i class="material-icons">email</i>
                    </span>
                    <div class="form-group label-floating is-empty">
                      <label class="control-label">Email address</label>
                      <input class="form-control" style="cursor: auto;" type="email" id="email">
                      <span class="material-input"></span></div>
                  </div>
                  <div class="input-group">
                    <span class="input-group-addon">
                      <i class="material-icons">lock_outline</i>
                    </span>
                    <div class="form-group label-floating is-empty">
                      <label class="control-label">Password</label>
                      <input class="form-control" style="cursor: auto;" type="password" id="passwd">
                      <span class="material-input"></span></div>
                  </div>
                </div>
                <div class="footer text-center">
                  <button type="submit" id="login" class="btn btn-rose btn-simple btn-wd btn-lg">Let's go</button>
                </div>
                
                  <div class="text-right">
					<a class="" href="/password/reset" id="forgotPwd"><span>Forgot Password ?</span></a>
                </div>
                
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>

    <div class="full-page-background" style="background-image: url(/img/random.jpeg) "></div>
   </div>
   
  </div>
  

  
  
 <!-- <script src="//cdn.staticfile.org/jquery/2.2.1/jquery.min.js"></script> -->
   <script type="text/javascript" src="../js/jquery-2.2.1.min.js"></script>


 
<script>
    $(document).ready(function(){
        function login(){

			document.getElementById("login").disabled = true;

            $.ajax({
                type:"POST",
                url:"/auth/login",
                dataType:"json",
                data:{
                    email: $("#email").val(),
                    passwd: $("#passwd").val(),
					code: $("#code").val(),
                    remember_me: $("#remember_me:checked").val()                },
                success:function(data){
              		var user= data.user;
                      /*
                      swal({
                        title: "Merry Christmas~!",
                        html: "<span style='color: #9954bb; font-size:2rem; font-weight: 500'>"+user+"</span>",
                        imageUrl: "/assets/images/shendan.png",
                      }).then(function(){
                        window.location.href = '/user/';
                      });
                    */
                    if(data.ret == 1){
                        swal({
                          title: "<span style='color: #9954bb; font-size:2rem; font-weight: 500'>"+user+"</span>",
                          text: "欢迎进入MySSR！！！",
                          imageUrl: "/assets/images/dotdot.jpg",
                          animation: "slide-from-top",
                          html: true,
                        },
                        function(){
   						 window.location.href = '/user/';
                        });
                    }else{
                    	swal(
                        'Error',
                        data.msg,
                        'error'
                                );

			document.getElementById("login").disabled = false;
			                    }
                },
                error:function(jqXHR){
			$("#msg-error").hide(10);
			$("#msg-error").show(100);
			$("#msg-error-p").html("发生错误"+jqXHR.status);
					document.getElementById("login").disabled = false;
			                }
            });
        }
        $("html").keydown(function(event){
            if(event.keyCode==13){
                login();
            }
        });
        $("#login").click(function(){
            login();
        });

		$('div.modal').on('shown.bs.modal', function() {
			$("div.gt_slider_knob").hide();
		});

		$('div.modal').on('hidden.bs.modal', function() {
			$("div.gt_slider_knob").show();
		});
    })
</script>
<script>
    var isWeixin = function () {
      var ua = navigator.userAgent.toLowerCase();
      return ua.match(/MicroMessenger/i) == "micromessenger";
    };
    if (isWeixin() == true) {
      $('body').html('<h5 style="margin:20px">不支持在微信内访问<br>请点击右上角菜单<br>选择浏览器打开</h5>')
    }
  </script>

 
<script src="/assets/js/perfect-scrollbar.jquery.min.js"></script>
<script src="/assets/js/material-dashboard.js"></script>
  <script src="/assets/js/material.min.js"></script>
 <script type="text/javascript" src="/assets/js/love.js"></script>
  <script text="text/javascript" src="/assets/js/particle.js"></script>
</body>
</html>
