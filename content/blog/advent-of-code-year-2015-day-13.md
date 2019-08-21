---
title: Advent of Code. Year 2015. Day 13
date: 2019-08-20T09:45:10.517Z
description: Solution to Advent of Code Year 2015 - Day 13
tags:
  - aoc-2015
---
## --- Day 13: Knights of the Dinner Table ---

In today's puzzle, we need to find optimal seating arrangement for a loving (hating) family.

### Part 1

In the first part we need to calculate get the right seat arrangement where total happiness would be the greatest. First, we need to get all the guests from the input.

```csharp
private static IEnumerable<string> GetGuests(IEnumerable<string> lines)
{
  const string pattern =
    @"(?<who>\w+) would (lose|gain) (\d+?) happiness units by sitting next to (?<with>\w+)";
  var res = new List<string>();
  foreach (var line in lines)
  {
    var match = Regex.Match(line, pattern);
    res.Add(match.Groups["who"].Value);
    res.Add(match.Groups["with"].Value);
  }

  return res.Distinct();
}
```

After that, we need to somehow represent units of happiness of all guests. I decided to use `Dictionary` where key is a guest name and the value is another `Dictionary` where stored other guests with units of happiness, e.g:

```json
{
  "Alice": {
    "Bob": 54,
    "David": 0
  },
  "Bob": {
    "Alice": 83,
    "David": -25
  },
  "David": {
    "Alice": -60,
    "Bob": -90
  }
}
```

Here's the code for this:

```csharp
private static Dictionary<string, Dictionary<string, int>> GetUnits(IEnumerable<string> lines, bool withMe = false)
{
  const string pattern = 
    @"(?<who>\w+) would (?<what>lose|gain) (?<by>\d+?) happiness units by sitting next to (?<with>\w+)";
  var res = new Dictionary<string, Dictionary<string, int>>();
  foreach (var line in lines)
  {
    var match = Regex.Match(line, pattern);
    var firstGuest = match.Groups["who"].Value;
    if (!res.ContainsKey(firstGuest))
    {
      res[firstGuest] = new Dictionary<string, int>();
    }

    var secondGuest = match.Groups["with"].Value;
    if (!res.ContainsKey(secondGuest))
    {
      res[secondGuest] = new Dictionary<string, int>();
    }

    res[firstGuest][secondGuest] =
      match.Groups["what"].Value == "lose"
        ? -int.Parse(match.Groups["by"].Value)
        : int.Parse(match.Groups["by"].Value);
    if (withMe)
      res[firstGuest]["Me"] = 0;
  }

  return res;
}
```

 .First, we need to create permutations of all guests. To do that we can use function from the [ninth day](/advent-of-code-year-2015-day-9).

### Part 2

desc

```csharp
code
```

- - -

Links:

* [Puzzle](https://adventofcode.com/2015/day/13)
* [Solution](https://github.com/PDmatrix/advent-of-code/tree/master/CSharp/Solutions/2015/13)
