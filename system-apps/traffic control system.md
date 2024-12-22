How to design a traffic control system?

A classical system design question from old age is still popular. Make sure you know how to transition from one state to another like RED to GREEN and from GREEN to ORANGE to RED, etc. One tip is you can use the state design pattern because there is a clear transition of the state from one to other. For example, you cannot go from RED to GREEN before ORANGE or so on.

You can also use the Enum to represent the state and implement the pattern, just as we did with the strategy design pattern.
