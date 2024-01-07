---
tags:
  - csharp
---
# Creating and Adding References to Assemblies

![[Pasted image 20240107135247.png]]

![[Pasted image 20240107135511.png]]
```c#
using System.Net;

namespace MyCodeLibrary
{
    public class Scrape
    {
        public string ScrapeWebPage(string url)
        {
            return GetWebPage(url);
        }

        public string ScrapWebpage(string url, string filepath)
        {
            string html = GetWebPage(url);
            File.WriteAllText(filepath, html);
            return html;
        }

        private string GetWebPage(string url)
        {
            WebClient client = new WebClient();
            return client.DownloadString(url);
        }
    }
}
```
* Building a Custom Class Library





