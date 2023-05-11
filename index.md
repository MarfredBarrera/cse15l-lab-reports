# Lab Report 3

This lab report will explore the possible uses of the ```grep``` command and its different command line options. By default, grep will search a given file for any uses of a given string and return the line where the string is found.

1. ```grep -i [PATTERN] [FILE]```

This command line option ignores case distinctions. I found this using (https://en.wikibooks.org/wiki/Grep)

Example using ./technical/government/Media/Helping_Hands.txt

```
$ grep -i "LEGAL" Helping_Hands.txt
```

```
Legal assistance for battered women is hard to come by. But it
residents, who can access free legal aid locally from West Texas
Legal Services.
programs are the working poor, who don't qualify for free legal
[cs15lsp23qz@ieng6-201]:Media:458$ grep -i "LEGAL" Helping_Hands.txt
Legal assistance for battered women is hard to come by. But it
residents, who can access free legal aid locally from West Texas
Legal Services.
programs are the working poor, who don't qualify for free legal
```
You can see that the pattern ```grep``` is looking for is "LEGAL". The exact string "LEGAL" does not show up in a grep search without -i, but all uses of "LEGAL" in the file Helping_Hands.txt are shown with ```grep -i```

Here is another example using ./technical/government/Media/Ginny_Kilgore.txt

```
$ grep -i 'law' Ginny_Kilgore.txt
```

```
University of Mississippi School of Law's 2002 Public Service
Kilgore's honor and hosted by law school Dean Samuel M. Davis, who
few years teaching, Kilgore enrolled at the UM law school. Upon
graduation in 1975, she entered private law practice in Oxford,
Since 1990, she has worked in the Administrative Law Unit and
Resource Development, and directed the Elder Law Project, serving
She also is an adjunct professor in the UM law school's Civil
Law Clinic. She held a similar post a few years ago in the school's
Elder Law Clinic.
Mississippi Bar Association with its 2000 Legal Services Lawyer of
Previous recipients of the law school's Public Service Award are
other UM law alumni: Forest attorney Constance Slaughter-Harvey;
```
Here, grep shows every line with the string 'law' without case distinction.
This option could be useful if you want to look for every instance of a word appearing in a text file, including if the word is capitalized in the start of a sentence. 

2. ```grep -m [NUM] [PATTERN] [FILE]```

The comman grep -m will count and print up to NUM lines matching the specified pattern

Example using ./technical/government/Alcohol_Problems/Session4-PDF.txt
```
$ grep -m 5 'alcohol' Session4-PDF.txt
```

```
Individuals who may benefit from alcohol counseling are often
unaware of their need for treatment. The provision of alcohol
more intractable stages of alcoholism. Finally, such interventions
As proven alcohol interventions emerge, a systematic effort is
that have limited the provision of alcohol intervention and
```

Here, the first 5 lines that contain the string 'alcohol' are shown. This could be useful to find the first few occurances of a string in a file.

Here is another examples using ./technical/government/About_LSC/State_Planning_Report.txt
```
$ grep -m 20 'community' State_Planning_Report.txt
```

```
building of the community is directed--the creation and maintenance
in every state of a "state justice community" collaborating on the
This Report describes progress that the legal services community
building a justice community capable of responding to the full
process. In a few states, a fully developed state justice community
developed key justice community institutions whose significant
increase the capacities of three community-based organizations.
with an active period within California's justice community. The
community. The first priority of the Commission was resource
services community, but despite signs of chronic weakness in two
assistance to the low-income community throughout the
in the state justice community in Colorado has always been
coordinated state justice community in Colorado.
programs. The results were reported to the equal justice community
internet access to community education materials beyond the current
community education site for immigrant advocacy organizations.
region, to be developed in 2001. A region-wide community economic
community, social service agencies, government agencies, civil
government agencies and community leaders to promote holistic,
planners develop ways to involve more clients and community
```

In this result, the first 20 lines that mention the string 'community' are shown. This could be useful if you want ```grep``` to stop looking for searches once you reach the amount of mentions you are interested in.

3.  ```grep -c [PATTERN] [FILE]```

The ```grep -c``` command will only print a count of how many matchin lines there are in a file.

Here is an example using ./technical/biomed/1471-213X-3-4.txt

```
$ grep -c 'RNA' 1471-213X-3-4.txt
```

``` 
16
```

As seen, grep -c does not print the matching lines themselves, only the number of lines that match the specified pattern. In file 1471-213X-3-4.txt, there are 16 lines that mention 'RNA'. 

Here is another example of ``` grep -c ``` using ./technical/biomed/1471-2253-2-5.txt

```
$ grep -c 'PBPK' 1471-2253-2-5.txt
```

```
35
```

Again, no lines are printed using grep -c, only the count of matching lines are printed. This command would be useful if you want to quickly search for how many lines contain a specific string, even if it appears multiple times in a single line.

4. ``` grep -o [PATTERN] [FILE] ```

```grep -o``` shows only the part of the line matching the pattern.

Here is an example using ./technical/911report/preface.txt

```
$ grep -o 'United States' preface.txt
```

```
United States
United States
United States
United States
```

Here, ```grep -o``` shows only the parts of the file matching the specified pattern. However, this includes when the pattern occurs multiple times in one line. For example,

```
$ grep -c 'United States' preface.txt
```

returns
```
3
```
because the string 'United States' appears in 3 lines. However, grep -o will show 4 instances of 'United States' because the pattern is mentioned twice in one line.
This could be used to count the total amount of times a pattern appears in a file.

Here is another examples using ./technical/911report/chapter-1.txt
```
$ grep -o 'NORAD' chapter-1.txt
```

```
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
NORAD
```

Here, the pattern 'NORAD' is found within chapter-1.txt many times. This would be a useful instance of using grep -o in conjunction with another command like grep -c or wc to quickly count the total amount of instances of a specific pattern inside a file.
