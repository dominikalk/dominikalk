```C#
using System;
using System.Collections.Generic;
using Microsoft.AspNetCore.Mvc;

public class DominikService : IDominikService
{
  private readonly ILogger<DominikService> _logger;
  
  private readonly string name = "Dominik Alkhovik";
  private readonly string role = "Full-Stack Developer at Spike Global";
  private readonly string degree = "First Class Computer Science BSc with Honours";
  private readonly string university = "Cardiff University";
  private readonly List<string> stack = new List<string>()
    {"ASP.NET", "EF Core", "MSTest", "SignalR", "React", 
      "React Native", "Redux", "SASS", "TailwindCSS", "GraphQL"};
  private readonly List<string> languages = new List<string>()
    {"C#", "TypeScript", "JavaScript", "Java", "Python", "HTML", "CSS"};
  
  public DominikService(ILogger<DominikService> logger)
  {
    _logger = logger;
  }
  
  public string GetCoverLetter()
  {
    string introduction = $"Hi, my name is {name} and I am a {role}. ";
    string studies = $"I have a {degree} from {university}. ";
    string stackInfo = $"I mainly work with {GetSeparatedList(stack)} ";
    string languagesInfo = $"and I'm also proficient with {GetSeparatedList(languages)}. ";
    
    _logger.LogInformation("Cover Letter Generated");
    return introduction + studies + stackInfo + languagesInfo;
  }
  
  private string GetSeparatedList(List<string> items)
  {
    if (items.Count == 0)
    {
      return "";
    } else if (items.Count == 1)
    {
      return items[0];
    }
    
    string last = items[items.Count - 1];
    items.RemoveAt(items.Count - 1);
    return String.Join(", ", items) + $" and {last}";
  }
  
  public IActionResult GetNegatives()
  {
    return NotFound();
  } 
}
```
