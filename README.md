# .NET-Web-Course-Notes

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

<!-- Views/Home/Index.cshtml -->
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
