# Lab Report 3
Given a string and a txt file, `grep` will return all the lines in the file matching that string. In order to `grep` search the whole `./technical` folder, we need a list of all the filepaths ending in `.txt`. This can be done with the command  
`find technical "*.txt" > technical_files.txt`.  
`xargs`, `grep`, and `technical_files.txt` can now be used in combination to search every txt file in `./technical`.

## 1. `grep -A num`
By default, `grep` will return the only the line containing the match. This option tells `grep` to return additional lines after the matching line. This is useful for getting more context without needing to open the file. Similary, `grep -B num` returns additional lines in front, and `grep -C num` returns additional lines on both sides.  
Source: `man grep`.

Adding 1 additional line after each search result:
```
xargs `grep` -A 1 "shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020440.txt-        tomato plant and a tree are remarkably similar,” (Figure 1) says Gillooly, who joined
--
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020276.txt-        and Brunner 2002). In species studied to date, host defense appears to be mediated by
...
```

Adding 2 additional lines after each search result:
```
edwardtang@Silver-Surfer docsearch % xargs `grep` -A 2 "shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020440.txt-        tomato plant and a tree are remarkably similar,” (Figure 1) says Gillooly, who joined
technical/plos/journal.pbio.0020440.txt-        Brown's group as a grad student to work on the temperature question. It's not yet clear
--
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020276.txt-        and Brunner 2002). In species studied to date, host defense appears to be mediated by
technical/plos/journal.pbio.0020276.txt-        homologous proteins. Taken together, these findings suggest that the regulatory mechanisms
...
```

## 2. `grep -E`
Chaining different patterns allows us to be more specific in our searches. However, it can be difficult to make complex searches with normal `grep`. This option makes it easier to build those patterns by enabling operators.  
Source: [thegeekstuff.com](https://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/).

Searching for lines with "wolf" OR "shark":
```
xargs `grep` -E "wolf|shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020262.txt:        from Chuy Aceves, who has hypertrichosis and looks like the original Hollywood wolfman but
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020113.txt:        and wolf populations brought to the brink of extinction swordfish and sharks are the
technical/plos/journal.pbio.0020113.txt:        more than 90% of large predatory fishes, such as marlin, sharks, and rays.
technical/plos/journal.pbio.0020113.txt:        Despite the controversy, most agree that the large predators, particularly sharks,
technical/biomed/1472-6785-1-5.txt:        wolf predation, and density dependence on the intrinsic
technical/biomed/1472-6785-1-5.txt:        series, the most parsimonious ecological model of wolf
technical/biomed/1472-6785-1-5.txt:        influence of winter climate in wolf-moose interactions [ 19
technical/biomed/1472-6785-1-5.txt:        ] , of the roles of wolf predation and density dependence
...
```

Searching for lines with "wolf" AND "shark":
```
xargs `grep` -E "wolf.*shark" < technical_files.txt
technical/plos/journal.pbio.0020113.txt:        and wolf populations brought to the brink of extinction swordfish and sharks are the
```
## 3. `grep --include`
The txt files in `./technical` are organized in several levels of subfolders. This options allows us to limit search the search to only one of those folders. `--exclude` works the opposite way.  
Source: `man grep`.

Searching for lines with "shark" and the filepath must contain `biomed`:
```
xargs `grep` --include "*biomed*" "shark" < technical_files.txt
technical/biomed/ar615.txt:          assay using purified shark chondroitin sulfate (Sigma
```

Searching for lines with "shark" and the filepath must contain `plos`:
```
xargs `grep` --include "*plos*" "shark" < technical_files.txt
technical/plos/journal.pbio.0020440.txt:        animals. “When you correct for size and temperature, the metabolic rates of a shark, a
technical/plos/journal.pbio.0020276.txt:        also been found in mice, sharks, nematodes, and plants (e.g., Pujol et al. 2001; Nurnberger
technical/plos/journal.pbio.0020113.txt:        and wolf populations brought to the brink of extinction swordfish and sharks are the
technical/plos/journal.pbio.0020113.txt:        more than 90% of large predatory fishes, such as marlin, sharks, and rays.
technical/plos/journal.pbio.0020113.txt:        Despite the controversy, most agree that the large predators, particularly sharks,
```

## 4. `grep -i`
This makes the search pattern not case-sensitive.  
Source: [warp.dev](https://www.warp.dev/terminus/make-grep-case-insensitive#:~:text=To%20recap%2C%20the%20grep%20command,or%20—ignore%2Dcase%20flag.)

Searching for "laden" without case-sensitivity:
```
xargs `grep` -i "laden" < technical_files.txt
technical/plos/pmed.0020060.txt:        luxuriant, larvae-laden hair while they were at it). Archaeologists have braved curses and
technical/plos/journal.pbio.0020400.txt:        glutathionylated in vitro (Hausladen et al. 1996; Kim et al. 2002), but the in vivo
...
technical/911report/chapter-2.txt:            On the morning of August 7, the bomb-laden trucks drove into the embassies roughly
technical/911report/chapter-6.txt:                to resolve the Bin Laden problem at the earliest possible time." But Zinni came back
technical/911report/chapter-6.txt:                nine months later, on October 12,2000, al Qaeda operatives in a small boat laden
...
```

Searching for "jesus" without case-sensitivity:
```
xargs `grep` -i "jesus" < technical_files.txt
technical/biomed/1471-2407-3-14.txt:        In 1847, members of the Church of Jesus Christ of
technical/911report/chapter-13.3.txt:            78. See Tom Mangold, Cold Warrior: James Jesus Angleton, the CIA's Master Spy Hunter
technical/911report/chapter-3.txt:                James Jesus Angleton, who headed counterintelligence in the CIA until the early
technical/911report/chapter-2.txt:                from the one and only God, the God of Abraham and of Jesus. These revelations,
technical/911report/chapter-2.txt:                from Abraham through Jesus, complete God's message to humanity. The Hadith, which
```