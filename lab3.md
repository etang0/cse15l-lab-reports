# Lab Report 2
Given a string and a txt file, grep will return all the lines in the file matching that string. In order to grep search the whole `./technical` folder, we need a list of all the filepaths ending in `.txt`. This can be done with the command `find technical "*.txt" > technical_files.txt`. 
`xargs`, `grep`, and `technical_files.txt` can now be used in combination to search every txt file in `./technical`.
All of these options were found with `man grep`.

## `grep -A num`
By default, grep will return the only the line containing the match. This option tells grep to return additional lines after the matching line. This is useful for getting more context without needing to open the file. Similary, `grep -B num` return additional lines in front, and `grep -C num` returns additional lines on both sides.

Example 1:
```
xargs grep -A 1 "shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020440.txt-        tomato plant and a tree are remarkably similar,” (Figure 1) says Gillooly, who joined
--
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020276.txt-        and Brunner 2002). In species studied to date, host defense appears to be mediated by
...
```

Example 2:
```
edwardtang@Silver-Surfer docsearch % xargs grep -A 2 "shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020440.txt-        tomato plant and a tree are remarkably similar,” (Figure 1) says Gillooly, who joined
technical/plos/journal.pbio.0020440.txt-        Brown's group as a grad student to work on the temperature question. It's not yet clear
--
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020276.txt-        and Brunner 2002). In species studied to date, host defense appears to be mediated by
technical/plos/journal.pbio.0020276.txt-        homologous proteins. Taken together, these findings suggest that the regulatory mechanisms
...
```