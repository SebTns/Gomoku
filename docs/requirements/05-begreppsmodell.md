    ```mermaid
classDiagram
    direction TB

    class Game {
        +mode: vs AI | vs Player
        +status: pending | inProgress | completed
        +outcome: blackWins | whiteWins | draw | forfeit
        +boardSize: 15×15 | 19×19
    }

    class Player {
        +username: String
        +colour: black | white
        +placeStone(intersection) Move
        +forfeit()
    }

    class HumanPlayer {
        +email: String
        +statistics: Statistics
    }

    class AIOpponent {
        +difficulty: easy | medium | hard
        +calculateMove() Intersection
    }

    class Board {
        +size: Int
        +isEmpty(intersection) Boolean
    }

    class Intersection {
        +row: Int
        +col: Int
        +isEmpty: Boolean
    }

    class Stone {
        +colour: black | white
    }

    class Move {
        +moveNumber: Int
        +placedAt: DateTime
    }

    class FiveInARow {
        <<win condition>>
        +direction: horizontal | vertical | diagonal
        +stones: Stone[5]
    }

    class Statistics {
        +wins: Int
        +losses: Int
        +draws: Int
        +winRate: Float
    }

    Player <|-- HumanPlayer : is a
    Player <|-- AIOpponent  : is a

    Game "1" --> "2" Player        : has players\none Black · one White
    Game "1" --> "1" Board         : is played on
    Game "0..1" --> "1" FiveInARow : decided by

    Player "1" --> "*" Move        : makes

    Move "1" --> "1" Stone         : places
    Move "1" --> "1" Intersection  : at

    Stone "*" --> "1" Intersection : occupies

    Board "1" *-- "n×n" Intersection : consists of

    FiveInARow "1" --> "5" Stone   : formed by consecutive

    HumanPlayer "1" --> "1" Statistics : tracks

    Player "1" ..> "1" Player      : opposes as Opponent

