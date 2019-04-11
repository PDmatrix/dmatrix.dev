---
title: Advent of Code. Year 2015. Day 4
date: 2019-04-08T22:42:51.075Z
description: Solution to Advent of Code Year 2015 - Day 4
tags:
  - aoc-2015
---
## --- Day 4: The Ideal Stocking Stuffer ---

Today, we are going to mine some AdventCoins. For this we need to find MD5 hashes which, in hexadecimal, start with at least five zeroes. The input to the MD5 hash is some secret key followed by a number in decimal. We need to find the lowest number that produces such hash.

### Part 1

In order to get hash from string I took function from [StackOverflow](https://stackoverflow.com/questions/11454004/calculate-a-md5-hash-from-a-string)

```
private static string CreateMd5(string input)
{
  using (var md5 = MD5.Create())
  {
    var inputBytes = Encoding.ASCII.GetBytes(input);
    var hashBytes = md5.ComputeHash(inputBytes);
    var sb = new StringBuilder();
    foreach (var hashByte in hashBytes)
    {
      sb.Append(hashByte.ToString("X2"));
    }

    return sb.ToString();
  }
}
```

### Part 2

part2

```csharp
code
```

- - -

Links:

* [Puzzle](https://adventofcode.com/2015/day/4)
* [Solution](https://github.com/PDmatrix/advent-of-code/tree/master/CSharp/Solutions/2015/4)
