
    <!DOCTYPE html>
    <html>
    <head>
        <title>Login</title>
        <link rel="shortcut icon" type="image/x-icon" href="/favicon.ico" />
        <meta charset="utf-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
        <link href="/assets/styles/vendors-extensions/login/bootstrap-ex.min.css?ver=180314001" rel="stylesheet" />

        
    
    <link href="/assets/bundles/themes/default.min.css?ver=180314001" rel="stylesheet" />


    </head>
    <body>

        <div id="divLoading" style="display: none">
            <h2>
                Loading... please wait
            </h2>
        </div>

        <div id="mainholder" class="block-login">
            <form id="formLogin" class="form-login" action="/" method="POST" autocomplete="off">
                



<div class="box-lang">
    <div class="dropdown">
        <span class="btn dropdown-toggle" type="button" id="langList" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
            <span class="flag" id="flag"></span>
            <span id="lblLanguage">English</span> 
            <span class="caret"></span>
            <input type="hidden" value="en-US" id="hidLanguage" name="hidLanguage">
        </span>
        <ul class="dropdown-menu" aria-labelledby="langList" id="language-ddl">
            <li><a href="#"><span class="flag flag-en" data-language-code="en-US"></span>English</a></li>
            <li><a href="#"><span class="flag flag-tw" data-language-code="zh-TW"></span>繁體中文</a></li>
            <li><a href="#"><span class="flag flag-cn" data-language-code="zh-CN"></span>简体中文</a></li>
            <li><a href="#"><span class="flag flag-jp" data-language-code="ja-JP"></span>日本語</a></li>
            <li><a href="#"><span class="flag flag-th" data-language-code="th-TH"></span>ภาษาไทย</a></li>
            <li><a href="#"><span class="flag flag-kr" data-language-code="ko-KR"></span>한국어</a></li>
                <li><a href="#"><span class="flag flag-vn" data-language-code="vi-VN"></span>Tiếng Việt</a></li>
        </ul>
    </div>
</div>

<h1 class="title login-text">Login</h1>

    <div class="rowlg msg-error" errCode="0" id="errmsg"></div>

<div class="rowlg">
    <input type="text" class="txt" placeholder="Username"  id="txtUserName" name="txtUserName" tabindex="1" />
    <i class="icon-user"></i>
</div>

<div class="rowlg">
    <input type="password" class="txt" placeholder="Password" id="txtPassWord" name="txtPassWord" tabindex="2" autocomplete="off" />
    <i class="icon-lock"></i>
</div>

<div class="rowlg checkbox">
    <label>
        <input name="chb-showpass" type="checkbox" id="chbShowPass" tabindex="3" /> 
        <span id="lbShowPass">Show password</span>
    </label>
</div>


<input type="hidden" name="browserSize" id="browserSize" value="" />
<div class="list-button">
    <input type="button" class="btnLogin" value="Login" id="btnLogin" tabindex="5"/>
</div>




                <input name="code" id="code" type="hidden" value="4577" />
                <input id="detecas-analysis" name="detecas-analysis" value="{}" type="hidden" />
            </form>
        </div>


        <script src="/assets/bundles/login.min.js?ver=180314001" type="text/javascript"></script>

        

<input id="ModelErrCode" name="ModelErrCode" type="hidden" value="0" />
<input id="ModelErrMsg" name="ModelErrMsg" type="hidden" value="" />
<input id="ModelLanguage" name="ModelLanguage" type="hidden" value="0" />
<input id="ModelIp" name="ModelIp" type="hidden" value="42.118.196.157" />
<input id="ModelUTMS" name="ModelUTMS" type="hidden" value="56E8B62076A5176E7274C928095C75" />
<input id="ModelDomain" name="ModelDomain" type="hidden" value="b88ag.com" />
<input id="ModelCaptcha" name="ModelCaptcha" type="hidden" value="4577" />
<input id="CommonAppSettingFpsActivator" name="CommonAppSettingFpsActivator" type="hidden" value="//sc.detecas.com/di/activator.ashx" />
<input id="RootUrl" name="RootUrl" type="hidden" value="/" />

<script type="text/javascript">
    var detecasAnalysis = document.getElementById("detecas-analysis");
    detecasAnalysis ? (detecasAnalysis.value = '{"startTime":1446686616296,"version":"0.0.0","enable":true}') : false;

    var _page = {
        errCode: 0,
        errMsg: '',
        language: 0,
        ip: '',
        __utms: '',
        domain: '',
        captcha: '',
        fpsActivator: ''
    };

    _page.errCode = document.getElementById("ModelErrCode").value;
    _page.errMsg = document.getElementById("ModelErrMsg").value;
    _page.language = document.getElementById("ModelLanguage").value;
    _page.ip = document.getElementById("ModelIp").value;
    _page.__utms = document.getElementById("ModelUTMS").value;
    _page.domain = document.getElementById("ModelDomain").value;
    _page.captcha = document.getElementById("ModelCaptcha").value;
    _page.fpsActivator = document.getElementById("CommonAppSettingFpsActivator").value;

    window.rootUrl = document.getElementById("RootUrl").value;


    $(function () {
        if (parseInt(_page.errCode) === -1) {
            $('#mainholder').css('display', 'none');
            $('#divLoading').css('display', 'block');
            $("body").css("background", "none");
            window.location.href = '/Customer/SignIn/Flow';
        }

        (function (json, base64) {

            function getDeviceId() {
                var diInput = document.getElementById("__di");
                var collectedDeviceInfo = base64.decode(diInput.value);
                collectedDeviceInfo = json.parse(collectedDeviceInfo);
                return collectedDeviceInfo.deviceId;
            }

            function addDevideIdElement(deviceId) {
                $("#formLogin").append('<input type="hidden" name="deviceId" id="deviceId" value="' + deviceId + '" />');
            }

            var completeTimeout = setTimeout(function () {
                try {
                    var deviceId = getDeviceId();
                    addDevideIdElement(deviceId);
                }
                catch (err) {
                    addDevideIdElement("N/A");
                    window.console.log("fps error = " + err);
                }
            }, 2000); // Wait 2000 miliseconds only

        })(Detecas.JSON, Detecas.Base64);
    });

    !function (e, t, a, c, n) {
        var s = t.createElement(a),
        o = t.getElementsByTagName(c)[0];
        s.async = true, s.defer = true, s.src = n, o.appendChild(s)
    }(window, document, "script", "body", document.getElementById("CommonAppSettingFpsActivator").value);


</script>


        

        

    <script>
      (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
      (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
      m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
      })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

      ga('create', 'UA-93265717-4', 'auto');
      ga('send', 'pageview');

    </script>


    <script type="text/javascript">
//<![CDATA[
(function() {
var _analytics_scr = document.createElement('script');
_analytics_scr.type = 'text/javascript'; _analytics_scr.async = true; _analytics_scr.src = '/_Incapsula_Resource?SWJIYLWA=719d34d31c8e3a6e6fffd425f7e032f3&ns=1&cb=1720171567';
var _analytics_elem = document.getElementsByTagName('script')[0]; _analytics_elem.parentNode.insertBefore(_analytics_scr, _analytics_elem);
})();
// ]]>
</script></body>
</html>
