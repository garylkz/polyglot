[#]:#<<\<\!--&>/dev/null

# polyglot

Two times the script

# Milestone

<t>

| Language | c | html | js | php | py | sh |
| --- | :-: | :-: | :-: | :-: | :-: | :-: |
| html | [✓](src/html-c) | - | [✓](src/html-js) | [✓](src/html-php) | [✓](src/html-py) | [✓](src/html-sh) |
| js | X | [✓](src/js-html) | - | [✓](src/js-php) | [✓](src/js-py) | [✓](src/js-sh) |
| php | [✓](src/php-c) | X | [✓](src/php-js) | - | [✓](src/php-py) | [✓](src/php-sh) |
| py | [✓](src/py-c) | [✓](src/py-html) | [✓](src/py-js) | [✓](src/py-php) | - | [✓](src/py-sh) |
| sh | [✓](src/sh-c) | [✓](src/sh-html) | [✓](src/sh-js) | [✓](src/sh-php) | [✓](src/sh-py) | - |

</t>

# Usage

List of commands to run the file in its corresponding "mode".
 Do note that most example commands below is written in Bash.

## HTML

Open the file with browser

## Bash

```bash
chmod +x $FILE # Set executable
./$FILE
```

## C

```bash
gcc -x c $FILE # Compile
./a.out
```

## Others

```bash
node   $FILE # Javascript
php    $FILE
python $FILE
```

<!--
# List languages
LS=($(ls src))
L1=() L2=()
for i in ${LS[@]}
do
    L=${i%-*}
    if [[ ${L1[@]} != *$L* ]]
    then
        L1[${#L1[@]}]=$L
    fi
    L=${i#*-}
    if [[ ${L2[@]} != *$L* ]]
    then
        L2[${#L2[@]}]=$L
    fi
done
L2=($(echo ${L2[*]} | tr " " "\n" | sort))

# Generate table
TABLE="\n| Language |"
for L in ${L2[@]} 
do
    TABLE+=" $L |"
done
TABLE+="\n| --- |"
for L in ${L2[@]} 
do
    TABLE+=" :-: |"
done
TABLE+="\n"
for L in ${L1[@]}
do
    TABLE+="| $L |"
    for R in ${L2[@]}
    do
        F="$L-$R"
        if [[ $L == $R ]]
        then
            TABLE+=" - |"
        elif [[ ${LS[@]} == *$F* ]]
        then
            TABLE+=" [✓](src\/$F) |"
        else
            TABLE+=" X |"
        fi
    done
    TABLE+="\n"
done

# Write table
perl -0777 -i -pe "s/(<t>\n).*?(\n<\/t>)/\$1$TABLE\$2/s" README.md

if [[ $USER != "runner" ]]
then
    echo "NOT RUNNER, SKIPPING COMMIT"
    exit 0
fi

git config --global user.email gary.github@gmail.com
git config --global user.name wotgary
git add README.md
git commit -m "Update README.md (Auto)"
git push
#-->
