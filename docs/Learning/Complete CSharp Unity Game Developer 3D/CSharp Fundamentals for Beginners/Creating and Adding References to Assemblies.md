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

```c#

using MyCodeLibrary;

namespace Program
{
    class Program
    {
        static void Main(string[] args)
        {
            Scrape myScrape = new Scrape();
            string value = myScrape.ScrapeWebPage("http://google.com");
            Console.WriteLine(value);
            Console.ReadLine();
        }
    }
}
```
* Using that Custom Class Library within another application







