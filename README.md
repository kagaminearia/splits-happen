# Design and Development Challenge – Bowling Score

## Installation and Usage

### Installation

Create a new directory and pull this repo to that directory. Install the required packages. 

```
mkdir -p ~/bowling_score_challenge
cd ~/bowling_score_challenge
git init
git pull https://github.com/kagaminearia/splits-happen.git
pip3 install pytest
```

### Usage

__User Inputs__

This program allows users to directly enter a string as input and generates the score from the string. The program stops when the user enters `q` as command.

```
python3 main.py
```

__Unit Testing__

A unit testing file is provided to test the functionalities of the main program.

```
pytest test.py
```


## Requirement
Create a program which, given a valid sequence of rolls for one line of American Ten-Pin Bowling, produces the total score for the game. Fork this repository, build your program in Python, then submit a pull request with your code.

## Tasks which are out of scope
*   No need to check for valid rolls.
*   No need to check for correct number of rolls and frames.
*   No need to provide scores for intermediate frames.

## Scoring Logic
*   Each game, or "line" of bowling, includes ten turns, or "frames" for the bowler.
*   In each frame, the bowler gets up to two tries to knock down all the pins.
*   If in two tries, he fails to knock them all down, his score for that frame is the total number of pins knocked down in his two tries.
*   If in two tries he knocks them all down, this is called a "spare" and his score for the frame is ten plus the number of pins knocked down on his next throw (in his next turn).
*   If on his first try in the frame he knocks down all the pins, this is called a "strike". His turn is over, and his score for the frame is ten plus the simple total of the pins knocked down in his next two rolls.
*   If he gets a spare or strike in the last (tenth) frame, the bowler gets to throw one or two more bonus balls, respectively. These bonus throws are taken as part of the same turn. If the bonus throws knock down all the pins, the process does not repeat: the bonus throws are only used to calculate the score of the final frame.
*   The game score is the total of all frame scores.

## Validation Test Cases
Use the test cases from the table below to validate the scoring logic of your program. For program input, "X" indicates a strike, "/" indicates a spare, "-" indicates a miss, and a number indicates the number of pins knocked down in the roll.

| Program Input         | Scoring Calculation                                                                                                             | Total Score |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|-------------|
| XXXXXXXXXXXX          | (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) + (10+10+10) | 300         |
| 9-9-9-9-9-9-9-9-9-9-  | 9 + 9 + 9 + 9 + 9 + 9 + 9 + 9 + 9 + 9                                                                                           | 90          |
| 5/5/5/5/5/5/5/5/5/5/5 | (10+5) + (10+5) + (10+5) + (10+5) + (10+5) + (10+5) + (10+5) + (10+5) + (10+5) + (10+5)                                         | 150         |
| X7/9-X-88/-6XXX81     | (10+7+3) + (7+3+9) + 9 + (10+0+8) + 8 + (8+2+0) + 6 + (10+10+10) + (10+10+8) + (10+8+1)                                         | 167         |
