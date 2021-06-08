# DSI_Galvanize_May_17_2021 Notes for DSI Galvanize
# Table of Contents
`Markdown All in One, Command+Shift+P, Create table of contents`- [DSI_Galvanize_May_17_2021 Notes for DSI Galvanize](#dsi_galvanize_may_17_2021-notes-for-dsi-galvanize)
- [DSI_Galvanize_May_17_2021 Notes for DSI Galvanize](#dsi_galvanize_may_17_2021-notes-for-dsi-galvanize)
- [Table of Contents](#table-of-contents)
  - [Relevant Links](#relevant-links)
- [SQL](#sql)
- [Git](#git)
  - [MacOS password requests](#macos-password-requests)
  - [Quick reference](#quick-reference)
- [Markdown](#markdown)
  - [Syntax, LaTex](#syntax-latex)
  - [Images](#images)
- [Bash Scripting](#bash-scripting)
    - [make a bash function](#make-a-bash-function)
  - [Terminal tricks](#terminal-tricks)
    - [recall line editing in terminal](#recall-line-editing-in-terminal)
- [Zoom](#zoom)
  - [!49 Participants](#)
- [Python](#python)
  - [Syntax](#syntax)
    - [Type Hints](#type-hints)
    - [Formatting](#formatting)
    - [Nested Loop with product](#nested-loop-with-product)
    - [Saving pictures](#saving-pictures)
  - [Data wrangling](#data-wrangling)
    - [Space separated numerical data](#space-separated-numerical-data)
  - [Jupyter Notebooks](#jupyter-notebooks)
    - [jup shortcut (credit: Hamid)](#jup-shortcut-credit-hamid)
    - [correct closure of notebooks](#correct-closure-of-notebooks)
  - [Comprehensions](#comprehensions)
  - [functions to remember](#functions-to-remember)
- [Pandas](#pandas)
  - [Data checks](#data-checks)
  - [Data extraction](#data-extraction)
  - [Machine Learning Workflow](#machine-learning-workflow)
    - [Cross Validation](#cross-validation)
    - [k-fold Cross Validation](#k-fold-cross-validation)
    - [Bootstrap](#bootstrap)
- [Sorting Algorithms](#sorting-algorithms)
  - [Bubble Sort](#bubble-sort)
- [`matplotlib.pyplot` visualizations](#matplotlibpyplot-visualizations)
  - [Font Sizes](#font-sizes)
- [Derivations](#derivations)

## Relevant Links
* [Visualizing `scipy.stats` distributions](https://stackoverflow.com/questions/37559470/what-do-all-the-distributions-available-in-scipy-stats-look-like)
* [MathJax basic tutorial and quick reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
example:
```
$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$
Does not render in GitHub !
```
$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$
* VirtualBoxVM on MacOS for Ubuntu installation instructions:
[Step-by-Step info for MacOS](https://siytek.com/ubuntu-mac-virtualbox/)

# SQL
* ROUND to 1000
 ```
SELECT name, population AS "POP", ROUND(gnp, -3)
FROM country
WHERE continent = 'South America' AND gnp > 0
ORDER BY population ASC;
 ```
 * CASE WHEN
```
SELECT name,
       CASE WHEN continent='Caribbean' THEN 'North America'
            ELSE continent END
FROM country
WHERE name LIKE 'J%';
```

# Git
## MacOS password requests
* Git keeps prompting me for user name and password every time
[credit](https://stackoverflow.com/questions/7773181/git-keeps-prompting-me-for-a-password)
Configuring credential.helper: On OS X (now macOS), run this in Terminal:
`git config --global credential.helper osxkeychain`
When pushing/pulling for the first time after that, reply always in keychain popup window
## Quick reference
* create new repository on githup, copy address and run in local directory git pull "GitHub URL"
* mess with data locally, then in local terminal run the following:
* git status
* git add .
* git status
* git commit -m ""Here is what was done""
* git push
* To navigate back to TOC above, `Ctrl+Up`


# Markdown
## Syntax, LaTex
* new line `<br />` [credit](https://stackoverflow.com/questions/24575680/new-lines-inside-paragraph-in-readme-md)
* Greek letters `$\tau$` $\tau$, `$\theta$` $\theta$ [credit](https://stackoverflow.com/questions/54698075/how-do-i-print-greek-letters-in-jupyter)
* Font size `\Huge, \huge, \Large, \large` [credit](https://texblog.org/2012/08/29/changing-the-font-size-in-latex/)
* `$\frac{n!}{k!(n-k)!}$` $\frac{n!}{k!(n-k)!}$ [credit](https://csrgxtu.github.io/2015/03/20/Writing-Mathematic-Fomulars-in-Markdown/)
* $\Huge \frac{n!}{k!(n-k)!}$ `\Huge`

* Ctrl+K,V open preview to the right
[Marketplace URL](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)
![Markdown Preview Enhanced Extension](images/Marketplace_Markdown_Preview_Enhanced.png)
![Markdown Preview Enhanced](images/VSCode_Enhanced_View.png)
* [Python section of this doc](#python) (Internal Links/anchors to sections)
## Images
```
![Python Environment](https://imgs.xkcd.com/comics/python_environment.png)
```
![Python Environment](https://imgs.xkcd.com/comics/python_environment.png)
![](https://imgs.xkcd.com/comics/machine_learning.png)



------------------------------
# Bash Scripting
* bash profile location on OSX: '~/.bash_profile'
* gitadder command not found - in addition to adding gitadder to '~/.bash_profile', refer '~/.zshrc', not '~/.zsh' edit, and reboot:
```bash
# May 4, 2021
# /Users/alexey_imac/.bash_profile = ~/.bash_profile
export PATH="/Users/alexey_imac:$PATH"
# https://stackoverflow.com/questions/18428374/commands-not-found-on-zsh
# Created by code ~/.zsh
# Added hoping to get gitadder function in  ~/.bash_profile to work
# instead of getting
# zsh: command not found: gitadder
source ~/.bash_profile
```
### make a bash function
triple tics ` create a code block, and bash declares language to color code
```bash
function gitadder(){
    git pull  # pull possible updates from GitHub
    git add .  # Add everything - dangerous ?
    # dt=$(date '+%d/%m/%Y %H:%M:%S');
    git commit -m "Auto Updated: $(date '+%a
    %M:%H %h %d %Y')"  # date is shell comand
    git push
}
```
* recursive delete a directory: `rm -rf <directory_name>`
## Terminal tricks
[Credit](https://lifehacker.com/ctrl-r-to-search-and-other-terminal-history-tricks-278888)
* `Tab` completion
* `history` - display command history
* `Up / Down` keys - most recent comman recall
* `^Control + R` (iMac) search as you type, when found Enter
* `!characters` - last command
* Increase retained history - .bash_profile, or .zshrc (refer `man bash` "HISTORY")
```q
HISTFILESIZE=1000000000
HISTSIZE=1000000
```
* review terminal stats [here](https://lifehacker.com/review-your-most-oft-used-unix-commands-202712)
* `Esc-backspace` delete previous word
* `Escape-d` delete forward word
* `Ctrl+U` delete backward to beginning (can be found in `man bash` "Killing and Yanking")
* well we are actually using `zsh`
### recall line editing in terminal
after up arrow or typing beginning, and Esc+p or Ctrl+R recall,
* `Ctrl+c` **Give up** on the current line, return to prompt
* `Ctrl+a` place cursor at the **start of the line**
* `Ctrl+e` place cursor at the **end of the line**
* `ESC+f` _move forward_ to the beginning of the next word (make sure to release Esc after each jump, and press again)
* `ESC+b` _move left_ back one word
* `Esc+d` **delete word** current word (cursor is at the first character of the word)
* `Ctrl+k` **delete right** all characters to the right of cursor, including current word
* `Ctrl+w` **delete left** left (cursor at the first character of the word to keep)  characters to the left of cursor
* `Esc-p` or `Ctrl+r` **history** having typed a few characters, search for similar start
* `Command+K` = `clear` **clear** screen from previous outputs in MacOS
* `.zsh_history / .bash_history` stores commands
* `.zshrc` or `.bashrc`
** Adding functionality to show your current github branch (if in a github repo)
** Colors/appearance/themes
** Spellcheck
** Package/Language specific functionality
** Different/enhanced autocomplete settings
# Zoom
[Video Freeze](https://www.youtube.com/watch?v=FozorSuK2Sc)
* Preferences->Video->Advanced->Uncheck hardware acceleration box
* Blured background - on Mac - available in 5.5.0 and up, check version: ![Obsolete Zoom Ver. 5.4.9 on Mac](images/Zoom_Version.png)
![Obsolete Zoom Ver. 5.4.9 on Mac](images/Zoom_Blur.png)
![49 Participants](images/Zoom_49_participants.png)
---------------------------------
# Python
## Syntax
### Type Hints
* typing — Support for type hints [credit](https://docs.python.org/3/library/typing.html)
`def greeting(name: str) -> str:` <br />
`    return 'Hello ' + name`
### Formatting
* formatting
```
print("Sample Mean: {0:1.3f}".format(mu_hat))
Sample Mean: -0.159
  ```
### Nested Loop with product
* for mu, sigma_sq in product([-1, 0, 1], [0.5, 1, 2]):
```
from itertools import product

for mu, sigma_sq in product([-1, 0, 1], [0.5, 1, 2]):
    print("Log-Lik of Two Parameter Normal Model With mu={0}, sigma_sq={1}: {2:3.2f}".format(
        mu, sigma_sq, log_likelihood_normal_two_parameters(mu, sigma_sq, data))
    )

Log-Lik of Two Parameter Normal Model With mu=-1, sigma_sq=0.5: -102.05
Log-Lik of Two Parameter Normal Model With mu=-1, sigma_sq=1: -82.66
Log-Lik of Two Parameter Normal Model With mu=-1, sigma_sq=2: -81.63
Log-Lik of Two Parameter Normal Model With mu=0, sigma_sq=0.5: -52.85
Log-Lik of Two Parameter Normal Model With mu=0, sigma_sq=1: -58.06
Log-Lik of Two Parameter Normal Model With mu=0, sigma_sq=2: -69.33
Log-Lik of Two Parameter Normal Model With mu=1, sigma_sq=0.5: -103.64
Log-Lik of Two Parameter Normal Model With mu=1, sigma_sq=1: -83.46
Log-Lik of Two Parameter Normal Model With mu=1, sigma_sq=2: -82.03

```
### Saving pictures
`plt.savefig('../images/hist_plot1.png')`


## Data wrangling
### Space separated numerical data
[credit](https://stackoverflow.com/questions/19555472/change-a-string-of-integers-separated-by-spaces-to-a-list-of-int)
Say you are supposed to use data that looks like print output like this:
data = [-0.24525234  0.34258838  0.66512235 -2.15445321  1.30069225  0.42041963
 -0.67904514  0.2990795  -0.20201848  0.05410431  0.26106412 -0.89171509
 -0.15872403  0.83111975 -0.11941908  0.00667906  0.10079108 -0.60899067
  0.52596165  0.08029374  0.80668211 -0.10465914 -0.44508377 -0.76350006
  0.55267201  0.53581223 -0.68529436 -0.64163356  0.4809197  -0.97424692
 -0.12309056  0.30210824 -0.50851312  0.49089701 -0.5729919   1.84253363
 -0.77796115  0.49132436 -0.50516287 -0.09554953  0.70306746  0.17312964
  1.37490091 -0.72273023 -0.68162468  0.01836007  0.71899727 -0.86227295
 -0.04175399 -0.21037323]
 Not very useful, do this:
 * Chage text to a string (add line continuation `\` at each line), replace closing `]` with `"` at the last line to create a long string
 * rename to data_s
 * split, and convert to a numerical list using list comprehension:
 data_s = "-0.24525234  0.34258838  0.66512235 -2.15445321  1.30069225  0.42041963 \
 -0.67904514  0.2990795  -0.20201848  0.05410431  0.26106412 -0.89171509 \
 -0.15872403  0.83111975 -0.11941908  0.00667906  0.10079108 -0.60899067 \
  0.52596165  0.08029374  0.80668211 -0.10465914 -0.44508377 -0.76350006 \
  0.55267201  0.53581223 -0.68529436 -0.64163356  0.4809197  -0.97424692 \
 -0.12309056  0.30210824 -0.50851312  0.49089701 -0.5729919   1.84253363 \
 -0.77796115  0.49132436 -0.50516287 -0.09554953  0.70306746  0.17312964 \
  1.37490091 -0.72273023 -0.68162468  0.01836007  0.71899727 -0.86227295 \
 -0.04175399 -0.21037323"
data = [float(i) for i in data_s.split()]
print(data)
* to get this:
* [-0.24525234, 0.34258838, 0.66512235, -2.15445321, 1.30069225, 0.42041963, -0.67904514, 0.2990795, -0.20201848, 0.05410431, 0.26106412, -0.89171509, -0.15872403, 0.83111975, -0.11941908, 0.00667906, 0.10079108, -0.60899067, 0.52596165, 0.08029374, 0.80668211, -0.10465914, -0.44508377, -0.76350006, 0.55267201, 0.53581223, -0.68529436, -0.64163356, 0.4809197, -0.97424692, -0.12309056, 0.30210824, -0.50851312, 0.49089701, -0.5729919, 1.84253363, -0.77796115, 0.49132436, -0.50516287, -0.09554953, 0.70306746, 0.17312964, 1.37490091, -0.72273023, -0.68162468, 0.01836007, 0.71899727, -0.86227295, -0.04175399, -0.21037323]
## Jupyter Notebooks
### jup shortcut (credit: Hamid)
In ~/.zshrc add:
```
# Galvanize Unix lecture aliases
# for those tired of typing jupiter notebook:
alias jup="jupyter notebook"
# to update edits: source ~/.zshrc
```
### correct closure of notebooks
1. Logout notebook, close tab
2. Logout jupyter file browser, close tab
3. in corresponding terminal where jupyter was launched from Ctrl+C, Yes to close jupyter server
4. Make sure there are no hung up jupyter severs: `jupyter notebook list`
5. If none are listed, in terminal `exit, Ctrl+q` to close terminal - clean close

## Comprehensions
```python
[num for num in range(100)]
```

## functions to remember
```python
def factorial(n):
    prod = 1
    for num in range(n+1):
        prod*= num
    return prod
```

# Pandas
* May 20, 2021 Comment was made during pandas lecture (Andrew Nicholls) - pandas load data in memory, and are therefore fast, BUT it becomes a liability for large datasets.
Q: Is there a way to estimate sie of data before loading to prevent crash?
A Credit (Everett Schroeder):
[Loading large datasets in Pandas](https://towardsdatascience.com/loading-large-datasets-in-pandas-11bdddd36f7b)

## Data checks
* Show non NaNs in a column
`df['Verified Date'].dropna().head`
* Multi_index
```
payments_this_month.loc[payments_this_month.index.get_level_values(1).isin(active_loan_ids), :]

all_payments.loc[pd.IndexSlice[:, loan_ids_from_training_set], :][cols]
```
## Data extraction
```
In [26]: df2c
Out[26]:
Return Year  Species
1976         Chinook      14482
             Chum             5
             Coho         21934
1977         Chinook       9913
             Chum             4
                          ...
2020         Coho         14245
             Steelhead       12
             Unknown          4
2021         Chinook         33
             Steelhead        1
Length: 211, dtype: int64
# ======
In [27]: df2c.reset_index()
Out[27]:
     Return Year    Species      0
0           1976    Chinook  14482
1           1976       Chum      5
2           1976       Coho  21934
3           1977    Chinook   9913
4           1977       Chum      4
..           ...        ...    ...
206         2020       Coho  14245
207         2020  Steelhead     12
208         2020    Unknown      4
209         2021    Chinook     33
210         2021  Steelhead      1

[211 rows x 3 columns]
# ==========
In [30]: df_tmp = df2c.reset_index()

In [31]: df_tmp[df_tmp['Species'] == 'Coho']
Out[31]:
     Return Year Species       0
2           1976    Coho   21934
5           1977    Coho   25826
9           1978    Coho   20836
13          1979    Coho   25235
18          1980    Coho   39638
...
202         2019    Coho   43973
206         2020    Coho   14245
```
---------------------------

## Machine Learning Workflow

### Cross Validation
```python
# train/test split

```

### k-fold Cross Validation

### Bootstrap

------------------
# Sorting Algorithms

## Bubble Sort

```python
# hand coded algorythm
```

```python
# library call
```
# `matplotlib.pyplot` visualizations
## Font Sizes
[credit](https://www.statology.org/change-font-size-matplotlib/)
* How to Change Font Sizes on a Matplotlib Plot
```
import matplotlib.pyplot as plt
plt.rc('font', size=10) #controls default text size
plt.rc('axes', titlesize=10) #fontsize of the title
plt.rc('axes', labelsize=10) #fontsize of the x and y labels
plt.rc('xtick', labelsize=10) #fontsize of the x tick labels
plt.rc('ytick', labelsize=10) #fontsize of the y tick labels
plt.rc('legend', fontsize=10) #fontsize of the legend
```
-----------------
# Derivations
* [Derivation of Perceptron with LaTEX](https://github.com/ans12256/DSI_Galvanize_May_17_2021/blob/15b601cbd579136a87e1cef08c78a4b8000583aa/notebooks/derivation_of_a_perceptron.ipynb)
