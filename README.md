# 120b_prepatory_scripts

This repository hosts the wonderful `prepare_files` script. This script will take
a directory full of lab exercises (so a directory with files like `ex1.c`, `ex2.c`,
`part3.c`, etc.) and rename them properly according to the lab guidelines. It
will also prepend the header text to every C file (filling in fields as necessary)
and create the big PDF file. It will even tar everything up and put a bow on it
so that you can just submit the result directly.

## Using

Once you get the script installed (see the next section) you can simply run
the command `prepare_files LAB_NUMBER DIRECTORY` (ex:
`prepare_files 2 my_lab_2_files`) to create a zip
file containing everything you need.

If you run `prepare_files -h` some information on the flags and how to use the
tool is displayed.

The only thing you will have to make sure to do is number your files
somehow. The script will take the last number in the file name and assume
that that is the exercise number. For example, if the script sees a file named
`part1.c` it will assume that the code is the solution for the first exercise.
Likewise if it sees a file named `dbdfskjlsdfa23kjdfj21.c` (don't name your files
like this -_-) it will assume that the code is the solution for the twenty-first
exercise because 21 is the last number in that filename.

## Reporting Bugs

If you find any bugs (especially ones that might result in losing points on a
lab!) please make an issue for it in the issue tracker (which you can find by
clicking *Issues* near the top of the page, or by clicking
[here](https://github.com/brownhead/120B-prepatory-scripts/issues)).

Feel free to fix it too and send me the code by opening up a pull request, I
will be sure you receive proper attribution.

## Installing

Download a zip file of this repository by clicking
[here](https://github.com/brownhead/120B-prepatory-scripts/archive/master.zip).
Then you'll want to unzip the file, ensure that the script is executable, and
optionally put the script somewhere in your PATH.

**If you are on any of the
school computers, including bell, then the following series of commands
will work (just copy and paste into the terminal):**

```bash
cd ~

# Download the ZIP file and unpack it
wget https://github.com/brownhead/120B-prepatory-scripts/archive/master.zip
unzip master
rm -f master
mv 120B-prepatory-scripts-master 120B-prepatory-scripts
cd ~/120B-prepatory-scripts

# Make the script executable
chmod +x prepare_files

# Add this location to your path
echo 'PATH=~/120B-prepatory-scripts/:$PATH' >> ~/.bashrc
source ~/.bashrc
```

## Example

```
john@narwhal:~/demo$ ls
lab_stuff
john@narwhal:~/demo$ ls lab_stuff
part1.c  part2.c  part3.c
john@narwhal:~/demo$ prepare_files 2 lab_stuff
We need a little bit of data from you...
	Enter value for 'full_name' (leave blank for John Sullivan): 
	Enter value for 'email' (leave blank for jsull003@ucr.edu): 
	Enter value for 'cs_login' (leave blank for jsull003): 
	Enter value for 'partner_full_name' (leave blank for unknown): 
	Enter value for 'partner_email' (leave blank for unknown@ucr.edu): 
	Enter value for 'lab_section' (leave blank for 021): 
The header now looks like: 
/*	[file_name] - Apr 13, 2013
 *	Name & E-mail: John Sullivan <jsull003@ucr.edu>
 *	CS Login: jsull003
 *	Partner(s) Name & E-mail: unknown <unknown@ucr.edu>
 *	Lab Section: 021
 *	Assignment: Lab 2 Exercise [exercise_number]
 *	
 *	I acknowledge all content contained herein, excluding template or example
 *	code, is my own original work.
 */
 

(Don't worry, exercise_number and file_name will be filled in for you)
Does this look good (enter yes or no)?: yes
[/home/john/tmpezEcMJ/jsull003_lab2_part1.c (C): 1 page on 1 sheet]
[/home/john/tmpezEcMJ/jsull003_lab2_part2.c (C): 1 page on 1 sheet]
[/home/john/tmpezEcMJ/jsull003_lab2_part3.c (C): 1 page on 1 sheet]
[Total: 3 pages on 3 sheets] sent to the printer `pdf'
[3 lines wrapped]
jsull003_lab2_part1.pdf
jsull003_lab2_part1.c
jsull003_lab2_part2.c
jsull003_lab2_part3.c
john@narwhal:~/demo$ ls
jsull003_lab2.tgz  lab_stuff
john@narwhal:~/demo$ tar -xf jsull003_lab2.tgz 
john@narwhal:~/demo$ ls
jsull003_lab2_part1.c    jsull003_lab2_part2.c  jsull003_lab2.tgz
jsull003_lab2_part1.pdf  jsull003_lab2_part3.c  lab_stuff
john@narwhal:~/demo$
```

## License

This code is licensed under the unlicense, so go nuts. Also know that I'm not
responsible for any badness that arises from you using this script, though I
will try to help out if I can.
