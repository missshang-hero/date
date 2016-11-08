# date
dear diary
用clip实现圆环进度条加载
    <!DOCTYPE html>  
    <html lang="cn">  
    <head>  
        <meta charset="UTF-8">  
        <title>Document</title>  
        <style>  
        *{  
            margin: 0;  
            padding: 0;  
        }  
        .wrap,.circle,.percent{  
            position: absolute;  
            width: 200px;  
            height: 200px;  
            border-radius: 50%;  
        }  
        .wrap{  
            top:50px;  
            left:50px;  
            background-color: #ccc;  
        }  
        .circle{  
            box-sizing: border-box;  
            border:20px solid #ccc;  
            clip:rect(0,200px,200px,100px);  
        }  
        .clip-auto{  
            clip:rect(auto, auto, auto, auto);  
        }  
        .percent{  
            box-sizing: border-box;  
            top:-20px;  
            left:-20px;  
        }  
        .left{  
            transition:transform ease;  
            border:20px solid blue;  
            clip: rect(0,100px,200px,0);  
        }  
        .right{  
            border:20px solid blue;  
            clip: rect(0,200px,200px,100px);  
        }  
        .wth0{  
            width:0;  
        }  
        .num{  
            position: absolute;  
            box-sizing: border-box;  
            width: 160px;  
            height: 160px;  
            line-height: 160px;  
            text-align: center;  
            font-size: 40px;  
            left: 20px;  
            top: 20px;  
            border-radius: 50%;  
            background-color: #fff;  
            z-index: 1;  
        }  
        </style>  
        <script src="http://apps.bdimg.com/libs/zepto/1.1.4/zepto.min.js"></script>  
    </head>  
    <body>  
    <div class="wrap">  
        <div class="circle">  
            <div class="percent left"></div>  
            <div class="percent right wth0"></div>  
        </div>  
        <div class="num"><span>0</span>%</div>  
    </div>  
    </body>  
    <script>  
        var percent=0;  
        var loading=setInterval(function(){  
            if(percent>100){  
                percent=0;  
                $('.circle').removeClass('clip-auto');  
                $('.right').addClass('wth0');  
            }else if(percent>50){  
                $('.circle').addClass('clip-auto');  
                $('.right').removeClass('wth0');  
            }  
            $('.left').css("-webkit-transform","rotate("+(18/5)*percent+"deg)");  
            $('.num>span').text(percent);  
            percent++;  
        },200);  
    </script>  
    </html>  
