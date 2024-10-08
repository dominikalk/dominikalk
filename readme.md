```C#
using System;
using System.Collections.Generic;
using Microsoft.AspNetCore.Mvc;

public class DominikService : IDominikService
{
  private readonly ILogger<DominikService> _logger;
  
  private readonly string name = "Dominik Alkhovik";
  private readonly string role = "Platform Developer at UrbanThings";
  private readonly string degree = "First Class Computer Science BSc with Honours";
  private readonly string university = "Cardiff University";
  private readonly IEnumerable<string> stack =
    ["ASP.NET", "EF Core", "MSTest", "SignalR", "React",
    "React Native", "Redux", "SASS", "TailwindCSS", "GraphQL"];
  private readonly IEnumerable<string> languages =
    ["C#", "TypeScript", "JavaScript", "Java", "Python", "HTML", "CSS"];
  
  public DominikService(ILogger<DominikService> logger)
  {
    _logger = logger;
  }
  
  public string GetCoverLetter()
  {
    string introduction = $"Hi, my name is {name} and I am a {role}. ";
    string studies = $"I have a {degree} from {university}. ";
    string stackInfo = $"I mainly work with {String.Join(", ", stack)} ";
    string languagesInfo = $"and I'm also proficient with {String.Join(", ", languages)}. ";
    
    _logger.LogInformation("Cover Letter Generated");
    return introduction + studies + stackInfo + languagesInfo;
  }
  
  public IActionResult GetNegatives()
  {
    return NotFound();
  } 
}
```
