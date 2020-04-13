# MVNet
- Supports a variety of proxies (Http/s, Socks4, Socks4a, Socks5).
- Supports TLS/SSL (tls1.0, tls1.1, tls1.2, tls1.3, SSL3.0).

## Features
#### HTTP Methods
- GET
- POST

#### Using
```csharp
using MVNet;

try
{
    var hr = new HttpRequest();
    var res = hr.Get("https://api.ipify.org?format=json");
    if (res.IsOk)
    {
        Console.WriteLine(res.Content);
    }
    else
    {
        Console.WriteLine(res.StatusCode);
    }
}
catch (HttpException ex)
{
    Console.WriteLine(ex.Message);
}
```

#### SSL(ON/OFF)
```csharp
//ON
var hr = new HttpRequest()
{
    Ssl = true
};

//OFF
var hr = new HttpRequest()
{
    Ssl = false
};
```

#### Set Proxy
````csharp
ProxyClient pc = new ProxyClient(ProxyType.Http, "127.0.0.1:80");
//Or
ProxyClient pc = new ProxyClient(ProxyType.Http, "127.0.0.1", 80);
//Or
ProxyClient pc = new ProxyClient(ProxyType.Http, "127.0.0.1", 80, "User", "Pass");

var hr = new HttpRequest()
{
    UseProxy = true,
    ProxyClient = pc
};
````

#### Set Cookie
```csharp
CookieDictionary cookie = new CookieDictionary();
cookie.Add("name1", "value1");
cookie.Add("name2", "value2");

var hr = new HttpRequest()
{
    Cookies = cookie
};

//Or

var hr = new HttpRequest();
hr.Cookies.Add("name1", "value1");
hr.Cookies.Add("name2", "value2");
```

#### Set Header
```csharp
HeaderDictionary header = new HeaderDictionary();
header.Add("name1", "value1");
header.Add("name2", "value2");

var hr = new HttpRequest()
{
    Headers = header
};

//Or

var hr = new HttpRequest();
hr.Headers.Add("name1", "value1");
hr.Headers.Add("name2", "value2");
```

#### Get Cookies
````csharp
string cookie;
res.Cookies.TryGetValue("name", out cookie);
````

#### Get Header
````csharp
string header;
res.Headers.TryGetValue("name", out cookie);
````
