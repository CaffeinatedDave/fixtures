# Contribution Guidelines

Firstly, Thanks for taking the time to consider contributing to this repo, and for reading this document.

### Modification

Notice a fixture/time change? Update the "date" or "time" fields to the new time/date.

Adding some scores? Add a scoreH and scoreA element to the JSON object with the score. If it goes to extra time/overtime etc - use the scoreHOT and/or scoreAOT to indicate the final score after this period is over.

Example
`{"date":"Mon 6 Aug 2018","time":"18:00","home":"Team A","away":"Team B","scoreH":3,"scoreA":3,"scoreHOT":4}`

This gives a final score of 4-3 to the home side, when the match ended 3-3 after regulation time.

### Creation

Check out the existing examples of fixture lists to see how to craft the JSON file. The file format should be [Competition][Date].json, for example EIHL1819 for the Elite League season for 2018-19.

The format of the file will be:

```
{
  "meta": <any>        <-- General object indicating things like maintainer, author, lifetime relevance etc. Not used anywhere.
  "teams": {           <-- Object using the team abbreviation as the key
    "KEY": {             <-- Team specific object
      "name": <string>     <-- Team name to be displayed (mandatory)
      "logo": <string>     <-- File name of team logo (optional - defaults to [KEY].png)
    },
    ..
  } 
  "competitions: {     <-- Object of competitions with competition abbreviation as key
    "KEY": {             <-- Competition object
      "name": <string>     <-- Name of competition (mandatory)
    },
    ..
  }
  "fixtures": [        <-- List of fixtures split by competition
    {
      "competition": <string> <-- competition abbreviation: Must exist in competitions object above
      "fixtures": [           <-- list of actual fixtures for this competition
        {
          "date":             <-- Date the fixture takes place (mandatory)
          "time":             <-- Time the fixture starts (optional)
          "home":             <-- Home team abbreviation. Must exist in teams object above (mandatory)
          "away":             <-- Away team abbreviation. Must exist in teams object above (mandatory)
          "scoreH":           <-- Home score (optional)
          "scoreA":           <-- Away score (optional)
          "scoreHOT":         <-- Home score after overtime (optional)
          "scoreAOT":         <-- Away score after overtime (optional)
        }
        ..
      ]
    }
    ..
  ]
```

Ensure that for each team in the teams object, a relevant image has been added to the `/imgs` directory and mapped if necessary. BLANK.png is acceptable, but needs to be mapped.

Additions to metadata (and therefore the dropdown on the page) are at my personal discretion: Your Sunday League schedule probably won't make it... Please leave this file be, and I'll update this part manually when I review the pull request. You'll still be able to access the fixtures at `https://caffeinateddave.xyz/fixtures?fixtures=YOURFILENAME`

It's perfectly fine to just upload fixtures and not track scores here.

### Validation

Please take the time to run the modified/new JSON file through https://jsonlint.com/. It's incredibly easy to miss a comma or bracket when creating these files, and this will save headaches in the long run.

### Removal

TBC - probably 6-12 months after the last fixture on the list.
