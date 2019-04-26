---
title: Advent of Code. Year 2015. Day 5
date: 2019-04-22T13:40:38.031Z
description: Solution to Advent of Code Year 2015 - Day 5
tags:
  - aoc-2015
---
## --- Day 5: Doesn't He Have Intern-Elves For This? ---

body

### Part 1

part1

```csharp
public string Part1(IEnumerable<string> input)
{
  bool HasThreeVowels(string str) => 
    Regex.Matches(str, @"[aeiou]").Count >= 3;

  bool HasDoubledLetter(string str) => 
    Regex.IsMatch(str, @"(\w)\1");

  bool ContainsNaughtyStrings(string str) => 
    Regex.IsMatch(str, @"ab|cd|pq|xy");

  bool IsNiceString(string str) =>
    HasThreeVowels(str)
    && HasDoubledLetter(str)
    && !ContainsNaughtyStrings(str);

  var niceStrings = input.Count(IsNiceString);
  return niceStrings.ToString();
}
```

### Part 2

part2

```csharp
public string Part2(IEnumerable<string> input)
{
  bool HasPair(string str) => 
    Regex.IsMatch(str, @"(\w{2}).*\1");

  bool HasDuplicate(string str) => 
    Regex.IsMatch(str, @"(\w).\1");

  bool IsNiceString(string str) =>
    HasDuplicate(str)
    && HasPair(str);

  var niceStrings = input.Count(IsNiceString);
  return niceStrings.ToString();
}
```

- - -

Links:

* [Puzzle](https://adventofcode.com/2015/day/5)
* [Solution](https://github.com/PDmatrix/advent-of-code/tree/master/CSharp/Solutions/2015/5)
