# Lab Report 3

## Part 1: Researching Commands

> Note: when using these commands, use bash or make sure to use a linux-based terminal in order for them to work properly.
>
> Note: Pressing ```q``` after entering the command will cause the contents of the file to be cleared from the command-line.
> 
>Note: The examples shown below were done by using the files and directories in ```./technical```.

Using the ```less``` command, there are four command-line options to use it.

---
One way to use the ```less``` command is by using the ```-N``` option.


Shown below are two examples of using the ```-N``` option for the ```less``` command.

> Before pressing enter with command:
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -N technical/911report/chapter-10.txt
```
> After pressing enter with command: (Some of the output is shortened for simplicity, but the concept can still be understood.)
```
      1 
      2
      3
      4             WARTIME
      5             After the attacks had occurred, while crisis managers were still sorting out a number
      6                 of unnerving false alarms, Air Force One flew to Barksdale Air Force Base in
      7                 Louisiana. One of these alarms was of a reported threat against Air Force One
      8                 itself, a threat eventually run down to a misunderstood communication in the hectic
      9                 White House Situation Room that morning.
     10
technical/911report/chapter-10.txt
```

Based on the example above, using the ```-N``` option with the ```less``` command along with a given file, in this case ```chapter-10.txt``` from the technical/911report directory, will print out a portion of the lines of content from the file with line numbers to the left of them.  Repeatedly pressing enter will keep printing out the contents of the file until it has reached the end of the file, as depicted below.

>Before pressing enter with command:
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -N technical/biomed/ar149.txt
```

>After pressing enter with command: (Some of the output is shortened for simplicity, but the concept can still be understood.)
```
      1 
      2
      3
      4
      5         Introduction
      6         The synovial tissue in rheumatoid arthritis (RA)
      7         contains synovial fibroblasts and stromal cells as well as
      8         macrophages. Synovial stromal cells and fibroblasts are
      9         thought to proliferate
     10         in situ [ 1]. On the contrary,
technical/biomed/ar149.txt
```
>After pressing enter repeatedly until the end of the file is reached. (Some of the output is shortened for simplicity, but the concept can still be understood.)
```
    460         = peripheral blood mononuclear cells; PE = phycoerythrin;RA
    461         = rheumatoid arthritis; RANTES = regulated upon activation,
    462         normal T cell expressed and secreted; RT-PCR = reverse
    463         transcriptase-polymerasechain reaction; SCL = stromal cell
    464         line; SRBC = sheep red blood cells; TNF-α = tumor necrosis
    465         factor-α.
    466
    467
    468
(END)
```
Based on the second example above, the same command and option is used, but in the final code block, I pressed the enter key until I reached the end, ```(END)``` was printed out.  This is useful for tracking which line that a specific piece of content is at.

---
Another way to use ```less``` is with the ```-X``` option.

Shown below are two examples of using the ```-X``` option for the ```less``` command.

> Entering ```less``` command with ```-X``` option: (Some of the output is shortened for simplicity, but the concept can still be understood.)
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -X technical/biomed/ar140.txt




        Introduction
        RA is an autoimmune disease that is characterized by
        persistent local and systemic inflammation [ 1, 2, 3].
        Aggressive forms of RA are thought to be driven by
        T-lymphocyte activity, leading to the rapid erosion of bone
        and cartilage. Activated Tm are found in the perivascular
        regions of the inflamed synovium, and T cells accumulate in
        the synovial fluid [ 4, 5, 6]. It appears that memory T

Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$
```

Using the ```-X``` option for the ```less``` command will print out a portion of contents from the file, but this time without numbers, and when ```q``` is entered, the contents will remain on the screen compared to the ```-N``` option where it clears the screeen.


> Note: the code block below shows the command with the command-line option being entered
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -X technical/plos/pmed.0020015.txt




        Introduction
```
> Note: the code block below shows the behavior of the command-line option once the end of the file has been reached using the ```less``` command
```
        The likelihood that mechanisms other than anticapsular antibody confer immunity to
        pneumococcal disease has important implications with respect to vaccine design. As
        experience with conjugate pneumococcal vaccines in children unfolds, it is becoming
        increasingly clear that such a strategy suffers from several limitations, including the
        possibility of serotype replacement (already confirmed in several clinical trials), a
        modest effect on nasopharyngeal colonization, limited serotype coverage, cost, and
        difficulties in production that have led to shortages since licensure. A better
        understanding of the mechanisms that underlie natural immunity to pneumococcus could pave
        the way for the development of more effective, species-specific pneumococcal vaccines.



(END)
```

The code blocks above show the second example with similar behavior as the first example, but here enter was pressed repeatedly until the end of the file was reached, as indicated by the ```(END)``` printed out after the end of the file.

---
A third way to use ```less``` is by using the ```-s``` option.

Shown below are two examples of using the ```-s``` option for the ```less``` command.

> Before pressing enter with command: 
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -s technical/911report/chapter-1.txt
```
> After pressing enter with command: (Shortened for simplicity, but concept can still be understood)
```
 The details of what happened on the morning of September 11 are complex, but they play out a simple theme. NORAD and the FAA were unprepared for the type of attacks launched against the United States on September 11, 2001. They struggled, under difficult circumstances, to improvise a homeland defense against an unprecedented challenge they had never before encountered and had never trained to meet.

    At 10:02 that morning, an assistant to the mission crew commander at NORAD's Northeast Air Defense Sector in Rome, New York, was working with his colleagues on the floor of the command center. In a brief moment of reflection, he was recorded remarking that "This is a new type of war."

    He was, and is, right. But the conflict did not begin on 9/11. It had been publicly declared years earlier, most notably in a declaration faxed early in 1998 to an Arabic-language newspaper in London. Few Americans had noticed it. The fax had been sent from thousands of miles away by the followers of a Saudi exile gathered in one of the most remote and impoverished countries on earth.
```

The code blocks above show the ```-s``` option being used for the ```less``` command.  The behavior of the ```-s``` option is that it prints out the contents of the file but it reduces the amount of blank lines.

> Before pressing enter with command:
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -s technical/biomed/rr74.txt
```
> After pressing enter with command: (Shortened for simplicity)
```
        17, 18] suggesting an increase in lung eNOS and iNOS
        levels. We therefore hypothesized that NOS isoforms are
        upregulated following hypoxia and that this may account for
        the increased susceptibility to hypoxic pulmonary
        hypertension in mice that lack eNOS [ 9, 12]. In the
        present study we exposed wild-type mice to severe hypobaric
        hypoxia from birth and measured NOS mRNA and protein
        levels. We then compared the findings with localization of
technical/biomed/rr74.txt
```
The example above shows similar behavior with a different file from the ```./technical``` directory, but there are no blank spaces found so the file is printed out as is. 

> Note: in both examples above, ```q``` was entered, and the contents of the file were cleared from the screen.

---
Finally, another way to use the ```less`` command is with the ```-M``` option.

Shown below are two examples of using the ```-M``` option for the ```less``` command.

> Before pressing enter with command:
```
Michael MINGW64 ~/Documents/GitHub/docsearch (main)
$ less -M technical/government/Media/pro_bono_efforts.txt
```
> After pressing enter with command:
```
Attorneys step up pro bono efforts
As the city's need for services grows, area's firms urge
partners to volunteer their time.

By Russ Rizzo
August 5, 2002
INDIANAPOLIS- Four years ago, the state Supreme Court asked law
firms to address a growing problem: Not enough lawyers were
donating time for pro bono work, and thousands of people were left
with no legal help in civil cases.
This year, two of the state's legal giants responded.
Barnes and Thornburg, the state's largest firm, asked all of its
lawyers to volunteer at least 25 hours a year helping low-income
people on the clock.
The firm's 335 lawyers now can bill up to 50 hours of pro bono
work, which is free legal service for people who cannot afford
it.
technical/government/Media/pro_bono_efforts.txt lines 1-41/76 53%
```

In the code block above, the ```-M``` option will print out a portion of the contents of the file, just like with the ```-N``` option, but this time there are no line numbers and pressing enter repeatedly will not do anything. 

>2nd example of using ```-M``` option: (Shortened for simplicity but the concept can still be understood.)
```
        2005): “To leave the world a bit better, whether by a healthy child, a garden patch or a
        redeemed social condition; to know even one life breathed easier because you have lived;
        this is to have succeeded [as a whistleblower].”



technical/plos/pmed.0020281.txt lines 1-40/40 (END)
```

In the code block above, the ```-M``` option will print out the contents of the file if the file is short enough, as depicted above by the last line ```technical/plos/pmed.0020281.txt lines 1-40/40 (END)```.
