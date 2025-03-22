# Contributing Page 
_A modern PHP backend framework for secure and modular applications._

## 📖 Table of Contents  
1. [Go back](readme.md) 
2. [Code Style & Naming Conventions:](#code-style-naming-conventions)
3. [Class Conventions:](#-class-conventions)

## Code Style & Naming Conventions
1. **Indentation**: 4 spaces per level (no tabs).
2. **Line length**: 120 characters max.
3. **No trailing spaces**.
4. **Control structures** (if, while, for, etc.) must have a space before the opening parenthesis.
5. **Opening braces `{`** must be on the same line as the statement.



// Indentation: 4 spaces per level (no tabs).
if (condition) {
    // Control structure with a space before the opening parenthesis.
    // Opening brace { is on the same line as the statement.
    // Code goes here.
}

// Line length: 120 characters max.
$this->methodThatHasAVeryLongNameThatExceedsTheCharacterLimitShouldBeFormattedInThisWaySoThatItIsEasierToReadWithoutBreakingTheCodeTooMuch();

// No trailing spaces.
$variable = 'value'; // No trailing spaces here.

// Control structures (if, while, for, etc.) must have a space before the opening parenthesis.
for ($i = 0; $i < 10; $i++) {
    // Some code here
}

// Opening braces { must be on the same line as the statement.
while ($condition) {
    // Some code inside the loop
}


## Class Conventions
using lt as class name