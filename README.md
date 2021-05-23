# DSI_Galvanize_May_17_2021 Notes for DSI Galvanize
## Following steps in
* [Setting up DSI notes] (https://www.youtube.com/watch?t=4722&v=W5kZjp2uh8M&feature=youtu.be)

# Table of Contents
`Markdown All in One, Ctrl+Shift+P, Create table of contents`
- [DSI_Galvanize_May_17_2021 Notes for DSI Galvanize](#dsi_galvanize_may_17_2021-notes-for-dsi-galvanize)
  - [Following steps in](#following-steps-in)
- [Table of Contents](#table-of-contents)
  - [Relevant Links](#relevant-links)
- [Git](#git)
  - [MacOS password requests](#macos-password-requests)
  - [Quick reference](#quick-reference)
- [Markdown](#markdown)
  - [Images](#images)
- [Bash Scripting](#bash-scripting)
    - [make a bash function](#make-a-bash-function)
  - [Terminal tricks](#terminal-tricks)
    - [recall line editing in terminal](#recall-line-editing-in-terminal)
- [Zoom](#zoom)
  - [!49 Participants](#)
- [Python](#python)
  - [Jupyter Notebooks](#jupyter-notebooks)
    - [jup shortcut (credit: Hamid)](#jup-shortcut-credit-hamid)
    - [correct closure of notebooks](#correct-closure-of-notebooks)
  - [Comprehensions](#comprehensions)
  - [functions to remember](#functions-to-remember)
- [Pandas](#pandas)
  - [Loading large datasets in Pandas](#loading-large-datasets-in-pandas)
  - [Machine Learning Workflow](#machine-learning-workflow)
    - [Cross Validation](#cross-validation)
    - [k-fold Cross Validation](#k-fold-cross-validation)
    - [Bootstrap](#bootstrap)
- [Sorting Algorithms](#sorting-algorithms)
  - [Bubble Sort](#bubble-sort)
- [`matplotlib.pyplot` visualizations](#matplotlibpyplot-visualizations)
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

-----------------
# Derivations
* [Derivation of Perceptron with LaTEX](https://github.com/ans12256/DSI_Galvanize_May_17_2021/blob/15b601cbd579136a87e1cef08c78a4b8000583aa/notebooks/derivation_of_a_perceptron.ipynb)
