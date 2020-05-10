```javascript
/**
 * [regGetCookie description]
 * @author Hackshen
 * @email  hackshen.com@gmail.com
 * @param  key [需要获取的Key]
 */
function getCookie(name) {
    if(document.cookie.length > 0) {
        var cookies = document.cookie.replace(/&/g, ';');
        c_start = cookies.indexOf(name + "=");
        if(c_start != -1) {
            c_start = c_start + name.length + 1;
            c_end = cookies.indexOf(";", c_start);
            if(c_end == -1) c_end = cookies.length;
            return decodeURI(cookies.substring(c_start, c_end));
        }
    }
    return "";
}

/**
 * [regGetCookie description]
 * @author Hackshen
 * @email  hackshen.com@gmail.com
 * @param  key [需要获取的Key]
 */
function regGetCookie(key) {
    var cookie = document.cookie;
    if (cookie.indexOf(key) === -1) return '';
    var reg = new RegExp('.*([^;&]*' + key + '=)(.*?)([;&]|$).*');
    return cookie.replace(reg,'$2')
}

/**
 * [encryptPhone description]
 * @author Hackshen
 * @email  hackshen.com@gmail.com
 * @param  num [传入的手机号]
 */
function regPhone(num){
    if(!num) return;
    return num.replace(/^(\d{3})(\d{4})(\d+)/, '$1$2****')
}


```
