# ViewBagExample

Bu proje, ASP.NET MVC kullanarak `ViewBag` ile bir listeyi `Controller`'dan `View`'a nasıl gönderebileceğinizi gösterir.

## Kodlar

### Controller ve View Kodları

```csharp
// Controllers/HomeController.cs
using System.Collections.Generic;
using System.Web.Mvc;

namespace ViewBagExample.Controllers
{
    public class HomeController : Controller
    {
        public ActionResult Index()
        {
            // Ürün listesi oluşturuluyor
            List<string> products = new List<string> { "Laptop", "Tablet", "Akıllı Telefon", "Kulaklık", "Klavye" };
            
            // ViewBag ile liste View'a gönderiliyor
            ViewBag.ProductList = products;
            
            return View();
        }
    }
}
```

```html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>ViewBag ile Liste Gönderme</title>
</head>
<body>
    <h2>Ürün Listesi</h2>
    
    <ul>
        @foreach (var product in ViewBag.ProductList)
        {
            <li>@product</li>
        }
    </ul>
</body>
</html>
```
# TempDataExample

Bu proje, ASP.NET MVC kullanarak `TempData` ile bir mesajı bir aksiyondan başka bir aksiyona yönlendirme (`redirect`) sonrasında nasıl gönderebileceğinizi gösterir.

## Kodlar

### Controller ve View Kodları

```csharp
// Controllers/AccountController.cs
using System.Web.Mvc;

namespace TempDataExample.Controllers
{
    public class AccountController : Controller
    {
        public ActionResult Submit()
        {
            // TempData kullanarak bir başarı mesajı gönderiyoruz
            TempData["SuccessMessage"] = "Kullanıcı başarıyla kaydedildi!";
            
            // Başka bir aksiyona yönlendirme yapıyoruz
            return RedirectToAction("Success");
        }

        public ActionResult Success()
        {
            return View();
        }
    }
}
```
```html
<!-- Views/Account/Success.cshtml -->
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>TempData ile Mesaj Gönderme</title>
</head>
<body>
    <h2>Sonuç</h2>
    
    <p>
        @if (TempData["SuccessMessage"] != null)
        {
            <strong>@TempData["SuccessMessage"]</strong>
        }
    </p>
</body>
</html>
```
# ViewDataExample

Bu proje, ASP.NET MVC kullanarak `ViewData` ile bir listeyi `Controller`'dan `View`'a nasıl gönderebileceğinizi gösterir.

## Kodlar

### Controller ve View Kodları

```csharp
// Controllers/ProductController.cs
using System.Collections.Generic;
using System.Web.Mvc;

namespace ViewDataExample.Controllers
{
    public class ProductController : Controller
    {
        public ActionResult Index()
        {
            // Ürün listesi oluşturuluyor
            List<string> products = new List<string> { "Bilgisayar", "Tablet", "Akıllı Telefon", "Kulaklık", "Klavye" };
            
            // ViewData ile liste View'a gönderiliyor
            ViewData["ProductList"] = products;
            
            return View();
        }
    }
}
```
```html
<!-- Views/Product/Index.cshtml -->
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>ViewData ile Liste Gönderme</title>
</head>
<body>
    <h2>Ürün Listesi</h2>
    
    <ul>
        @if (ViewData["ProductList"] != null)
        {
            foreach (var product in (List<string>)ViewData["ProductList"])
            {
                <li>@product</li>
            }
        }
    </ul>
</body>
</html>
```
