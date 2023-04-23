# Cat Me if You Can

## Challenge Description

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/Cat%20Me%20if%20You%20Can/images/challengedescription.png)

The description mentions `cat` and escaping, so we'll have to get around the `cat` command and use a different method to display the flag. As expected, entering `cat flag.txt` doesn't get us the flag: 

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/Cat%20Me%20if%20You%20Can/images/catdoesntwork.png)

So, we use command substitution instead as described in the [GNU command substitution documentation](https://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html). Entering `echo "$(cat flag.txt)"` doesn't work either, but `echo "$(<flag.txt)"` does and prints our flag to `stdout`!

![](https://github.com/mt3636/HackPack-CTF-2023/blob/main/Cat%20Me%20if%20You%20Can/images/flag.png)

    flag{(^._.^)_m3ow_me0w_(^._.^)}
