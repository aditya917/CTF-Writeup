CTF Writeup: Vimjail

In the LakeCTF Qualifications, the “Vimjail” challenge was an intriguing puzzle with a very interesting solution. However, before delving into the complexities of the puzzle and the solution, some base information needs to be covered.

<img src="https://github.com/aditya917/CTF-Writeup/assets/52827225/c2c03ef6-80ea-4482-a4ce-c126eedccac4" alt="drawing" width="400"/>
“Vim” is a free and open-source text editor. Vim is extremely fast and capable, mainly due to its lightweight and command-based nature. Vim has a graphical user interface, yet it can also be conveniently run through a terminal (which was the case in this CTF challenge). The text editor has a lot of different commands and programmed keyboard shortcuts, which makes developing the application a lot easier. With multiple community-made plugins for the application, Vim also has the reputation of being highly customizable with many other features.

![image](https://github.com/aditya917/CTF-Writeup/assets/52827225/4cfe5709-578a-4b70-a69c-a79c4fd56d39)

In the CTF challenge, competitors ssh on a remote server with the address “chall.polygl0ts.ch” and the username “user” on port 9018 with the password “lakectf.” Competitors are also provided with a “chall.vimrc1” file. A “.vimrc” file is a configuration file, and many things can be done on this file, like remapping keys, syntax highlighting, and many other valuable functions. In the “.vimrc1” file, all the keys were mapped to an underscore, meaning that the underscore completely overwrote any meaningful commands typed. Figuring out how to bypass this was the most challenging part of the function and the main reason this challenge was called “Vimjail.” Everything seemed impossible to solve, and I was stuck at the empty vim screen for quite some time.

![image](https://github.com/aditya917/CTF-Writeup/assets/52827225/203c5e13-9beb-4497-9f51-79cb42ece26c)

However, as I started to search and learn more about Vim, I realized it comes with many modes. I won’t go into all the different modes in this document. However, the one primary mode all the competitors were forced into was insert mode, allowing users to insert and remove text from the file. To get the flag in this competition, the main thing that needed to be done was to enter different characters as expressions. Vim allows users to insert results of expressions like “2+2” into the file. Using the shortcut <Ctrl - R> <=>, users can enter the expression evaluation interface to enter the results of expressions into the file. 

![image](https://github.com/aditya917/CTF-Writeup/assets/52827225/8c19629a-a315-43ff-a045-15d092564c5a)

With a bit more tinkering, remembering the <ctrl> keybindings, and scrolling through the PBR Discord, there was a unique keybind <Ctrl-q> + <any character> coupled with the <Ctrl - R> <=> keybind which allowed any character to appear on the screen. Using the expression evaluation interface and using the <ctrl-q> + <any character> to type into the interface allowed me to type “system(“cat flag”), which finds the flag file on the system and returns the output in accurate text. 

![image](https://github.com/aditya917/CTF-Writeup/assets/52827225/7eedd531-90fc-41d3-b6c4-d7c94562de5d)

Looking back, this “Vimjail” challenge wasn’t tough to solve, but it felt hard in the moment. It was an excellent opportunity to learn more about things I had rarely worked with before and the complicated workings of a popular application. I hope to solve similar and even more complex problems as I continue with Psi Beta Rho, but this was a great base difficulty.
