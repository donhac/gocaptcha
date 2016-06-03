# gocaptcha
一个简单的Go语言实现的验证码
##简介

基于Golang实现的图片验证码生成库，可以实现随机字母个数，随机直线，随机噪点等。可以设置任意多字体，每个验证码随机选一种字体展示。

##实例

具体实例可以产科example目录，有生成的验证码图片。

```
	
  func Get(w http.ResponseWriter, r *http.Request) {
      //初始化一个验证码对象
		captchaImage,err := gocaptcha.NewCaptchaImage(dx,dy,gocaptcha.RandLightColor());

  	  //画上三条随机直线
  	  captchaImage.Drawline(3);

  	  //画边框
  	  captchaImage.DrawBorder(gocaptcha.ColorToRGB(0x17A7A7A));
      
  	  //画随机噪点
  	  captchaImage.DrawNoise(gocaptcha.CaptchaComplexHigh);
  
  	  //画随机文字噪点
  	  captchaImage.DrawTextNoise(gocaptcha.CaptchaComplexLower);
      //画验证码文字，可以预先保持到Session种或其他储存容器种
  	  captchaImage.DrawText(gocaptcha.RandText(4));
    	if err != nil {
    		  fmt.Println(err)
    	}
  	  //将验证码保持到输出流种，可以是文件或HTTP流等
		  captchaImage.SaveImage(w,gocaptcha.ImageFormatJpeg);
	}

```




