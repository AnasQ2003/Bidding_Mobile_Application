<div align="center">

# 🍾 Bidding Game Challenge

> An algorithmic game-theory simulation in Java where two automated bidders compete in a tactical auction to pull a bottle to their side of the board.

🎬 **Watch the Demo Video — Bidding Application:** *(https://youtu.be/jwHRJb5j3vk)*

[![Java](https://img.shields.io/badge/Java-8-ED8B00.svg?style=flat-square&logo=openjdk)](https://www.java.com/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

</div>

---

## 🌟 Overview

The **Bidding Game Challenge** is an algorithmic programming simulation where two players compete in a multi-round tactical auction. The game board is represented as an array of 11 positions with a "bottle" starting directly in the middle (position 6). 

Each player starts with a budget of **$100**. In each round, both players simultaneously place a secret bid. The player with the higher bid wins the round, causing the bottle to move one position closer to their side. If the bottle reaches position 1, Player One wins. If it reaches position 11, Player Two wins. 

This project serves as an educational coding exercise to test algorithmic strategy, game theory, and dynamic decision-making under resource constraints.

---

## 🎮 Game Rules & Logic

### 1. The Board & Movement
- **Positions**: The board consists of `11` positions (1 to 11).
- **Starting Position**: The bottle starts in the center, at position `6`.
- **Winning Condition**:
  - **Player One** wins if the bottle reaches position `1`.
  - **Player Two** wins if the bottle reaches position `11`.
- **Movement**:
  - If **Player One** wins a round, the bottle moves **left** (closer to 1).
  - If **Player Two** wins a round, the bottle moves **right** (closer to 11).

---

### 2. Money & Budgets
- **Starting Amount**: Both players start with **$100**.
- **Spending**: The winner of the round has their bid deducted from their remaining balance. The loser keeps their money.
- **Out of Money Default**: If a player spends all their money and cannot prevent the other player from winning, the opponent wins by default.

---

### 3. Ties & Illegal Moves
- **Ties**: If both players bid the same amount, a random boolean generator decides who wins the round.
- **Illegal Moves**: A bid must be **greater than 0** and **less than or equal to the player's remaining money**.
- **Default Loss**: If a player places an illegal bid (e.g. bidding $0, a negative amount, or more than their remaining budget), they **instantly lose the game by default**.

---

## 🛠️ The `Bidder` Interface

To write a bidding bot, a class must implement the `Bidder` interface:

```java
package edu.app.biddingchallenge;

import java.util.ArrayList;

public interface Bidder {
    /**
     * Calculate your bid based on the current game state.
     * 
     * @param yourMovesSoFar   - List of bids you placed so far.
     * @param theirMovesSoFar  - List of bids the opponent placed so far.
     * @param position         - Distance of the bottle from your side.
     * @param yourMoneyLeft    - Your remaining budget.
     * @param theirMoneyLeft   - Opponent's remaining budget.
     * @return Your bid for this round (Must be >= 1 and <= yourMoneyLeft).
     */
    public int calculateBid(ArrayList<Integer> yourMovesSoFar, 
                            ArrayList<Integer> theirMovesSoFar, 
                            int position, 
                            int yourMoneyLeft, 
                            int theirMoneyLeft);
    
    /**
     * @return The display name of your bidder.
     */
    public String getName();
}
```

---

## 📁 Project Structure

```
Bidding-Game-master/
│
├── src/
│   └── edu/app/biddingchallenge/
│       ├── Bidder.java              # The interface you must implement
│       ├── BidLogic.java            # The game engine & simulation loop
│       ├── ExampleBidderOne.java    # Example bot (Fixed bid strategy)
│       └── ExampleBidderTwo.java    # Example bot (Random bid strategy)
│
├── .classpath                       # Eclipse classpath configuration
├── .project                         # Eclipse project metadata
└── README.md                        # Project documentation
```

---

## 🤖 Example Strategies Included

1. **ExampleBidderOne**: Always bids a flat rate of **$10** every round.
2. **ExampleBidderTwo**: Bids a random integer between **$7 and $11** every round:
   ```java
   (int) (Math.random() * 5) + 7
   ```

---

## 🚀 How to Setup and Play

### Prerequisites
- **Java Development Kit (JDK 8 or higher)** installed on your machine.
- An IDE (Eclipse, IntelliJ IDEA, NetBeans) or command-line terminal.

### Steps to Run

**1. Clone the Repository:**
```bash
git clone https://github.com/AnasQ2003/Bidding_Application.git
cd Bidding_Application
```

**2. Open in your IDE:**
- If using **Eclipse**, import it directly as an existing project (`.project` file included).
- If using **IntelliJ**, open the directory and configure the SDK.

**3. Implement your Bot:**
- Create a new class implementing `Bidder`.
- Write your custom tactical logic in the `calculateBid` method.

**4. Register and Play:**
- In `BidLogic.java`, instantiate your custom bot inside the `main` method:
  ```java
  playerOne = new MyCustomBidder();
  playerTwo = new ExampleBidderTwo();
  ```
- Run `BidLogic.java` to simulate the game. Output will display round-by-round status with visual indicators:
  ```text
  Bidder One Balance: 100
  Bidder Two Balance: 100
  _  _  _  _  _  X  _  _  _  _  _ 

  Bidder One Balance: 90
  Bidder Two Balance: 100
  Bidder One bid: 10 *Wins round
  Bidder Two bid: 9
  _  _  _  _  X  _  _  _  _  _  _ 
  ```

---

## 📄 License

```
MIT License

Copyright (c) Bidding Mobile Application --- 2026 AnasQ2003🍾

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## 👨‍💻 Author

**Anas Ahmed Qureshi** — [@AnasQ2003](https://github.com/AnasQ2003)

---

<div align="center">

Built with ❤️ by **Anas**

Made with 🔥 and a lot of ☕

**⭐ If you found this useful, please star the repository!**

</div>

