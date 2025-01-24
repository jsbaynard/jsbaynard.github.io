```mermaid
flowchart TD
    Start([Start])
    GenerateRandom[Generate number between 1 and 10]
    PromptUser[Prompt user to guess between 1 and 10, collect input]
    EnsureNumeric{Is user input numeric?}
    EnsureWithinGuessBounds{Is user input within prompted range?}
    InvalidInput([Display invalid input error])
    TryAgainPrompt[Prompt user to try again]
    PlayAgainPrompt[Prompt user to play again]
    CheckGuess([Compare guess to generated value])
    GuessCorrect[Display correct, good job]
    GuessTooLow[Display that guess is too low]
    GuessTooHigh[Display that guess is too high]
    End([End])

    Start --> GenerateRandom --> PromptUser --> EnsureNumeric
    InvalidInput --> PromptUser

    EnsureNumeric ---|Yes| EnsureWithinGuessBounds
    EnsureNumeric ---|No| InvalidInput

    EnsureWithinGuessBounds ---|No|InvalidInput
    EnsureWithinGuessBounds ---|Yes|CheckGuess
    

    CheckGuess ---|Correct|GuessCorrect --> PlayAgainPrompt
    CheckGuess ---|Guess is lower|GuessTooLow
    CheckGuess ---|Guess is higher|GuessTooHigh

    GuessTooLow --> TryAgainPrompt
    GuessTooHigh --> TryAgainPrompt

    TryAgainPrompt ---|Yes|PromptUser
    TryAgainPrompt ---|No|End

    PlayAgainPrompt ---|Yes|GenerateRandom
    PlayAgainPrompt ---|No|End
```

#### Documentation:

GenerateRandom: Generates value between 1 and 10
PromptUser: Asks user to enter a value between 1 and 10 and collects input
EnsureNumeric: Ensures that the entered value is a valid integer. Display invalid input error if not and reprompt.
EnsureWithinGuessBounds: Check if guessed value is within 1-10, as prompted before. Display invalid input error if not and reprompt.
CheckGuess: Checks if the value is correct first. If false, check if lower, and if not lower, then check if higher. Communicate the status of their guess (too high or low) and ask user if they would like to try again. If correct, ask user if they would to play again with a new number. If so, start again at GenerateRandom. If not, terminate program.